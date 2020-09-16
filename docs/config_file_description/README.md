# Config File Description


ImunifyAV(+) config file is available on the following location after installation:

_/etc/sysconfig/imunify360/imunify360.config_

In the config file it is possible to set up ImunifyAV(+) configuration. The following options are available:

<table>
<tr>
<th colspan="2" align="left"><span class="notranslate">MALWARE_SCANNING:</span></th></tr>
<tr><td><span class="notranslate">default_action: notify</span></td>
<td># default action on malicious file detected.<br>
Available options:
<ul>
<li><span class="notranslate">notify</span> – do not delete and send email notification</li>
<li><span class="notranslate">delete</span> – delete malicious file</li>
<li><span class="notranslate">cleanup</span> – cleanup malicious file</li></ul></td></tr>
<tr><td><span class="notranslate">max_signature_size_to_scan: 1048576</span></td>
<td># max file size to scan in the standard mode; value is set in bytes</td></tr>
<tr><td><span class="notranslate">max_cloudscan_size_to_scan: 10485760</span></td>
<td># max file size to scan in the cloud-assisted (by hashes) mode; value is set in bytes</td></tr>
<tr><td><span class="notranslate">max_mrs_upload_file: 10485760</span></td>
<td># max file size to upload to CloudLinux malware research service; value is set in bytes</td></tr>
<tr><td><span class="notranslate">detect_elf: False</span></td>
<td># enable (<span class="notranslate">True</span>) or disable (<span class="notranslate">False</span>) (default value) binary (ELF) malware detection</td></tr>
<tr><td><span class="notranslate">optimize_realtime_scan: True</span></td>
<td># enable (<span class="notranslate">True</span>) (default value) or disable (<span class="notranslate">False</span>) the  <a href="https://docs.cloudlinux.com/cloudlinux_os_kernel/#file-change-api" target="_blank">File Change API</a> support to reduce the system load while watching for file changes in comparison with inotify watch</td></tr>
<tr><td><span class="notranslate">sends_file_for_analysis: True</span></td>
<td># send (<span class="notranslate">True</span>) (default value) or not (<span class="notranslate">False</span>) malicious and suspicious files to the Imunify team for analysis</td></tr>
<tr><td><span class="notranslate">cloud_assisted_scan: True</span></td>
<td># speed up scans by check file hashes using cloud database</td></tr>
<tr><td><span class="notranslate">rapid_scan: True</span></td>
<td># speeds up (<span class="notranslate">True</span>) (default value) ot not (<span class="notranslate">False</span>) repeated scans based on smart re-scan approach, local result caching and cloud-assisted scan.</td></tr>
<th colspan="2" align="left"><span class="notranslate">ERROR_REPORTING:</span></th></tr>
<tr><td><span class="notranslate">enable: True</span></td>
<td># automatically report errors to the Imunify team</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">MALWARE_SCAN_INTENSITY:</span></th></tr>
<tr><td><span class="notranslate">cpu: 2</span></td>
<td># intensity level for CPU consumption. Can be set from 1 to 7, default is 2</td></tr>
<tr><td><span class="notranslate">io: 2</span></td>
<td># intensity level for file operations. Can be set from 1 to 7, default is 2</td></tr>
<tr><td><span class="notranslate">ram: 2048</span></td>
<td># intensity level for RAM consumption. Minimum value is 1024, default is 2048</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">MALWARE_SCAN_SCHEDULE:</span></th></tr>
<tr><td><span class="notranslate">day_of_month: 1</span></td>
<td># when the background scan shall start, day of the month. Can be from 1 to 31, the default value is 1 (the next day after installation).</td></tr>
<tr><td><span class="notranslate">day_of_week: 0</span></td>
<td># when the background scan shall start, day of the week. Can be from 0 to 7 (0 for Sunday, 1 for Monday..., 7 for Sunday (again)), the default value is 0</td></tr>
<tr><td><span class="notranslate">hour: 3</span></td>
<td># when the background scan shall start, hour. Can be from 0 to 23, the default value is 3</td></tr>
<tr><td><span class="notranslate">interval: MONTH</span></td>
<td># interval of scan. Supported values: strings <span class="notranslate">`NONE`</span> (no scan), <span class="notranslate">`DAY`</span>, <span class="notranslate">`WEEK`</span>, <span class="notranslate">`MONTH`</span>, the default value is <span class="notranslate">`MONTH`</span></td></tr>
<tr><th colspan="2" align="left"><span class="notranslate">MALWARE_CLEANUP:</span></th></tr>
<tr><td><span class="notranslate">trim_file_instead_of_removal: True</span></td>
<td># do not remove infected file during cleanup but make the file zero-size (for malwares like web-shells) (<span class="notranslate">True</span>) (default value)</td></tr>
<tr><td><span class="notranslate">keep_original_files_days: 14</span></td>
<td># the original infected file is available for restore within the defined period. The default is 14 days. The minimum value is one day.</td></tr>
<tr><th colspan="2" align="left"><span class="notranslate">ADMIN_CONTACTS:</span></th></tr>
<tr><td><span class="notranslate">emails: youremail@email.com</span></td>
<td># your email to receive reports about critical issues, security alerts or system misconfigurations detected on your servers.</td></tr>
<tr><th colspan="2" align="left"><span class="notranslate">PERMISSIONS:</span></th></tr>
<tr><td><span class="notranslate">support_form: True</span></td>
<td># show (<span class="notranslate">True</span>) (the default value) or hide (<span class="notranslate">False</span>) the Support icon in the ImunifyAV(+) UI.</td></tr>
<tr><td><span class="notranslate">user_ignore_list: True</span></td>
<td># show (<span class="notranslate">True</span>) (the default value) or hide (<span class="notranslate">False</span>) the Ignore List tab for end-users in the ImunifyAV(+) UI.</td></tr>
<tr><td><span class="notranslate">allow_malware_scan: False</span></td>
<td># enable (<span class="notranslate">True</span>) or disable (<span class="notranslate">False</span>) (the default value) “scan” action in the UI of the end-user.</td></tr>
<tr>
<td width="250px;"><span class="notranslate">upgrade_button: True</span></td><td># enable (<span class="notranslate">True</span> - the default value) or disable (<span class="notranslate">False</span>) the Imunify upgrade button.</td></tr>
<tr>
<th colspan="2" align="left"><span class="notranslate">RESOURCE_MANAGEMENT:</span></th></tr>
<tr><td><span class="notranslate">ram_limit: 500</span></td>
<td># set RAM consumption limit for ImunifyAV(+) in MB</td></tr>
<tr><td><span class="notranslate">io_limit: 2</span></td>
<td># set IO consumption limit for ImunifyAV(+) in MB</td></tr>
<tr><td><span class="notranslate">cpu_limit: 2</span></td>
<td># set CPU consumption limit for ImunifyAV(+) in MB.</td></tr>
</table>

### How to apply changes from CLI

In order to apply changes via command-line interface (CLI), you can use the following command:

<div class="notranslate">

```
imunify-antivirus config update ‘{"SECTION": {"parameter": value}}’ 
```
</div>

For example, if you want to set <span class="notranslate">`MALWARE_SCAN_INTENSITY.cpu = 5`</span> from a command line, then you should execute the following command:

<div class="notranslate">

```
imunify-antivirus config update ‘{"MALWARE_SCAN_INTENSITY": {"cpu": 5}}’
```
</div>

