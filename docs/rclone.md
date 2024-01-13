# Rclone

Setting up Rclone on your Raspberry Pi to sync with Dropbox for Business involves several steps. First, you'll install Rclone, configure it for Dropbox for Business, and then set up your sync tasks. Here's how to do it:

1. **Install Rclone**:
   - Open a terminal on your Raspberry Pi.
   - Run the following command to download and install Rclone:
     ```bash
     curl https://rclone.org/install.sh | sudo bash
     ```

2. **Configure Rclone for Dropbox for Business**:
   - Run `rclone config` to start the configuration process.
   - Choose `n` for a new remote.
   - Name your remote (e.g., `dropboxbusiness`).
   - Choose the number corresponding to `Dropbox`.
   - When asked for an API key, choose the default (full access) unless you have specific needs.
   - For `Use auto config?`, if you're on a headless setup, choose `N`. It'll give you a URL to paste into a browser (you can do this on any machine where you're logged into your Dropbox account).
   - Follow the instructions to authorize Rclone. This will involve logging into your Dropbox account and authorizing access.
   - When asked if you are using a Dropbox Business account, choose `Yes`.
   - Complete the configuration and exit.

3. **Test Rclone Connection**:
   - Test the connection to your Dropbox account:
     ```bash
     rclone lsd dropboxbusiness:
     ```
   - This command lists directories at the top level of your Dropbox.

4. **Create Backup Script**:
   - Write a script to sync your desired folder to Dropbox. For example:
     ```bash
     #!/bin/bash
     rclone sync /home/copple dropboxbusiness:/pi/wanaka
     ```
   - Replace `/home/copple` with the directory you want to back up and `/path/to/backup/folder` with the path in your Dropbox where you want the backup stored.

5. **Make Script Executable**:
   - Make your script executable:
     ```bash
     chmod +x /path/to/your/script.sh
     ```

6. **Schedule Regular Backups**:
   - Use `cron` to schedule your backup script. Edit your crontab file:
     ```bash
     crontab -e
     ```
   - Add a line to run your script at regular intervals. For example, to run it daily at 2 AM:
     ```
     0 2 * * * /path/to/your/script.sh
     ```

7. **Monitor Your Backups**:
   - Consider implementing logging in your script to keep track of backup status.
   - You could redirect output to a log file in your script:
     ```bash
     rclone sync /home/copple dropboxbusiness:/path/to/backup/folder >> /var/log/rclone_backup.log 2>&1
     ```

Remember, it's essential to regularly verify that your backups are running successfully and to test restores periodically to ensure your backup data is reliable.