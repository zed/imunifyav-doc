# Command-Line Interface

#### Description

ImunifyAV(+) command-line interface (CLI) makes working with ImunifyAV(+) basics and features from your terminal even simpler.

::: tip Note
CLI commands are available only for cPanel and DirectAdmin control panels. Plesk and ISPmanager CLI support is coming soon.
:::

#### Usage

For access to the ImunifyAV agent features from the command-line interface, use the following command:

```
imunify-antivirus
```

Basic usage:

```
imunify-antivirus [command] [--option1] [--option2]... 
```

#### Options

The following options are available for all commands.

| | |
|-|-|
|`-h`, `--help `|show this help message and exit|
|`--console-log-level {ERROR,WARNING,INFO,DEBUG}`|level of logging input to the console|
|`--json`|returns data in JSON format|
|`--verbose, -v`|allows to return data in good-looking view if option `--json` is used|

#### Examples

1. This command allows to show help for the `start` command:
    ```
    imunify-antivirus start [-h]
    ```


**Available commands:**

| | |
|-|-|
|[`add-sudouser`](/cli/#add-sudouser)|add a user with root privileges|
|[`checkdb`](/cli/#сheckdb)|check database integrity|
|[`check-domains`](/cli/#check-domains)|send domain list check|
|[`config update`](/cli/#config-update)|update configuration file via CLI|
|[`delete-sudouser`](/cli/#delete-sudouser)|remove a user with root privileges|
|[`doctor`](/cli/#doctor)|collect info about the system and send it to ImunifyAV(+)|
|[`infected-domains`](/cli/#infected-domains)|returns infected domain list|
|[`feature-management`](/cli/#feature-management)|manage ImunifyAV(+) features available for users|
|[`hooks`](/cli/#hooks)|hooks-related operations|
|[`malware`](/cli/#malware)|malware-related operations|
|[`register`](/cli/#register)|register the agent|
|[`rstatus`](/cli/#rstatus)|send a query to server to the check if the license is valid|
|[`start`](/cli/#start)|start the agent|
|[`unregister`](/cli/#unregister)|unregister the agent|
|[`update`](/cli/#update)|update malware signatures|
|[`update-license`](/cli/#update-license)|force license update|
|[`version`](/cli/#version)|show version|


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

## Check-domains


Allows to send domains list to check on ImunifyAV central server. This command requires cPanel. After domains checked, the results is available via the `infected-domains` command.

::: tip Note
`check-domains` command may take a few minutes to complete.
:::

**Usage**:


```
imunify-antivirus check-domains [--optional arguments]
```



## Config update

Allows to update configuration file via CLI.


**Usage:**

```
imunify-antivirus config update [configuration options]
```

You can find instructions on how to apply configuration changes from CLI [here](/cli/#how-to-apply-changes-from-cli) and configuration options can be taken from the `/etc/sysconfig/imunify360/imunify360.config` file.

**Example:**

Set the `MALWARE_SCAN_INTENSITY.cpu = 5` configuration option from a command line:

```
imunify-antivirus config update ‘{"MALWARE_SCAN_INTENSITY": {"cpu": 5}}’
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

## Infected-domains

Allows to retrieve infected domains list.

**Usage**:

```
imunify-antivirus infected-domains [-h] [--optional arguments]
```

Optional arguments for `list`:

| | |
|-|-|
|`--limit`|Limits the output with the specified number of domains.<br>Must be a number greater than zero. By default, equals 100.|
|`--offset`|Offset for pagination. By default, equals 0.|

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

## Hooks

Hooks-related command description is available [here](/imunifyav/#hooks-cli)

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
|`--intensity {low,moderate,high}`|

`action` is the second positional argument for `suspicious` and can be one of:

| | |
|-|-|
|`delete`|delete a Suspicious List entry|
|`list`|obtain the list of Suspicious List entries|
|`move-to-ignore`|move a Suspicious List entry to the (malware) Ignore List|

**Example**

1. The following command starts on-demand scanner for the path specified after the `start` command:

```
imunify-antivirus malware on-demand start --path /home/<username>/public_html/
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

## Start
 
This command allows to run the agent.

**Usage:**

```
imunify-antivirus start [--optional arguments]
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


## How to apply changes from CLI

In order to apply changes via command-line interface (CLI), you can use the following command:

```
imunify-antivirus config update '{"SECTION": {"parameter": value}}'
```

For example, if you want to set `MALWARE_SCAN_INTENSITY.cpu = 5` from a command line, then you should execute the following command:

```
imunify-antivirus config update '{"MALWARE_SCAN_INTENSITY": {"cpu": 5}}'
imunify-antivirus config update '{"MALWARE_SCANNING": {"rapid_scan": true}}'
```

It is also possible to apply several parameters at once.

For example:

```
imunify-antivirus config update '{"MALWARE_SCAN_INTENSITY": {"cpu": 5, "io": 7}}'
```


<Disqus/>