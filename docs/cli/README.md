# Command-Line Interface

::: tip Note
CLI commands are available only for cPanel and DirectAdmin control panels. Plesk and ISPmanager CLI support is coming soon.
:::

For access to ImunifyAV agent features from the command-line interface, use the following command:

```
imunify-antivirus
```

 **Optional arguments:**
| | |
|-|-|
| `-h`, `--help `| show this help message and exit|
| `--console-log-level {ERROR,WARNING,INFO,DEBUG}` | level of logging input to the console|

**Basic usage:**

```
imunify-antivirus [command] [--option1] [--option2]... 
```

**Available commands:**

| | |
|-|-|
| `start`| start the agent|
| `add-sudouser`| add a user with root privileges|
| `checkdb`| check database integrity|
| `delete-sudouser`| remove a user with root privileges|
| `doctor`| collect info about the system and send it to ImunifyAV|
| `register`| register the agent|
| `rstatus`| send a query to server to the check if the license is valid|
| `unregister`| unregister the agent|
| `update`| update malware signatures|
| `update-license`| force license update|
| `version`| show version|
| `feature-management`| manage ImunifyAV features available for users|
| `malware`| malware-related operations|

## Start
 
This command allows to run the agent.

**Usage:**

```
imunify-antivirus start [--optional arguments]
```

## Add-sudouser

This command adds a user with root privileges to the server.

**Usage:**

```
imunify-antivirus add-sudouser <userID> [--optional arguments]
```

## Сheckdb

Checks database integrity. In case database is corrupt, then this command saves backup copy of the database at `/var/imunifyav` and tries to restore integrity of the original database.

:::tip Note
If this command cannot restore database integrity, then it will destroy the original broken database.
:::
 
**Usage:**

```
imunify-antivirus checkdb [--optional arguments]
```

## Delete-sudouser

This command removes a user with root privileges from the server.

**Usage:**

```
imunify-antivirus delete-sudouser <userID> [--optional arguments]
```

## Doctor

This command collects information about ImunifyAV state, generates the report and sends it to the ImunifyAV Support Team. This command can be used in case of any troubles or issues with ImunifyAV. This command will generate a key to be sent to the ImunifyAV Support Team. With that key the ImunifyAV Support Team can help with any problem as fast as possible.

**Usage:**
 
```
imunify-antivirus doctor [--optional arguments]
```

## Register

Allows to register and activate ImunifyAV. You can use it in case if ImunifyAV was not activated during installation process or in case if activation key of the ImunifyAV was changed for any reason. If you do not know what is an activation key or have any problem with it then, please, read [Installation Guide](/imunifyav/#installation-guide) or [contact our support team](https://cloudlinux.zendesk.com/hc/requests/new).

**Usage:**
 
```
imunify-antivirus register [--optional arguments] [KEY]
```

`KEY` is a positional argument:

| | |
|-|-|
|`KEY`| register with activation key (use `IPL` to register by IP)|

If you will use this command without the `KEY` argument, then it will try to register and activate current activation key.

**Example 1:**
The following command will register and activate Imunify360 with the provided activation key:

```
imunify-antivirus register IMAV250jjRRjowbjk56dGN
```

**Example 2:**
If you have an IP-based license, you can use `IPL` argument to register and activate ImunifyAV:

```
imunify-antivirus register IPL
```

## Rstatus

Allows to check if ImunifyAV server license is valid.

**Usage:**

```
imunify-antivirus rstatus [--optional arguments]
```

## Unregister


Allows to unregister and disable ImunifyAV on the server.

**Usage:**

```
imunify-antivirus unregister [--optional arguments]
```

## Update

This command allows updating ImunifyAV malware signatures.

**Usage:**

```
imunify-antivirus update [--optional arguments] signatures
```

## Update-license

This command force updating the ImunifyAV license.

**Usage:**

```
imunify-antivirus update-license [--optional arguments]
```

## Version

Allows to show the actual ImunifyAV version installed on the server.

**Usage:**

```
imunify-antivirus version [--optional arguments]
```

## Feature-management

Allows to manage ImunifyAV features available for users.

**Usage:**

```
imunify-antivirus feature-management [command] [--optional argument]...
```

`Command` can be one of the following:

| | |
|-|-|
| `defaults`| show the default value for each feature that is applied for newly created user|
| `disable`| disable a feature for some or all users|
| `enable`| enable a feature for some or all users|
| `get`| obtains the status of all available features for a `USER`|
| `list`| list all available features|

`Optional argument` for the `enable/disable` commands can be one of the following:

| | |
|-|-|
|<span class="notranslate">`[--feature cleanup]`</span>|enable/disable <span class="notranslate">Malware Cleanup</span>|
<span class="notranslate">`[--feature proactive]`</span>|enable/disable <span class="notranslate">Proactive Defense</span>|
| `[--users [USERS [USERS ...]]]`| specifies the list of users which will be affected, otherwise the default value will be changed|

The mandatory argument for the `get` command:

| | |
|-|-|
| `[--user USER]`| specifies a user name to obtain the status of features for|

**Example:**

The following command enables malware cleanup feature for the `user1`:

```
imunify-antivirus feature-management enable --feature cleanup --users user1
```

## Malware 

Allows to manage malware-related operation.

**Usage:**

```
imunify-antivirus malware [command] [--argument]...
```

`command` can be one of the following:

| | |
|-|-|
| `cleanup status`| show the status of the cleanup process|
| `hash`| file hash white/blacklist related operations|
| `history list`| lists the complete history of all malware-related incidents/actions (optional arguments available)|
| `ignore`| malware Ignore List operations|
| `malicious`| malware Malicious List operations|
| `on-demand`| on-demand Scanner operations|
| `suspicious`| malware Suspicious List operations|

The optional arguments are:

| | |
|-|-|
| `--order-by [ORDER_BY [ORDER_BY ...]]`| sorting order|
| `--limit LIMIT`| limits the output; must be a number greater than zero (by default, equals 100)|
| `--since SINCE`| start date|
| `--offset OFFSET`| offset for pagination (by default, equals 0)|
| `--user USER`| returns results for a chosen user|
| `--by-status [BY_STATUS [BY_STATUS ...]]`|return items with selected status|
| `--by-scan-id BY_SCAN_ID`|return items with selected ID|
| `--items ITEMS`|return selected items|
| `--to TO`| end date|
| `--search SEARCH`| search query|


`action` is the second positional argument for `hash` and can be one of the following:

| | |
|-|-|
| `list`|list white/black-listed file hashes (optional arguments apply)|
| `add`|add file hash(es) of the specified type|
| `remove`| remove file hash(es) of the specified type|

Positional arguments for `add/remove` are the list of SHA256 hashes calculated from the file contents

The argument that specifies which kind of hashes to add/remove:

`--type` - hash(es) type: black or white


`action` is the second positional argument for `ignore` and can be one of the following:

| | |
|-|-|
|`add`|add a file PATH to the Ignore List|
|`delete`|delete a file PATH from the Ignore List|
|`list`|shows Ignore List entries (optional arguments apply)|

`command2` is the second positional argument for the `malicious` command and can be one of the following:

| | |
|-|-|
|`cleanup`|clean up infected ITEMS for a USER|
|`cleanup-all`|clean up all files that have been detected as infected for all users|
|`restore-original`|restore the original (malicious/infected) file to its original location|
|`delete`|delete malicious/infected files|
|`list`|list malicious/infected files|
|`move-to-ignore`|move a malicious list entry to the (malware) Ignore List|
|`remove-from-list`|remove malicious/infected files from the Malicious List|


`action` is the second positional argument for `on-demand` and can be one of the following:

| | |
|-|-|
|`list`|list all on-demand scans performed|
|`start --path PATH`|starts an on-demand scan for a specified PATH|
|`status`|show the on-demand malware scanner status|
|`stop`|stop on-demand malware scanner process|

The optional arguments for `on-demand start` are:

| |
|-|
|`--ignore-mask IGNORE_MASK`|
|`--follow-symlinks`|
|`--no-follow-symlinks`|
|`--file-mask FILE_MASK`|
|`--hash-filter`|
|`--no-hash-filter`|
|`--intensity {low,moderate,high}`|

`action` is the second positional argument for `suspicious` and can be one of:

| | |
|-|-|
|`delete`|delete a Suspicious List entry|
|`list`|obtain the list of Suspicious List entries|
|`move-to-ignore`|move a Suspicious List entry to the (malware) Ignore List|

**Examples**

1. The following command adds a hash to the malware Black List:

```
imunify-antivirus malware hash add --type black ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f20015ad
```

2. The following command starts on-demand scanner for the path specified after the `start` command:

```
imunify-antivirus malware on-demand start --path /home/<username>/public_html/
```

## Hooks

Hooks-related command description is available [here](/imunifyav/#hooks-cli)

