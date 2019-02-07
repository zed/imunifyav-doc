# Command-Line Interface


**_Note that CLI commands are available only for cPanel and DirectAdmin control panels. Plesk and ISPmanager CLI support is coming soon._**

For access to ImunifyAV agent features from the command-line interface, use the following command:

```
imunify-antivirus
```
```
 
```
**Optional arguments:**

| | |
|-|-|
| | show this help message and exit|
| ` ` `--console-log-level` ` ` `{ERROR,WARNING,INFO,DEBUG}` | level of logging input to the console|

**Basic usage:**

```
imunify-antivirus [command] [--option1] [--option2]... 
```
```
    
```
**Available commands:**

| | |
|-|-|
| | start the agent|
| | add a user with root privileges|
| | check database integrity|
| | remove a user with root privileges|
| | disable hosting panel plugin|
| | collect info about the system and send it to ImunifyAV|
| | enable hosting panel plugin (if detected)|
| | register the agent|
| | send a query to server to the check if the license is valid|
| | unregister the agent|
| | update malware signatures|
| | force license update|
| | show version|
| | manage ImunifyAV features available for users|
| | malware-related operations|

## Start


 

 
## Usage:


 
```
imunify-antivirus start [--optional arguments]
```
```
 
```
## Add-sudouser


 

 
## Usage:


 
```
imunify-antivirus add-sudouser <userID> [--optional arguments]
```
```
 
```
## Сheckdb


 
## /var/imunifyav


## Note that if this command cannot restore database integrity, then it will destroy the original broken database.


 
## Usage:


 
```
imunify-antivirus checkdb [--optional arguments]
```
```
 
```
## Delete-sudouser


 

 
## Usage:


 
```
imunify-antivirus delete-sudouser <userID> [--optional arguments]
```
```
 
```
## Disable-plugin


 

 
## Usage:


 
```
imunify-antivirus disable-plugin <panel> [--optional arguments]
```
```
 
```
## Doctor


 

 
## Usage:


 
```
imunify-antivirus doctor [--optional arguments]
```
```
 
```
## Enable-plugin


 

 
## Usage:


 
```
imunify-antivirus enable-plugin <panel> [--optional arguments]
```
```
 
```
## Register


 

 
## Usage:


 
```
imunify-antivirus register [--optional arguments] [KEY]
```

`KEY` is a positional argument:

| | |
|-|-|
|KEY | register with activation key (use `IPL` to register by IP)|

If you will use this command without the `KEY` argument, then it will try to register and activate current activation key.

**Example 1:**
The following command will register and activate Imunify360 with the provided activation key:

```
imunify-antivirus register IMAV250jjRRjowbjk56dGN
```
```
 
```
**Example 2:**
If you have an IP-based license, you can use IPL argument to register and activate ImunifyAV:

```
imunify-antivirus register IPL
```
```
 
```
## Rstatus



Allows to check if ImunifyAV server license is valid.

**Usage:**

```
imunify-antivirus rstatus [--optional arguments]
```
```
 
```
## Unregister



Allows to unregister and disable ImunifyAV on the server.

**Usage:**

```
imunify-antivirus unregister [--optional arguments]
```
```
 
```
## Update



This command allows updating ImunifyAV malware signatures.

**Usage:**

```
imunify-antivirus update [--optional arguments] signatures
```
```
 
```
## Update-license



This command force updating the ImunifyAV license.

**Usage:**

```
imunify-antivirus update-license [--optional arguments]
```
```
 
```
## Version



Allows to show the actual ImunifyAV version installed on the server.

**Usage:**

```
imunify-antivirus version [--optional arguments]
```
```
 
```
## Feature-management



Allows to manage ImunifyAV features available for users.

**Usage:**

```
imunify-antivirus feature-management [command] [--optional argument]...
```

```
Command
```
```
 
```
| | |
|-|-|
| | show the default value for each feature that is applied for newly created user|
| | disable a feature for some or all users|
| | enable a feature for some or all users|
| | obtains the status of all available features for a `USER`|
| | list all available features|

```
Optional argumentenable/disable
```
```
 
```
| | |
|-|-|
| | specifies which feature to enable/disable|
| | specifies the list of users which will be affected, otherwise the default value will be changed|
```
 
```

The mandatory argument for the `get` command:


| | |
|-|-|
| | specifies a user name to obtain the status of features for|


**Example** :

The following command enables malware cleanup feature for the `user1` :

```
imunify-antivirus feature-management enable --feature cleanup --users user1
```


## Malware 



Allows to manage malware-related operation.

**Usage:**

```
imunify-antivirus malware [command] [--argument]...
```

```
Command
```

| | |
|-|-|
| | show the status of the cleanup process|
| | allows to manage hashes|
| | lists the complete history of all malware-related incidents/actions (optional arguments available)|
| | allows to add, delete or show files which will not be scanned|
| | allows to manage malicious files|
| | allows to manage on-demand scanner|
| | allows to read malware files|
| | allows to manage suspicious files|


The optional arguments are:

| | |
|-|-|
| | sorting order|
| | limits the output; must be a number greater than zero (by default, equals 100)|
| | start date|
| | offset for pagination (by default, equals 0)|
| | returns results for a chosen user|
| | end date|
| | search query|

```
actionhash
```

| | |
|-|-|
| | list added hashes|
| | add file hashes of the specified type|
| | remove file hashes of the specified type|

Positional argument for `add/remove` is the list of SHA256 hashes calculated from the file contents

The argument that specifies which kind of hashes to add/remove:

```
--type -- hash(es) type: black or white
```
```
 
```
```
commandignore
```

| | |
|-|-|
| | add a file or files divided by space to the Ignore List|
| | delete an ignored file or files divided by space from the list|
| | show a list of ignored files|

```
commandmalicious
```

| | |
|-|-|
| | delete malicious file or files divided by space|
| | show a list of malicious files|
| | move a file or files divided by space to the Ignore List|
| | allows to add malicious files to quarantine|
| | restore source files from backup|
| | restore files from quarantine|

```
commandon-demand
```

| | |
|-|-|
| | start on-demand scanner for the path specified after the start command|
| | returns a list of all on-demand scanner session results|
| | show current status for on-demand scanner|
| | stop current scanning|

```
commandsuspicious
```

| | |
|-|-|
| | delete suspicious file or files divided by space|
| | show a list of suspicious files|
| | move suspicious files divided by space to the Ignore List|
| | move suspicious files divided by space to the quarantine|

**Examples**

1. The following command adds a hash to the malware Black List:

```
imunify-antivirus malware hash add --type black ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f20015ad
```

2. The following command starts on-demand scanner for the path specified after the `start` command:

```
imunify-antivirus malware on-demand start --path /home/<username>/public_html/
```



