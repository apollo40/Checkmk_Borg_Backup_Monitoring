# Checkmk_Borg_Backup_Monitoring

This is a quick local Plugin for Checkmk to Monitor your Borg Backups.

When you Backup just add a 

echo $(date +%s) > /var/log/borg_last_success

to your Script if it runs sucessfull.

For Example:

borg create -p -C lz4 YOUR_BACKUP_USER@YOUR_BACKUP_SERVER:/backup/::$(date -I) /PATH_TO_BACKUP
if [ $? -eq 0 ]; then
echo $(date +%s) > /var/log/borg_last_success
fi

Copy the check_backup Script to /usr/lib/check_mk_agent/local/borg

Checkmk will find this local Plugin automatically.