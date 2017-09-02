crontab-installer
=================

A simple script to install or remove a custom crontab.

Here's how it works:

1. Create a file `./crontab.sh.crontab` with the custom crontab of your project

2. Run `./crontab.sh` to add the crontab entry if it does not already exist

3. Run `./crontab.sh --remove` to remove the crontab entry

The script detects if the crontab already exists,
by looking for a specific format:

    # BLANK LINE HERE
    # $PWD
    YOUR CRONTAB
    # BLANK LINE HERE

`$PWD` is the absolute path of the directory of the `crontab.sh` script.
The blank lines at the start and end, and the line with the path
should uniquely identify the entry in the complete crontab of the user.
This makes it possible to avoid adding an entry twice,
and to remove the entry.

The script creates this format for you, you don't need to write it manually.
You just create your crontab entry in `crontab.sh.crontab`,
and the script will install it in the above format.

To use this script in a project:

- Copy `crontab.sh` to your project, add to version control

- Create `crontab.sh.crontab` as appropriate for the project,
  but don't add to version control

- Optionally add `crontab.sh.crontab.sample` to version control,
  without sensitive or deployment-specific information.

- Mark `crontab.sh.crontab` and `crontab.sh.crontab.bak` ignored in version control,
  as the crontab entries typically contain sensitive information
  or settings specific to deployment.

When installing your project in production,
copy `crontab.sh.crontab.sample` to `crontab.sh.crontab` and modify as needed.
Install the crontab by running `./crontab.sh`,
uninstall by running `./crontab.sh --remove`.
