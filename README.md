These backup scripts are intended to facilitate the backups of Wordpress sites running in docker or podman containers.   Upon running the backup script, a self-executing backup archive is created that can be run on another host to perform a semi-automated restore of the site in just seconds (depending on the size of the site's data).

**backup**

* This is the backup script. Add this to a folder named backup, inside the container's folder, and add it to cron. For example, if your container is in /opt/docker/test, then you would do the following:

    `mkdir /opt/docker/test/backup`
  
    `cp backup restore /opt/docker/test/backup/`

    `crontab -l > crontab`

    `echo "00 00 * * * /opt/docker/test/backup/backup" >> crontab`

    `crontab crontab`

**restore**

* Used as part of the backup script to create a self-executable restore archive. This is the logic that does the self-extraction AND handles the restore itself.  You do not run this, it's only used by the backup script to create the archive.
