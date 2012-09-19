Instructions
============

Example config file
-------------------
<pre>module = example
path = /usr/local/www

owner = deploy
group = apache

includes = tmp/cache/index.htmlmod
excludes = sql /tests tmp/cache/*

ssh_user = deploy

[staging]
hosts = bulldog dalmatian

[live]
hosts = poodle labrador</pre>

Explanation
-----------
The config file should be stored in /configs.  The reason I used a subdirectory is to prevent the shell from autocompleting the name of the config file ... as I would prefer people would be explicit about which module they are deploying.

* module - the name of the module.
* path - the path on the server where the module resides.
* owner (optional) - chown the module to owner before deploying
* group (optional) - chgrp the module to group before deploying
* includes (optional) - rsync --include
* excludes (optional) - rsync --exclude
* ssh_user - the user used to connect to the host

[environment] sections
* hosts - a space delimited list of hosts

Usage
-----
deploy (-t TAG | -b BRANCH) -n example

* (--tag|-t) TAG - Checkout tag TAG
* (--branch|-b) BRANCH - Checkout branch BRANCH
* (--environment|-e) ENVIRONMENT - Use environment ENVIRONMENT (e.g. live, staging)
* (--dry-run|-d|-n) - Dry-run

TODO
----
* Add a repo to the config file so if the module has not been cloned, the script can do it
* Add a way to have per-environment path
* Add a way to have per-host users
* Whether to --delete should be an option
* Should be able to pass alternative options to rsync
* have a defaults ini file