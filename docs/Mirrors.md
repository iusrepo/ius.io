# Mirrors

## Summary

This article outlines a basic way of syncing with IUS. That said, you aren’t
required to use these scripts or processes if you wish to write your own.  Here
are the basic guidelines for syncing.

* Upstream Official Repository is `rsync://dl.iuscommunity.org/ius`
* The file named CURRENT in the root of the repo is generated at the end of
every push. Therefore, you can automate syncing whenever this file changes
from what you have locally.
* Syncs should be done as near to the time that CURRENT changes as possible.

## Submitting a Request to IUS Core Development

Before you can access the upstream rsync service, you must submit a request to
have all downstream hosts added to our firewall. Send an email to
[coredev@iuscommunity.org][1] with the following information.

```text
contact name:
contact email:
public or private mirror:
IPv4 addresses to allow:
IPv6 addresses to allow:
content path (i.e. /pub/ius):
public protocols supported (http, https, ftp, rsync):
```

## Configuring Rsync

The IUS Upstream Repository can be mirrored via rsync. The following is
a preferred method as it allows mirrors to remain in sync hourly, but only
pulling updates if there has been changes.  Copy the following script
somewhere, and make it executable:

/root/scripts/sync-ius.sh:

```bash
# check to make sure we arent' already running
RES=$(ps -ef | grep "[/bin/bash] /root/scripts/sync-ius.sh" | wc -l)
if [ $RES -gt 2 ]; then
    echo "IUS sync already running...."
    exit
fi

UPSTREAM_URI='rsync://dl.iuscommunity.org/ius'
LOCAL_DIR='/var/www/pub/ius'
TMP=$(mktemp -d)
SYNC_CMD="rsync -aH --exclude-from=/etc/rsync/exclude.ius.txt --numeric-ids --delete --delete-after --delay-updates ${UPSTREAM_URI}/* ${LOCAL_DIR}"

mkdir -p ${LOCAL_DIR}

# check with current file, if it diffs then we sync
CURRENT=$(rsync ${UPSTREAM_URI}/CURRENT ${TMP}/CURRENT && cat ${TMP}/CURRENT)
MY_CURRENT=$(cat ${LOCAL_DIR}/CURRENT 2>/dev/null || echo "")

if [ "x${CURRENT}" != "x${MY_CURRENT}" ]; then
    echo "Local IUS repository is out of sync with CURRENT"
    if [ "x$1" = "x--randomize" ]; then
        let SEC=$(($RANDOM%3000+1))
        echo "Sleeping ${SEC} seconds to randomize sync time..."
        sleep $SEC
    fi
    ${SYNC_CMD}
else
    echo "Local IUS repository is in sync with CURRENT"
fi
```

## The Initial Sync

It is a good idea to run the initial sync manually so that the hourly cronjob
doesn’t try to run while we are syncing (though the script protects against
it). Plus, it allows you to detect any issues that might come up:

```bash
# /root/scripts/sync-ius.sh
```

## Setting Up Cron

To ensure not all downstream mirrors attempt to sync at the same time we
randomize a sleep interval in the script, so be sure to add the ‘–randomize’
flag to sync-ius.sh in your cron.

/etc/cron.d/sync-ius:

```bash
1 * * * * root /root/scripts/sync-ius.sh --randomize >/dev/null 2>&1
```

## Custom IUS Red Hat Satellite/Spacewalk channel

We have heard some people using a custom IUS channel within Red Hat Satellite
or Spacewalk instead of using a repository. The IUS team are not experts in
these applications recommend using [⁠Red Hat Satelltie][2] or [Spacewalk][3]
documentation.

[1]: mailto:coredev@iuscommunity.org
[2]: https://access.redhat.com/documentation/en-US/Red_Hat_Satellite/
[3]: https://fedorahosted.org/spacewalk/wiki/UserDocs
