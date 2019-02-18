# Crontab

List (`-l`), edit (`-e`) and remove (`-r`) crontab entries

    crontab -l
    crontab -e
    crontab -r

Edit crontab for a different user

    sudo -u <user> crontab -e

Example crontab entry (run php script every 30 minutes)

    30 * * * * cd /path/to/script; php -q script.php > /dev/null

Timing format

- min (0-59) / hour (0-23) / day of month (1-31) / month (1-12) / day of week (0-6, 0=Sunday)
- Use asterisk in a specific slot to represent every instance (eg. every hour, day etc)

Crontab Command Tips

- Separate multiple statements for one cron instruction with `;`
- Suppress error/output by redirecting result to `> /dev/null`
