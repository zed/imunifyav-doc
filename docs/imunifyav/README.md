# ImunifyAV for cPanel and DirectAdmin


**_Please note that this ImunifyAV documentation is for cPanel and DirectAdmin control panels only._**

**_You can find documentation for ImunifyAV for Plesk _**
**_You can find documentation for ImunifyAV for ISPmanager _**

ImunifyAV provides malware scanning features for cPanel and DirectAdmin control panels.

[Hoster Interface](/hoster_interface/)

[End User Interface](/end_user_interface/)

## Installation Guide


### Requirements



**Operating systems**

CentOS
RHEL
CloudLinux OS 6 and 7

**Virtualization**

OpenVZ - Works for Virtuozzo 7 with kernel 3.10.0-327.10.1.vz7.12.8 or later

**Hardware**

RAM: 512 Mb
HDD: 20 Gb available disk space

**Supported hosting panels**

cPanel
DirectAdmin (Ubuntu support is coming soon)

**Required browsers**

Safari version 9.1 or later
Chrome version 39 or later
Firefox version 28 or later
Edge version 17 or later
Internet Explorer version 11 or later

### Installation Instructions



To install ImunifyAV proceed the following steps:

1.Log in with root privileges to the server where ImunifyAV should be installed.

2.Go to your home directory and run the commands:

`wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh`  `bash imav-deploy.sh`
```
 
```
If you already have ImunifyAV+ license key you can use it during installation:

`wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh`  `bash imav-deploy.sh --key YOUR_KEY`
```
 
```
where YOUR_KEY is your license key. Replace YOUR_KEY with the actual key purchased at [https://www.imunify360.com/](https://www.imunify360.com/) .

If you have an IP-based license (for ImunifyAV+), run the same script with no arguments:

`wget `  `bash imav-deploy.sh --key IPL`

To view available options for installation script run:

`bash imav-deploy.sh -h`

In a case of registration key is passed later, then you can register an activation key via the `imunify-antivirus` command:

`imunify-antivirus register YOUR_KEY`
```
 
```
Where YOUR_KEY is your activation key or IPL in case of IP-based license.

### Update Instructions



To upgrade ImunifyAV run the command:

`yum update imunify-antivirus --enablerepo=imunify360-testing`
```
 
```


## Uninstall


To uninstall ImunifyAV, run the command:

`bash` ` ` `imav-deploy.sh` ` ` `--uninstall`

If you have already removed `imav-deploy.sh` then download it by running

`wget` ` ` `https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh`
```
 
```
And proceed to the directory with the script.


## Localization


ImunifyAV supports the following languages in addition to default (en-US):

de-DE
es-ES
fr-FR
ja-JP
it-IT
tr-TR
nl-NL
ru-RU
pt-BR
zh-CN

### How to perform a translation to your own language using our lang file



Contact ImunifyAV support to request the latest lang file.
The file is actually in JSON format, which values are the translation.
We use this syntax to translate plurals and other dynamic content:
[https://messageformat.github.io/messageformat/page-guide](https://messageformat.github.io/messageformat/page-guide)
Note, that you can use it to provide translation for each plural case in your language:
[http://www.unicode.org/cldr/charts/latest/supplemental/language_plural_rules.html](http://www.unicode.org/cldr/charts/latest/supplemental/language_plural_rules.html)

You can use this tool to simplify the process: [https://translation-manager-86c3d.firebaseapp.com/](https://translation-manager-86c3d.firebaseapp.com/)

Send the translated version to us and we will gladly include it in one of the nearest releases of ImunifyAV.


## Hoster Interface


Click _ImunifyAV_ in the main menu. There are following tabs in ImunifyAV hoster interface:

[Users](/users/)
[Files](/files/)
[Scan](/on-demand_scan/)
[History](/history/)
[Ignore List](/ignore_list/)
[Features Management](/features_management/)
[Settings](/dashboard/#settings)
[Upgrade](/upgrade/) 


### Users


Go to ImunifyAV → Users tab. Here, there is a table with a list of users on the server, except users with root privileges.

![](/images/avhosteruserstab_zoom70.png)

The table has the following columns:

**User name** — displays the user name.
**Home directory** — the path to the user home directory starting from the root.
**Infection status** —  the current status depending on the last action made:
`o` **-** — scanning is in progress;
`o` **Number of threats** — the number of infected files detected after scanning. Click to go to _Files_ tab where you can see all malicious files.
`o` **No malware found** — no malware was found during scanning.
**Actions** :
`o` **Scan for malware** — click _Scan_ icon to start scanning files for a particular user.
`o` **View report** — click _View Report_ icon to go to _Files_ tab and display the results of the last scan.
To perform a bulk action, tick required users and click the corresponding button above the table.

To cleanup all files of all users, please upgrade to **None** . To do so, click **Upgrade to ImunifyAV+** , you will be redirected to [ImunifyAV+ upgrade ](/upgrade/) page. Or click _ Cleanup all_ button, you will be redirected to [ ImunifyAV+ upgrade ](/upgrade/) page.

The following filters are available:

**Items per page displayed** — click the number at the table bottom.

The table can be sorted by _User name_ and _Infection status_ (by the date of the last action).

### Files


Go to ImunifyAV → Files tab. Here, there is a table with a list of infected files within all domains and user accounts.

![](/images/avhosterfiles_zoom70.png)

The table has the following columns:

**Detected** — displays the exact time when a file was detected as malicious.
**User name** — displays file owner name.
**File** — the path where the file is located starting with root
**Reason** — describes the signature which was detected during the scanning process. Names in this column depend on the signature vendor.
**Status** — displays the file status:
`o` **Infected** — threat was detected after scanning. If a file was not cleaned after cleanup, the info icon is displayed. Hover mouse over info icon to display the reason;
`o` **Cleaned** —  infected file is cleaned up.
`o` **Content removed** — a file content was removed after cleanup.
Actions:
`o` **Add to Ignore List** — add file to Ignore List and remove it from the Malicious files list. Note that if a file is added to Ignore List, ImunifyAV will no longer scan this file.
`o` **Delete permanently** — remove the file from the server and from the list of Malicious files.
`o` **View file** — click _eye_ icon in the file line and the file content will be displayed in the pop-up. Only the first 100Kb of the file content will be shown in case if a file has bigger size.
`o` **Restore original** — restore the initial infected file.

To perform a bulk action, tick required users and click the corresponding button above the table.

To cleanup all files of all users, please upgrade to **None** . To do so, click **Upgrade to ImunifyAV+** , you will be redirected to [ImunifyAV+ upgrade ](/upgrade/) page. Or click _ Cleanup all_ button, you will be redirected to [ ImunifyAV+ upgrade ](/upgrade/) page.

The following filters are available:

**Timeframe** — displays the results filtered by chosen period or date.
**Status** — displays the results filtered by chosen status.
**Items per page displayed** — click the number at the table bottom.

The table can be sorted by detection date (detected), user name, file path (file), reason, and status.

### Scan


Malware scanner allows users to scan a specific directory or file for malware. Go to ImunifyAV → Scan tab. Then proceed the following steps:

1. Type a folder name to scan in the _Folder to scan_ field. Start typing with the slash “/”.
It is possible to use _Advanced_ settings:
**Filename mask** allows to set file type for scanning (for example, “*.php” - all the files with extension php). Default setting is “*” which means all files without restriction.
**Ignore mask** allows to set file type to ignore (for example, “*.html” will ignore all file with extension html).
**Intensity** — defines the priority and resources that will be used for scanning  without decreasing efficiency.
`o` **Low** — low priority and fewer resources consumption
`o` **Moderate** — medium priority and resources consumption
`o` **High** — the highest  priority and resources consumption
2. Click _Start_ .

![](/images/avhosterscan_zoom70.png)

At the top right corner scanning progress and status are displayed:

**Scanner is stopped** means that there is no scanning process running.
**Scanning…%** means that the scanner is working at the moment. A percentage displays the scanning progress. You can also see the scanning status beneath the _Mask_ or _Advanced_ options.

![](/images/imunifyscanhosteruiondemandscanprogress_zoom70.png)

When scanning is completed, the results are shown in the table below with the following information:

**Date** — scan date;
**Path** — scanned folder path;
**Total files** — total number of scanned files;
**Result** — displays number of threats and the number of files detected as suspicious during scanning;
**Action** :
`o` **View report ** — click _View Report_ icon to go to Files tab and display the results of the last scan.
![](/images/hosterscantable_zoom70.png)

The following filters are available:

**Timeframe** — displays the results filtered by chosen period or date.
To review and manage suspicious and quarantined files go to [Files](/files/) tab.
The table can be sorted by Date, Path, Total files, and Result.

### History


History tab contains data of all actions for all files. Go to ImunifyAV → History tab. Here, there is a table with a list of files within all domains.

![](/images/avhosterhistory_zoom70.png)

The table has the following columns:

**Date** — action timestamp.
**Path to File** — path to the file starting from the root.
**Cause** — displays the way malicious file was found:
`o` **Manual ** — scanning or cleaning was manually processed by a user.
`o` **On-demand** — scanning or cleaning was initiated/made by a user;
`o` **Real time** — scanning or cleaning was automatically processed by the system.
**Owner** — displays a  user name of file owner.
**Initiator** — displays the name of a user who was initiated the action. For system actions the name is System.
**Event** — displays the action with the file:
`o` **Detected as malicious** — after scanning the file was detected as infected;
`o` **Cleaned** — the file is cleaned up.
`o` **Failed to clean up** — there was a problem during cleanup. Hover mouse over the info icon to read more.
`o` **Added to Ignore List** — the file was added to Ignore List. ImunifyAV will not scan it but the file is not quarantined.
`o` **Restored original** — file content was restored as not malicious.
`o` **Cleanup removed content** — file contend was removed after cleanup.
`o` **Deleted from Ignore List** — the file was removed from Ignore List. ImunifyAV will scan it.
`o` **Deleted** — the file was deleted.
`o` **Submitted for analysis** — the file was submitted to Imunify360 team for analysis.
`o` **Failed to delete** — there was a problem during removal. Hover mouse over the info icon to read more.
`o` **Failed to ignore** — there was a problem during adding to Ignore List. Hover mouse over the info icon to read more.
`o` **Failed to delete from ignore** — there was a problem during removal from Ignore List. Hover mouse over the info icon to read more.

The table can be sorted by Date, Path to File, Cause, and Owner.

### Ignore List


Ignore List tab contains the list of files that are excluded from Malware Scanner scanning. Go to ImunifyAV → Ignore List tab. Here, there is a table with a list of files within all  domains.

![](/images/avhosterignorelist_zoom70.png)

The table has the following columns:

**Added** — the date when the file was added to Ignore List.
**Path** — path to the file starting from the root.
**Actions** :
`o` **Remove from Ignore List** — click _Bin_ icon to remove the file from the Ignore List and start scanning.
`o` **Add new file or directory** — click _Plus_ icon to add a new file or directory to Ignore List.
To perform a bulk action, tick required files and click the corresponding button above the table.

The following filters are available:

**Timeframe** — displays the results filtered by chosen period or date.
**Items per page displayed** — click the number at the table bottom.

The table can be sorted by Added and Path. By default, it is sorted from newest to oldest.


### Features Management


Features Management tab allows to enable or disable ImunifyAV features for each customer. Go to ImunifyAV → Features Management tab.

![](/images/avhosterfeaturesmanagement_zoom70.png)


To enable Malware Cleanup feature for new users by default, move the _Malware Cleanup_ slider.

The table has the following columns:

**Name** — user name
**Domains** — user domain name
**Malware Cleanup** — allows to enable or disable Malware Cleanup feature for selected user by moving the slider.

To perform a bulk action, tick required users and move the _Malware Cleanup_ slider at the table header. Confirm the action on the confirmation popup.


### Settings


Go to ImunifyAV → Settings tab to set up the behaviour of ImunifyAV scanner.

![](/images/avhostersettings_zoom70.png)

The following settings are available:

**Enable Sentry error reporting** — send error reports to ImunifyAV error report server.
**Show ClamAV scanning results** – shoiw ClamAV scanning results on _Users/Files_ tab.

### Upgrade


To upgrade to ImunifyAV+ click _Upgrade Imunify_ button, upgrade page opens.

![](/images/avhosterupgrade_zoom70.png)
To upgrade, click _ Buy Now_ button, you will be redirected to the purchase page. Or activate the product using an activation key if you already have one.

## End User Interface


Click _ImunifyAV_ in the main menu. There are following tabs in ImunifyAV end user interface:

[Files](/files2/)
[History](/history3/)
[Ignore List](/ignore_list2/)

### Files


The user side is hidden by default and can be enabled by executing
`/opt/alt/python35/share/imunify360/scripts/av-userside-plugin.sh`

To disable it back, use
`/opt/alt/python35/share/imunify360/scripts/av-userside-plugin.sh -r`


Go to ImunifyAV → Files tab. Here, there is a table with a list of infected files.

![](/images/avuserfiles_zoom70.png)

The table has the following columns:

**Detected** — displays the exact time when a file was detected as malicious
**File** — the path where the file is located starting with root
**Reason** — describes the signature which was detected during the scanning process. Names in this column depend on the signature vendor
**Status** — displays the file status:
`o` **Infected** — threat was detected after scanning. If a file was not cleaned after cleanup, the info icon is displayed. Hover mouse over info icon to display the reason
`o` **Cleaned** —  infected file is cleaned up
`o` **Content removed** — a file content was removed after cleanup
Actions:
`o` **Add to Ignore List** — add file to Ignore List and remove it from the Malicious files list. Note that if a file is added to Ignore List, ImunifyAV will no longer scan this file
`o` **View file** — click _eye_ icon in the file line and the file content will be displayed in the popup. Only the first 100Kb of the file content will be shown in case if a file has bigger size

To perform a bulk action, tick required users and click the corresponding button above the table.

The following filters are available:

**Timeframe** — displays the results filtered by chosen period or date.
**Status** — displays the results filtered by chosen status.
**Items per page displayed** — click the number at the table bottom.

The table can be sorted by detection date (Detected), file path (File), Reason, and Status.

### History


History tab contains data of all actions for all files. Go to ImunifyAV → History tab. Here, there is a table with a list of files.

![](/images/avhistoryuser_zoom70.png)

The table has the following columns:

**Date** — action timestamp.
**Path to File** — path to the file starting from the root.
**Cause** — displays the way malicious file was found:
`o` **Manual ** — scanning or cleaning was manually processed by a user.
`o` **On-demand** — scanning or cleaning was initiated/made by a user;
`o` **Real time** — scanning or cleaning was automatically processed by the system.
**Owner** — displays a user name of file owner.
**Initiator** — displays the name of a user who was initiated the action. For system actions the name is System.
**Event** — displays the action with the file:
`o` **Detected as malicious** — after scanning the file was detected as infected;
`o` **Cleaned** — the file is cleaned up.
`o` **Failed to clean up** — there was a problem during cleanup. Hover mouse over the info icon to read more.
`o` **Added to Ignore List** — the file was added to Ignore List. ImunifyAV will not scan it but the file is not quarantined.
`o` **Restored original** — file content was restored as not malicious.
`o` **Cleanup removed content** — file contend was removed after cleanup.
`o` **Deleted from Ignore List** — the file was removed from Ignore List. ImunifyAV will scan it.
`o` **Deleted** — the file was deleted.
`o` **Submitted for analysis** — the file was submitted to Imunify360 team for analysis.
`o` **Failed to delete** — there was a problem during removal. Hover mouse over the info icon to read more.
`o` **Failed to ignore** — there was a problem during adding to Ignore List. Hover mouse over the info icon to read more.
`o` **Failed to delete from ignore** — there was a problem during removal from Ignore List. Hover mouse over the info icon to read more.

The table can be sorted by Date, Path to File, Cause, and Owner.

### Ignore List


Ignore List tab contains the list of files that are excluded from Malware Scanner scanning. Go to ImunifyAV → Ignore List tab. Here, there is a table with a list of files.

![](/images/avignorelistuser_zoom70.png)

The table has the following columns:

**Added** — the date when the file was added to Ignore List.
**Path** — path to the file starting from the root.
**Actions** :
`o` **Remove from Ignore List** — click _Bin_ icon to remove the file from the Ignore List and start scanning.
`o` **Add new file or directory** — click _Plus_ icon to add a new file or directory to Ignore List.
To perform a bulk action, tick required files and click the corresponding button above the table.

The following filters are available:

**Timeframe** — displays the results filtered by chosen period or date.
**Items per page displayed** — click the number at the table bottom.

The table can be sorted by Added and Path. By default, it is sorted from newest to oldest.


