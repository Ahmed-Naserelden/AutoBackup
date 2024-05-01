# Backup Script

This repository contains a script, `backup.sh`, designed to back up files from a specified directory to another specified directory.

## Usage

To use the `backup.sh` script, follow these steps:

1. Ensure you have Bash installed on your system. This script is written in Bash and requires a Bash-compatible shell to run.

2. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/Ahmed-Naserelden/AutoBackup.git
    ```

3. Navigate to the directory where you cloned the repository:

    ```bash
    cd AutoBackup
    ```

4. Make the script executable:

    ```bash
    chmod +x backup.sh
    ```

5. Run the script by providing two arguments: the target directory name and the destination directory name. For example:

    ```bash
    ./backup.sh /path/to/source_directory /path/to/destination_directory
    ```

   Replace `/path/to/source_directory` with the path to the directory containing the files you want to back up, and `/path/to/destination_directory` with the path to the directory where you want to store the backups.

6. The script will automatically create a compressed tar archive (`tar.gz`) containing the files from the source directory that were modified within the last 24 hours. It will then move the backup archive to the destination directory.

## Scheduling Automatic Backups with cron

To schedule the `backup.sh` script to run automatically at regular intervals, you can use cron. Here's how you can set up a cron job:

1. Open your terminal and type the following command to edit your cron jobs:

    ```bash
    crontab -e
    ```

2. Add the following line to the crontab file to schedule the script to run daily at midnight:

    ```cron
    0 0 * * * /path/to/backup.sh /path/to/source_directory /path/to/destination_directory
    ```

   Replace `/path/to/backup.sh` with the actual path to the `backup.sh` script, `/path/to/source_directory` with the path to the source directory, and `/path/to/destination_directory` with the path to the destination directory.

3. Save and exit the crontab file. The cron job will now run the `backup.sh` script daily at midnight, automatically backing up your files.

## Notes

- Ensure that you provide valid directory paths as arguments when running the script.
- This script assumes that the provided directories exist and are accessible.
- Make sure you have sufficient permissions to read from the source directory and write to the destination directory.
- The script creates a backup archive with a timestamp indicating when the backup was created.
- It is recommended to schedule the script to run automatically using cron to ensure regular backups.
