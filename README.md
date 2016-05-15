crontab-script
==============

A simple script to install or remove custom crontab entries.

Here's how it works:

1. Create a file `./crontab.sh.crontab` with the custom crontab of your project

2. Run `./crontab.sh` to add the crontab entry, or to check if it exists

3. Run `./crontab.sh --remove` to remove the crontab entry

The script detects if the crontab entry was already added.
It works by adding the entry in this format:

    # BLANK LINE HERE
    # $PWD
    YOUR CRONTAB
    # BLANK LINE HERE

`$PWD` is the absolute path of the directory of the `crontab.sh` script.
The blank lines at the start and end, and the line with the path
should uniquely identify the entry in the complete crontab of the user.
This makes it possible to avoid adding an entry twice,
and to remove the entry.

This is just for your information. The script creates this format, not you.
You just create your crontab entry in `crontab.sh.crontab`,
and the script will install it in the above format.

To use this script in a project:

- Copy `crontab.sh` to your project, add to version control

- Create `crontab.sh.crontab` as appropriate for the project,
  but don't add to version control

- Copy `crontab.sh.crontab` to `crontab.sh.crontab.sample`,
  remove sensitive or non-portable information, add to version control

- Mark `crontab.sh.crontab` and `crontab.sh.crontab.bak` ignored in version control,
  as the crontab entries typically contain sensitive information
  or settings specific to the local environment.
  If your case is simpler, then you don't need the sample,
  you can use this script directly, of course.

When installing your project in production,
copy `crontab.sh.crontab.sample` to `crontab.sh.crontab`,
and run `./crontab.sh` to install the crontab,
`./crontab.sh --remove` to remove it.
