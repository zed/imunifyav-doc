# ImunifyAV for cPanel and DirectAdmin


::: tip Note
This ImunifyAV documentation is applicable for **cPanel** and **DirectAdmin** control panels only.
:::

* You can find documentation for ImunifyAV for **Plesk** [here](https://plesk.revisium.com/)
* You can find documentation for ImunifyAV for **ISPmanager** [here](https://isp.revisium.com/)


ImunifyAV provides malware scanning features for cPanel and DirectAdmin control panels.

## Installation Guide

### Requirements

**Operating systems**

* CentOS
* RHEL
* CloudLinux OS 6 and 7

**Virtualization**

* OpenVZ - Works for Virtuozzo 7 with kernel 3.10.0-327.10.1.vz7.12.8 or later

**Hardware**

* RAM: 512 Mb
* HDD: 20 Gb available disk space

**Supported hosting panels**

* cPanel
* DirectAdmin (Ubuntu support is coming soon)

**Required browsers**

* Safari version 9.1 or later
* Chrome version 39 or later
* Firefox version 28 or later
* Edge version 17 or later
* Internet Explorer version 11 or later

### Installation Instructions

To install ImunifyAV proceed the following steps:

1. Log in with root privileges to the server where ImunifyAV should be installed.

2. Go to your home directory and run the commands:

```
wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh
bash imav-deploy.sh
```

If you already have **ImunifyAV+** license key you can use it during installation:

```
wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh
bash imav-deploy.sh --key YOUR_KEY
```
 
where `YOUR_KEY` is your license key. Replace `YOUR_KEY` with the actual key purchased at [https://www.imunify360.com/](https://www.imunify360.com/).

If you have an IP-based license for **ImunifyAV+**, run the same script with no arguments:

```
wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh
bash imav-deploy.sh --key IPL
```

To view available options for installation script run:

```
bash imav-deploy.sh -h
```
In a case of registration key is passed later, then you can register an activation key via the `imunify-antivirus` command:

```
imunify-antivirus register YOUR_KEY
```

Where `YOUR_KEY` is your activation key or IPL in case of IP-based license.

### Update Instructions

To upgrade ImunifyAV run the command:

```
yum update imunify-antivirus --enablerepo=imunify360-testing
```

## Uninstall

### How to uninstall ImunifyAV

To uninstall ImunifyAV, run the command:

```
bash imav-deploy.sh --uninstall
```

If you have already removed `imav-deploy.sh` then download it by running:

```
wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh
```

And proceed to the directory with the script.


### How to stop ImunifyAV

For CentOS6/CloudLinux6, run the following command:

<div class="notranslate">

```
service imunify-antivirus stop
```
</div>

For all other operating systems, run the following command:

<div class="notranslate">

```
systemctl stop imunify-antivirus
```
</div>

## Localization

ImunifyAV supports the following languages in addition to default (en-US):

* de-DE
* es-ES
* fr-FR
* ja-JP
* it-IT
* tr-TR
* nl-NL
* ru-RU
* pt-BR
* zh-CN

### How to perform a translation to your own language using our language file

* Contact ImunifyAV support to request the latest language file.
* The file is actually in JSON format, which values are the translation.
* We use this syntax to translate plurals and other dynamic content:
[https://messageformat.github.io/messageformat/page-guide](https://messageformat.github.io/messageformat/page-guide)

    Note, that you can use it to provide translation for each plural case in your language:
[http://www.unicode.org/cldr/charts/latest/supplemental/language_plural_rules.html](http://www.unicode.org/cldr/charts/latest/supplemental/language_plural_rules.html)

* You can use this tool to simplify the process: [https://translation-manager-86c3d.firebaseapp.com/](https://translation-manager-86c3d.firebaseapp.com/)

* Send the translated version to us and we will gladly include it in one of the nearest releases of ImunifyAV.


## Hoster Interface

Click _ImunifyAV_ in the main menu. There are following tabs in ImunifyAV hoster interface:

* [Users](/imunifyav/#users)
* [Files](/imunifyav/#files)
* [Scan](/imunifyav/#scan)
* [History](/imunifyav/#history)
* [Ignore List](/imunifyav/#ignore-list)
* [Features Management](/imunifyav/#features-management)
* [Settings](/imunifyav/#settings)
* [Upgrade](/imunifyav/#upgrade) 

### Users

Go to ImunifyAV → Users tab. Here, there is a table with a list of users on the server, except users with root privileges.

| ![ImunifyAV → Users tab](/images/avhosteruserstab_zoom70.png) |
|:--:| 
| *ImunifyAV → Users tab* |

The table has the following columns:

* **User name** — displays the user name.
* **Home directory** — the path to the user home directory starting from the root.
* **Infection status** —  the current status depending on the last action made:
  * **-** — scanning/cleaning is in progress;
  *  **Number of threats** — the number of infected files detected after scanning. Click to go to _Files_ tab where you can see all malicious files.
  *  **No malware found** — no malware was found during scanning.
* **Actions** :
  *  **Scan for malware** — click _Scan_ icon to start scanning files for a particular user.
  *  **View report** — click _View Report_ icon to go to _Files_ tab and display the results of the last scan.
  *  **Cleanup<sup>AV+</sup>** — click _Cleanup_ to start cleaning up infected files for the user.
  *  **Restore original<sup>AV+</sup>** — click _Restore original_ to restore original file after cleaning up if backup is available.
To perform a bulk action, tick required users and click the corresponding button above the table.

Cleaning up all files of all users and scanning all files is available in ImunifyAV+. To upgrade to ImunifyAV+, click **Upgrade to ImunifyAV+** , you will be redirected to [ImunifyAV+ upgrade](/imunifyav/#upgrade) page. Or click _Cleanup all_ button, you will be redirected to [ ImunifyAV+ upgrade ](/imunifyav/#upgrade) page.

The following filters are available:

**Items per page displayed** — click the number at the table bottom.

The table can be sorted by _User name_ and _Infection status_ (by the date of the last action).

| ![ImunifyAV+ → Users tab](/images/av+hosterusers_zoom70.png) |
|:--:| 
| *ImunifyAV+ → Users tab* |

### Files

Go to ImunifyAV → Files tab. Here, there is a table with a list of infected files within all domains and user accounts.

| ![ImunifyAV → Files tab](/images/avhosterfiles_zoom70.png) |
|:--:| 
| *ImunifyAV → Files tab* |

The table has the following columns:

* **Detected** — displays the exact time when a file was detected as malicious.
* **User name** — displays file owner name.
* **File** — the path where the file is located starting with root
* **Reason** — describes the signature which was detected during the scanning process. Names in this column depend on the signature vendor.
* **Status** — displays the file status:
  * **Infected** — threat was detected after scanning. If a file was not cleaned after cleanup, the info icon is displayed. Hover mouse over info icon to display the reason;
  *  **Cleaned** —  infected file is cleaned up.
  * **Content removed** — a file content was removed after cleanup.
  * **Cleanup queued<sup>AV+</sup>** — infected file is queued for cleanup.
Actions:
* **Add to Ignore List** — add file to Ignore List and remove it from the Malicious files list. Note that if a file is added to Ignore List, ImunifyAV will no longer scan this file.
* **Delete permanently** — remove the file from the server and from the list of Malicious files.
*  **View file** — click _eye_ icon in the file line and the file content will be displayed in the pop-up. Only the first 100Kb of the file content will be shown in case if a file has bigger size.
* **Restore original** — restore the initial infected file.
* **Cleanup file<sup>AV+</sup>** — click _Clean up_ to clean up all infected files within the account.

To perform a bulk action, tick required users and click the corresponding button above the table.

Cleaning up all files of all users is available in the ImunifyAV+. To upgrade to the ImunifyAV+, click **Upgrade to ImunifyAV+**, you will be redirected to [ImunifyAV+ upgrade](/imunifyav/#upgrade) page. Or click _Cleanup all_ button, you will be redirected to the [ ImunifyAV+ upgrade](/imunifyav/#upgrade) page.

The following filters are available:

* **Timeframe** — displays the results filtered by chosen period or date.
* **Status** — displays the results filtered by chosen status.
* **Items per page displayed** — click the number at the table bottom.

The table can be sorted by detection date (detected), user name, file path (file), reason, and status.

| ![ImunifyAV+ → Files tab](/images/av+hosterfiles_zoom70.png) |
|:--:| 
| *ImunifyAV+ → Files tab* |


### Scan

Malware scanner allows users to scan a specific directory or file for malware. Go to ImunifyAV → Scan tab. Then proceed the following steps:

1. Type a folder name to scan in the _Folder to scan_ field. Start typing with the slash `/`.
It is possible to use _Advanced_ settings:
* **Filename mask** allows to set file type for scanning (for example, `*.php` - all the files with extension php). Default setting is `*` which means all files without restriction.
* **Ignore mask** allows to set file type to ignore (for example, `*.html` will ignore all file with extension html).
* **Intensity** — defines the priority and resources that will be used for scanning  without decreasing efficiency.
  * **Low** — low priority and fewer resources consumption
  * **Moderate** — medium priority and resources consumption
  * **High** — the highest  priority and resources consumption
2. Click _Start_.

![](/images/avhosterscan_zoom70.png)

At the top right corner scanning progress and status are displayed:

* **Scanner is stopped** means that there is no scanning process running.
* **Scanning…%** means that the scanner is working at the moment. A percentage displays the scanning progress. You can also see the scanning status beneath the _Mask_ or _Advanced_ options.

![](/images/imunifyscanhosteruiondemandscanprogress_zoom70.png)

When scanning is completed, the results are shown in the table below with the following information:

* **Date** — scan date;
* **Path** — scanned folder path;
* **Total files** — total number of scanned files;
* **Result** — displays number of threats and the number of files detected as suspicious during scanning;
* **Action**:
  * **View report** — click _View Report_ icon to go to Files tab and display the results of the last scan.

![](/images/hosterscantable_zoom70.png)

The following filters are available:

**Timeframe** — displays the results filtered by chosen period or date.
To review and manage suspicious files go to [Files](/imunifyav/#files) tab.
The table can be sorted by Date, Path, Total files, and Result.

### History

History tab contains data of all actions for all files. Go to ImunifyAV → History tab. Here, there is a table with a list of files within all domains.

![](/images/avhosterhistory_zoom70.png)

The table has the following columns:

* **Date** — action timestamp.
* **Path to File** — path to the file starting from the root.
* **Cause** — displays the way malicious file was found:
  * **Manual** — scanning or cleaning was manually processed by a user.
  * **On-demand** — scanning or cleaning was initiated/made by a user;
  * **Real time** — scanning or cleaning was automatically processed by the system.
* **Owner** — displays a  user name of file owner.
* **Initiator** — displays the name of a user who was initiated the action. For system actions the name is System.
* **Event** — displays the action with the file:
  * **Detected as malicious** — after scanning the file was detected as infected;
  * **Cleaned** — the file is cleaned up.
  * **Failed to clean up** — there was a problem during cleanup. Hover mouse over the info icon to read more.
  * **Added to Ignore List** — the file was added to Ignore List. ImunifyAV will not scan it.
  * **Restored original** — file content was restored as not malicious.
  * **Cleanup removed content** — file contend was removed after cleanup.
  * **Deleted from Ignore List** — the file was removed from Ignore List. ImunifyAV will scan it.
  * **Deleted** — the file was deleted.
  * **Submitted for analysis** — the file was submitted to Imunify team for analysis.
  * **Failed to delete** — there was a problem during removal. Hover mouse over the info icon to read more.
  * **Failed to ignore** — there was a problem during adding to Ignore List. Hover mouse over the info icon to read more.
  * **Failed to delete from ignore** — there was a problem during removal from Ignore List. Hover mouse over the info icon to read more.

The table can be sorted by Date, Path to File, Cause, and Owner.

### Ignore List

Ignore List tab contains the list of files that are excluded from Malware Scanner scanning. Go to ImunifyAV → Ignore List tab. Here, there is a table with a list of files within all domains.

![](/images/avhosterignorelist_zoom70.png)

The table has the following columns:

* **Added** — the date when the file was added to Ignore List.
* **Path** — path to the file starting from the root.
* **Actions**:
  * **Remove from Ignore List** — click _Bin_ icon to remove the file from the Ignore List and start scanning.
  * **Add new file or directory** — click _Plus_ icon to add a new file or directory to Ignore List.
To perform a bulk action, tick required files and click the corresponding button above the table.

The following filters are available:

**Timeframe** — displays the results filtered by chosen period or date.
**Items per page displayed** — click the number at the table bottom.

The table can be sorted by Added and Path. By default, it is sorted from newest to oldest.

### Features Management<sup> AV</sup>

Features Management tab allows to enable or disable ImunifyAV features for each customer. Go to ImunifyAV → Features Management tab.

![](/images/avhosterfeaturesmanagement_zoom70.png)


To enable Malware Cleanup feature for new users by default, move the _Malware Cleanup_ slider.

The table has the following columns:

* **Name** — user name
* **Domains** — user domain name
* **Malware Cleanup** — allows to enable or disable Malware Cleanup feature for selected user by moving the slider.

To perform a bulk action, tick required users and move the _Malware Cleanup_ slider at the table header. Confirm the action on the confirmation popup.

### Settings


Go to ImunifyAV → Settings tab to set up the behaviour of ImunifyAV scanner.

| ![ImunifyAV → Settings tab](/images/avhostersettings_zoom70.png) |
|:--:| 
| *ImunifyAV → Settings tab* |

The following settings are available:

* **Enable Sentry error reporting** — send error reports to ImunifyAV error report server.

**ImunifyAV+ Settings**

| ![ImunifyAV+ → Settings tab](/images/av+hostersettings1_zoom70.png) |
|:--:| 
| *ImunifyAV+ → Settings tab* |

The following settings are available:

* **Automatically send malicious files for analysis** — send ImunifyAV team the files detected as malicious for analysis. Switched on by default.
* **Trim instead of removal** — do not remove infected file during cleanup but make the file zero-size (for malwares like web-shells);
* **Keep original files for … days** — the original infected file is available for restore within the defined period. Default is 14 days.
* **Enable Sentry error reporting** — send error reports to ImunifyAV error report server.

### Upgrade<sup> AV</sup>

To upgrade to ImunifyAV+ click _Upgrade Imunify_ button, upgrade page opens.

![](/images/avhosterupgrade_zoom70.png)

To upgrade, click _Buy Now_ button, you will be redirected to the purchase page. Or activate the product using an activation key if you already have one.

## End User Interface

The user side is hidden by default and can be enabled by executing the following command:

```
/opt/alt/python35/share/imunify360/scripts/av-userside-plugin.sh
```

To disable it back, run:

```
/opt/alt/python35/share/imunify360/scripts/av-userside-plugin.sh -r
```

Click _ImunifyAV_ in the main menu. There are following tabs in ImunifyAV end user interface:

* [Files](/imunifyav/#files-2)
* [History](/imunifyav/#history-2)
* [Ignore List](/imunifyav/#ignore-list-2)

### Files

Go to ImunifyAV → Files tab. Here, there is a table with a list of infected files.

| ![ImunifyAV Hoster UI → Files tab](/images/avuserfiles_zoom70.png) |
|:--:| 
| *ImunifyAV Hoster UI → Files tab* |

The table has the following columns:

* **Detected** — displays the exact time when a file was detected as malicious
* **File** — the path where the file is located starting with root
* **Reason** — describes the signature which was detected during the scanning process. Names in this column depend on the signature vendor
* **Status** — displays the file status:
  * **Infected** — threat was detected after scanning. If a file was not cleaned after cleanup, the info icon is displayed. Hover mouse over info icon to display the reason
  * **Cleaned** — infected file is cleaned up
  * **Content removed** — a file content was removed after cleanup
  * **Cleanup queued<sup> AV+</sup>** — infected file is queued for cleanup.
Actions:
* **Add to Ignore List** — add file to Ignore List and remove it from the Malicious files list. Note that if a file is added to Ignore List, ImunifyAV will no longer scan this file
* **View file** — click _eye_ icon in the file line and the file content will be displayed in the popup. Only the first 100Kb of the file content will be shown in case if a file has bigger size
* **Cleanup<sup> AV+</sup>** — click to cleanup the file.
* **Delete<sup> AV+</sup>** — remove the file from the server and from the list of Malicious files.
* **Restore original<sup> AV+</sup>** — click _Restore original_ to restore original file after cleaning up if backup is available.

To perform a bulk action, tick required users and click the corresponding button above the table.

The following filters are available:

* **Timeframe** — displays the results filtered by chosen period or date.
* **Status** — displays the results filtered by chosen status.
* **Items per page displayed** — click the number at the table bottom.

The table can be sorted by detection date (Detected), file path (File), Reason, and Status.

| ![ImunifyAV+ End User UI → Files tab](/images/av+userfiles_zoom70.png) |
|:--:| 
| *ImunifyAV+ End User UI → Files tab* |

### History

History tab contains data of all actions for all files. Go to ImunifyAV → History tab. Here, there is a table with a list of files.

![](/images/avhistoryuser_zoom70.png)

The table has the following columns:

* **Date** — action timestamp.
* **Path to File** — path to the file starting from the root.
* **Cause** — displays the way malicious file was found:
  * **Manual** — scanning or cleaning was manually processed by a user.
  * **On-demand** — scanning or cleaning was initiated/made by a user;
  * **Real time** — scanning or cleaning was automatically processed by the system.
* **Owner** — displays a user name of file owner.
* **Initiator** — displays the name of a user who was initiated the action. For system actions the name is System.
* **Event** — displays the action with the file:
  * **Detected as malicious** — after scanning the file was detected as infected;
  * **Cleaned** — the file is cleaned up.
  * **Failed to clean up** — there was a problem during cleanup. Hover mouse over the info icon to read more.
  * **Added to Ignore List** — the file was added to Ignore List. ImunifyAV will not scan it.
  * **Restored original** — file content was restored as not malicious.
  * **Cleanup removed content** — file contend was removed after cleanup.
  * **Deleted from Ignore List** — the file was removed from Ignore List. ImunifyAV will scan it.
  * **Deleted** — the file was deleted.
  * **Submitted for analysis** — the file was submitted to Imunify team for analysis.
  * **Failed to delete** — there was a problem during removal. Hover mouse over the info icon to read more.
  * **Failed to ignore** — there was a problem during adding to Ignore List. Hover mouse over the info icon to read more.
  * **Failed to delete from ignore** — there was a problem during removal from Ignore List. Hover mouse over the info icon to read more.

The table can be sorted by Date, Path to File, Cause, and Owner.

The table has the following columns:

### Ignore List

Ignore List tab contains the list of files that are excluded from Malware Scanner scanning. Go to ImunifyAV → Ignore List tab. Here, there is a table with a list of files.

![](/images/avignorelistuser_zoom70.png)

The table has the following columns:

* **Added** — the date when the file was added to Ignore List.
* **Path** — path to the file starting from the root.
* **Actions**:
  * **Remove from Ignore List** — click _Bin_ icon to remove the file from the Ignore List and start scanning.
  * **Add new file or directory** — click _Plus_ icon to add a new file or directory to Ignore List.
To perform a bulk action, tick required files and click the corresponding button above the table.

The following filters are available:

* **Timeframe** — displays the results filtered by chosen period or date.
* **Items per page displayed** — click the number at the table bottom.

The table can be sorted by Added and Path. By default, it is sorted from newest to oldest.

## Hooks

### Overview

Hooks are introduced starting from ImunifyAV version 4.2 Beta as a script-based interface for various application events. This is a simple and effective way to automate ImunifyAV alerts and event processing.
For example, an administrator can have ImunifyAV calling his own script when malicious files are detected or misconfigurations are detected and perform a custom processing or specific actions, for example, create a ticket.
Hooks are available only via CLI.

**Requirements**

* You can use any programming language to create a hook script
* A hook script should be executable
* For Native hooks, you should use Python 3.5 only

### How to start using hooks

Start using hooks with three simple steps:

1) Create a script to handle an event (a hook handler):
  * you can use our [scripts example](/imunifyav/#structure-and-examples-of-a-hook-script) as a template
  * [the following events are available](/imunifyav/#available-events-and-their-parameters)
2) Register your hook handler in ImunifyAV agent - use registration command:

<div class="notranslate">

```
imunify-antivirus hook add --event <event name> --path </path/to/hook_script>
```
</div>

3) Once the event added - check results and the log file (see below)

### Available events and their parameters

* **agent**
  * subtype ( started | misconfig )
    * started - the event is generated each time the Imunify agent is started/restarted
      * params[]
        * version / string / version of agent
    * misconfig - the event is generated when the agent detects agent misconfiguration / broken settings / etc.
      * params[]
        * error / string / error message where / what type of misconfiguration was detected and some details

* **malware-scanning**
  * subtype ( started | finished )
    * started - the event is generated when the malware scanning process is started (for on-demand and background scans only, yet not the ftp / waf / inotify)
      * params[]
        * scan_id / string / identifier of running scan
        * path / string / path that’s scanning
        * type / string / type of scanning (“on-demand”, “background”, “ftp”)
        * scan_params[]  / initial scanning params
          * file_mask / string / file mask to scan
          * follow_symlinks / boolean / shall scanner follow symlinks
          * ignore_mask / string / file mask to ignore
          * intensity / string / intensity type selected (“low”, “moderate”,  “high”)

<div class="notranslate">

```
{
"scan_id":"dc3c6061c572410a83be19d153809df1",
"home":"/home/a/abdhf/",
"user":"abdhf",
"type":"background",
"scan_params": {"file_mask":"*", "follow_symlinks":"true", "ignore_mask":"", "intensity":"low"}
}
```
</div>		  

*
  *
    * finished - the event is generated when the malware scanning process is finished (for on-demand and background scans only, yet not the ftp / waf / inotify)
      * params[]
	    * scan_id / string / identifier of running scan
		* path / string / path that’s scanned
		* users[] / string array/ user that’s scanned
		* started / int / unixtime when scan started
		* total_files / int / total number of files that were scanned
		* total_malicious / int / number of detected malicious files
		* errors[] / string / error message if any occurred during scanning
		* status / string / status of scan (“ok”, “has_errors”, “failed”)
		* scan_params[] / initial scanning params
		  * file_mask / string / file mask to scan
		  * follow_symlinks / boolean / shall scanner follow symlinks
		  * ignore_mask / string / file mask to ignore
		  * intensity / string / intensity type selected (“low”, “moderate”,  “high”)

<div class="notranslate">

```
{
"scan_id":"dc3c6061c572410a83be19d153809df1",
"home":"/home/a/abdhf/",
"user":"abdhf",
"started":1587365282,
"total_files":873535,
"total_malicious":345,
"errors":[],
"status":"ok",
"type":"background",
"scan_params": {"file_mask":"*", "follow_symlinks":"true", "ignore_mask":"", "intensity":"low"}
}
```
</div>

* **malware-detected**
  * subtype ( critical )
    * critical
	  * params[]
	    * scan_id / string / unique id of the scan
		* errors[] / string / error strings that happened during the last scan
		* started / int / unixtime when the scan was started
		* path / string / path that was scanned
		* users[] / string array / users that have been scanned (if any)
		* total_files / int / number of files checked within the last scanning
		* total_malicious / int / number of detected malicious files
		* tmp_filename / string / path to a temporary file with a list of detected threads. The list of threads is in the format of the following command: <span class="notranslate"> `imunify-antivirus malware malicious list --by-scan-id=... --json` </span>

<div class="notranslate">

```
{

"scan_id":"dc3c6061c572410a83be19d153809df1",
"path":"/home/a/abdhf/",
"username":["imunify"],
"started":1587365282,
"total_files":873535,
"total_malicious":345,
"errors":[],
"files":[
{
  "username":"imunify",
  "hash":"17c1dd3659578126a32701bb5eaccecc2a6d8307d8e392f5381b7273bfb8a89d",
  "size":"182",
  "cleaned_at":1553762878.6882641,
  "extra_data":{


  },
  "malicious":true,
  "id":32,
  "status":"cleanup_removed",
  "file":"/home/imunify/public_html/01102018_2.php",
  "type":"SMW-INJ-04174-bkdr",
  "scan_type":"on-demand",
  "Created":1553002672
},
{
  "username":"imunify",
  "hash":"04425f71ae6c3cd04f8a7f156aee57096dd658ce6321c92619a07e122d33bd32",
  "size":"12523",
  "cleaned_at":1553762878.6882641,
  "extra_data":{


  },
  "malicious":true,
  "id":33,
  "status":"cleanup_done",
  "file":"/home/imunify/public_html/22.js",
  "type":"SMW-INJ-04346-js.inj",
  "scan_type":"on-demand",
  "Created":1553002672
},
...

}
```
</div>

::: tip Note
All results can be saved in a temporary file before handler invocation and then remove the file after the event is being processed
:::

* **malware-cleanup**
  * subtype ( started | finished )
    * started - the event is generated when the malware cleanup process is started (for on-demand and background cleanup only, background auto-cleanup will be implemented later)
	  * params[]
	    * cleanup_id / string / unique id of the cleanup
		* started / int / unixtime when the cleanup was started
		* tmp_filename / string / path to a temporary file with a scanning report. The list is in the format of the following command: <span class="notranslate"> `imunify-antivirus malware malicious list --by-scan-id=... --json` </span> . See malware-detected hook section for details.
        * total_files / int / number of files that were sent for cleanup
	* finished - the event is generated when the malware scanning process is finished (for on-demand and background cleanup only, background auto-cleanup will be implemented later)
	  * params[]
	    * cleanup_id / string / identifier of running cleanup
		* started / int / unixtime when cleanup started
		* total_files / int / number of files that were sent for cleanup
		* total_cleaned / int / number of files that were successfully cleaned
		* tmp_filename / string / path to a temporary file with a list of results.
		* errors[] / string / error messages if any occurred during cleanup
		* errors[] / string / error messages if any occurred during cleanup
		
<div class="notranslate">

```
{
"scan_id":"dc3c6061c572410a83be19d153809df1",
"started":1587365282,
"total_files":873535,
"total_cleaned":872835,
"tmp_filename":”/var/imunify/tmp/hooks/tmp_02q648234692834698456728439587245.json”,
"errors":[],
"status":"ok"
}
```
</div>

### Hooks CLI

The following CLI command is used to manage hooks:

<div class="notranslate">

```
imunify-antivirus hook [command] --event [event_name|all] [--path </path/to/hook_script>]
```
</div>

The following commands are supported:

* <span class="notranslate"> **add** </span> - register a new event handler
* <span class="notranslate"> **delete** </span> - unregister existing event handler
* <span class="notranslate"> **list** </span> - show existing event handlers
* <span class="notranslate"> **add-native** </span> - register a new native event handler

The third parameter <span class="notranslate"> _event_name_ </span> defines a particular event that invokes a registered handler as opposed to <span class="notranslate"> **all** </span> keyword.     
The fourth parameter `/path/to/hook_script` shall contain a valid path to a handler of the event, it shall be any executable or Python Native event handlers that agent will run upon a registered event.

**Native**

Native hook is a script written on Python 3.5 and allows to quickly process events. The Python file should contain only one method that customer would implement:

<div class="notranslate">

```
def im_hook(dict_param):
	….
	pass
```
</div>

where `dict_param` would hold the same data as JSON that non-Native hook will gate. 

**Log File**

You can see all hook data in the log file. It is located at <span class="notranslate"> _/var/log/imunify360/hook.log_ </span> .
When the event comes, the data is recorded to the log file in the following format:

<div class="notranslate">

```
timestamp event : id : started [native:] name :  subtype : script_path
```
</div>

* <span class="notranslate"> **native** </span> is prepended for the Native hook implementation
* <span class="notranslate"> **id** </span> is a unique ID for each event

Once the listener is done, the data is recorded to the log file in the following format:

<div class="notranslate">

```
timestamp event : id : done [native:] script_path [OK|ERROR:code]
```
</div>

In case of an error, you can see the error code you have specified.

### Structure and examples of a hook script

Regular (non-native) hook:

<div class="notranslate">

```
#!/bin/bash

data=$(cat)

event=$(jq -r '.event' <<< ${data})
subtype=$(jq -r '.subtype' <<< ${data})

case ${event} in
    malware-scanning)
        case ${subtype} in
            started)
                # do stuff here
            ;;
            *)
                echo "Unhandled subtype: ${subtype}" 1>&2
                exit 1
        esac
        ;;
    *)
        echo "Unhandled event: ${event}/${subtype}" 1>&2
        exit 2
esac
```
</div>

Native hook:

<div class="notranslate">

```
def im_hook(dict_param):
   event = dict_param['event']
   subtype = dict_param['subtype']

   if event == 'malware-scanning':
       if subtype == 'started':
           # do stuff here
           pass
       elif subtype == 'finished':
           # do other stuff here
           pass
       else:
           raise Exception('Unhandled subtype {}'.format(subtype))
   else:
       raise Exception('Unhandled event {}'.format(event))
```
</div>

