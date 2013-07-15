postcpbackup
============

http://smyl.es/cpanel-multiple-daily-weekly-monthly-backup-rotation-with-ionice-and-nice/

cPanel by default only creates a single backup file.  If you happen to need the backup on the day the daily, weekly, and monthly are all in sync you are SOL.  This script creates an automatic backup rotation using postcpbackup so you will never have this problem again.

I am aware that cPanel has recently addressed this problem in newer releases to now allow multiple copies of backups.  The difference is that you can NOT backup incrementally (only what has changed) and you must create full backups if you use the new cPanel backup.  Using this script will allow you to still use incremental backups through the legacy backup system and create multiple backups.  Once I have time to do some testing I will test to see the IO and load compared between the two.

## Installation
Download postcpbackup to /scripts/postcpbackup on the cPanel server.

```shell
cd /scripts
wget https://raw.github.com/tripflex/postcpbackup/master/postcpbackup
```

## Configuration
Edit the postcpbackup file and modify these values or set them up in a separate configuration file.  If values are not set copies will not be created.

```shell
nano /scripts/postcpbackup
```

Edit these settings:

```shell
keepmonthly=2
keepweekly=3
keepdaily=7
```

## Set Permissions

```shell
chmod 755 /scripts/postcpbackup
```

## Testing
You can test the script and see what it will do by running this cmd

```shell
test=echo /scripts/postcpbackup
```

## Configure In WHM
Open up WHM interface, navigate to "Configure Backups", at the bottom it will say "Execute Pre/Post Backup Script", check the "postcpbackup" checkbox.

Voila!
