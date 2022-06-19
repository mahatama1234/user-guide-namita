# Table of content
1. [Kopia - Fast and Secure Open-Source Backup](#Kopia-Fast-and-Secure-Open-Source-Backup)
	* [Command Line Interface (CLI)](#Command-Line-Interface-(CLI))
	* [Graphical User Interface (GUI)](#Graphical-User-Interface-(GUI))
	* [Repository](#Repository)
	* [About Snapshot](#About-Snapshot)
2. [How to take Backups with Kopia](#How-to-take-Backups-with-Kopia)
	* [Installation Of Kopia](#Installation-Of-Kopia)
	* [Setting up Repository](#Setting-up-Repository)
		* [Creation of Repository](#Creation-of-Repository)
		* [Creation of directory path](#Creation-of-directory-path)
	* [Creating Snapshots](#Creating-Snapshots)
	* [Restoration of backups](#Restoration-of-backups)
	* [Delete a Backup](#Delete-a-Backup)
3. [Mounting](#Mounting)
4. [Licence](#Licence)
5. [Privacy policy](#Privacy-policy)
6. [Kopia Support Forum](#Kopia-Support-Forum)
7. [Disclaimer](#Disclaimer)


# Kopia - Fast and Secure Open-Source Backup

Kopia is a reliable application for creating backups of your data at any location of your choice. Restoration of the backups is an easy process with Kopia. It manages the versioning of the stored files.

Kopia is a software development model based on open collaboration. It is backed by GitHub open-source community. It has two very different models:

## Command Line Interface (CLI)

This is a standalone binary where Kopia is used in a terminal window or with a script. This option is usually preferred for advanced users and system administrators.

## Graphical User Interface (GUI)

This is a desktop application, KopiaUI. It offers a graphical user interface. This desktop application is recommended for novice users.

## Repository

It is remote storage where directories and files are stored or saved. It also maintains a set of occasional historical snapshot records based on defined policies. It’s typically remote storage, such as Filesystem, Google 
Cloud Storage, Amazon S3 (or compatible such as Minio.io, Wasabi, B2), Azure, SFTP, http/s, WebDAV or similar.
 NOTE: Any locally-mounted storage (using SMB, NFS or similar) can be used.

## About Snapshot
* Each snapshot is incremental.
* It stores multiple copies of the same file (De-duplication).
* It recognises the same content even in the renamed file (need not upload again).
* Any number of users or computers can share the same repository.
[NOTE: Currently there is no access control mechanism within the repository]
*Everybody with access to the repository can see everyone’s data.
* All data is encrypted before leaving your machine. Kopia uses state-of-the-art encryption algorithms, such as AES-256 or ChaCha20

To know more about features, click on the link https://kopia.io/docs/features/

# How to take Backups with Kopia

## Installation Of Kopia 

Please find the documentaion link for the installation https://kopia.io/docs/installation/

## Setting up Repository

### Creation of Repository
* This is the place where your backups will be saved at.
* Open Kopia application >> Filesystem >> Directory path
* Open Kopia application -->This is the starting window
 
![Kopia Landing Page](/images/kopia-landing-screen.png)

* Select the preferred storage type
[Note: Here we choose Filesystem as a storage type]
* A storage configuration window will open
[It is asking for a path to a directory where to store repository files]

![Kopia Storage Configuration](/images/kopia-storage-configuration.png)

To know more about Kopia Repositories, click on the link https://kopia.io/docs/repositories/

### Creation of directory path
* Go to your preferred location in your Filesystem
* Create a folder with the name of your choice
[The directory path has been created successfully]
* Copy the URL of the newly created folder
* Paste the URL at the directory path on the storage configuration page in KopiaUI.
* Click on the Next button.

![Kopia Storage Configuration Path](/images/kopia-storage-configuration-path.png)

* It will take you to a new Connect To Repository window.
* Create a repository password to connect.
[NOTE: Your password is important! If you lose it, you won't be able to access data stored in the repository]

![Kopia Connect Repository](/images/kopia-connect-to-repository.png)

* In the Connect to Repository window, click Show Advanced Options
* In the Show Advanced Options drop-down menu, select mode, username and hostname.
[Note: use this option, if there are multiple users]
 
![Kopia Connect Repository Options](/images/kopia-connect-to-repository-options.png)

* Click Connect to Repository button.
[NOTE: Once connected, you will be redirected to the Snapshots screen]

![Kopia New Snapshot](/images/kopia-snapshot-landing-page.png)
 
* Options available on the snapshot screen
	* Choose the type of snapshot you need
[Note- Two types of Snapshots are available- Local snapshot & ALL Snapshot]
	* New Snapshot option, to Create a new snapshot for backup.
	* Command line option
[Note- Users can track the Kopia command from here. 
See the example below]

![Kopia command Line](/images/kopia-command-line.png)

Now we're ready to back up some data. The contents of a directory at a specific point in time is called a "snapshot" in Kopia.

## Creating Snapshots
* Click on the New Snapshot tab.
* New Snapshot window gets open.

![Kopia New Snapshot](/images/kopia-new-snapshot-screen.png)

  [Note: Policy for snapshot can be set here]

Policies can be used to define:

* Snapshot retention - how long to keep snapshots before expiring them
* set of files to snapshot - excluded files can be defined similarly to. gitignore
* scheduling - how frequently/when should snapshots be created.

Policies can be applied to:

* username@hostname:/path
* username@hostname
* @hostname
* Global

![Kopia Policy](/images/kopia-policy.png)

* Type the **path** or choose from the **browse** folder option.
[**NOTE**: This path is the location (folder or file) which needs backup via Kopia]

![Kopia Directory Path backup](/images/kopia-directory-path-backup.png)


* Once you selected the path (folder or file) -->Click on Snapshot Now Option
 
![Kopia snapshot now](/images/kopia-snapshot-now.png)

* Snapshot has created

![Kopia snapshot created](/images/kopia-snapshot-created.png)
 
* Once Snapshot is successful --> check the Kopia Repository folder
[NOTE: You will see multiple folders containing encrypted files storing the backup of your data]

 ![Kopia snapshot completed](/images/kopia-snapshot-completed.png)

* You can also browse through the snapshot --> to check what all folder/files have been backup


## Restoration of backups
 
 ![Restore backup](/images/kopia-backup-restoration.png)

* To restore a Kopia backup/snapshot, First, we need to create a directory folder.
	
	[**NOTE**: This directory will be used as a destination for the restoration purpose]
 
 ![Restore backup](/images/kopia-repository-restored.png)

Options available in the restoration screen in Kopia
1. Destination --> location where the restoration occurs.
2. Skip previously restored files and the symlinks --> By default checked-->this will skip restoring previously restored files
3. Restore File Ownership --> By default checked
4. Restore File Permission --> By default checked
5. Restore File modification Time --> By default checked
6. Disable ZIP compression is checked --> By default checked
7. Overwrite Files --> If checked, this will overwrite previously restored files
8. Overwrite Directories --> If checked, this will overwrite previously restored directories
9. Overwrite Symbolic links --> If checked, this will overwrite previously restored Symbolic links
10. Write Files automatically --> If checked, this will write files automatically.

* Go to Snapshots --> [enter destination path] --> Begin Restore
* To check restoration status/progress --> Go to Tasks --> Select the time to check the restoration process.

![Tasks](/images/kopia-tasks.png)

![Restore backup status](/images/kopia-backup-status.png)
 
 

## Delete a Backup
* **Snapshot** --> **select snapshot** which needs to delete --> click on **delete selected**.

 ![Delete backup](/images/kopia-delete-snapshot.png)

* A pop-up will appear to confirm the delete action.

* On click of **Delete button** --> snapshot will be deleted.

![Delete button](/images/kopia-delete-snapshot-popup.png)
 

# Mounting
Mounting allows you to map content in the Kopia repository into a directory in the local filesystem and examine it using regular file commands or browser. This is currently the recommended way of restoring files from snapshots.

Mounting can be done repository-wise or content-wise.

To know more about Mounting click on the link https://kopia.io/docs/mounting/

# Licence
Kopia is licensed under the Apache License, Version 2.0. See https://github.com/kopia/kopia/blob/master/LICENSE for the full license text.

# Privacy policy 
https://kopia.io/docs/privacy-policy/

# Kopia Support Forum 
https://kopia.discourse.group/c/support/5?page=4

# Disclaimer
Kopia is a personal project and is not affiliated with, supported or endorsed by Google.