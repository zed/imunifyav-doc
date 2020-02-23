# Stand-alone version of ImunifyAV+

::: tip Note
Prior to version 4.3, ImunifyAV supported cPanel and DirectAdmin panels only. Starting from v4.3, ImunifyAV could be run on any CloudLinux OS, CentoOS 6/7 and RHEL 6/7 systems that have a required set of prerequisites. It doesn’t require any hosting panel installed, and can be run with any panel, as the UI is implemented using the Single Page Application paradigm.
::: 

Below you can find the steps to install and run ImunifyAV, in stand-alone mode, or within any hosting panel.

There are some basic steps to run ImunifyAV as a stand-alone application:

1. Define a way to serve web-based UI
2. Provide ImunifyAV with an actual list of users in the system
3. Configure a user authentication process

:::warning Warning
Imunify Web-UI PHP code has to be executed under a user which has access to `/var/run/defence360agent/non_root_simple_rpc.sock`. If it runs in CageFS, you'll need to configure it accordingly.
:::

#### How to configure ImunifyAV UI

:::warning Note
Imunify UI requires the `proc_open` PHP function to be enabled. If you are unable to log in, you might see a related message in the `errror.log` of the web-server.
If so, please remove it from the `disable_functions` list in `php.ini`.
:::

Create the file `/etc/sysconfig/imunify360/integration.conf` with the `ui_path` option defining the path that will serve web-based UI.

For example:

```
[paths]
ui_path = /var/www/vhosts/imav/imav.example-hosting.com/html/imav
```

ImunifyAV will automatically copy UI files there during installation/upgrade.

:::tip Note
Ensure that the domain you are going to use for the ImunifyAV web-based UI refers to this path, and that there are no other scripts or files under `ui_path`, as they might be overridden by the ImunifyAV installation.
:::

:::danger Warning
Version 4.4 and earlier require an additional upper case paths/ui_path entry in `/etc/sysconfig/imunify360/integration.conf`, like:

[PATHS]  
UI_PATH = /var/www/vhosts/imav/imav.example-hosting.com/html/imav
:::

#### How to provide ImunifyAV with an actual list of users (optional)

By default, ImunifyAV will use Linux system users, limited by `uid_min` and `uid_max` from `/etc/login.defs`.

If you want to see a specific list of users (note, that all of them must be real linux users accessible via PAM), you can specify the `user_list_script` option in `/etc/sysconfig/imunify360/integration.conf`:

```
[paths]
ui_path = …
user_list_script = /path/to/get-users-script.sh
```

It should point to an executable file that generates a json file with the following schema (domains are optional):

```
{"version": 1, "users": [{"name": "user1", "domains": ["user1.com"]}, {"name": "user2"},..]}
```

:::tip Note
Any type of executable file is acceptable. For example, you can use a Python or PHP script.
:::

#### How to configure authentication for ImunifyAV (optional) 

ImunifyAV can use PAM to authenticate users.

Once the UI is opened, the user sees a sign-in form. The credentials are checked via PAM.

You can specify which PAM service ImunifyAV should use with the `service_name` option:

```
[pam]
service_name = system-auth
```

If it is not specified, the “`system-auth`” service is used.

By default, “`root`” is considered to be the only “admin” user.

To add more administrators, list them in the `/etc/sysconfig/imunify360/auth.admin` file.

#### How to install ImunifyAV

Now everything is ready to install ImunifyAV.

The installation instructions are the same as for cPanel/DirectAdmin version, and can be found in the technical documentation: [https://docs.imunifyav.com/imunifyav/#installation-instructions](/imunifyav/#installation-instructions).

#### How to open ImunifyAV UI

Once ImunifyAV is installed, the web-based UI is available via the domain configured in `ui_path`.

For example:

if `/var/www/vhosts/imav/imav.example-hosting.com/html/imav` is the document root folder for imav.example-hosting.com domain, then you could open ImunifyAV with the following URL:

* `https://imav.example-hosting.com/` (when you have TLS certificate configured for the domain)
or 
* `http://imav.example-hosting.com/`










