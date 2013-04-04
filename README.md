stash - Shell I/O clipboard
===========================

Dummy Bash script that makes it easy to manage chunks of data coming from
standard input. A stash is nothing but a container of raw data tagged with a
name (i.e. a regular file), this script just makes file management painless.

Install
-------

Just copy `stash` in one of the directories listed in `$PATH`, for example:

    cp stash /usr/local/bin/stash

Stashes name
------------

A stash name must contain only alphanumeric characters, dashes (but not in the
first position) and underscores, when omitted it defaults to `default`.

Stashes location
----------------

If the environment variable `STASH_DIRECTORY` is not empty then stashes are
created underneath, otherwise in `~/.stash/`.

This can be used, for example, to share stashes across multiple machines with
Dropbox, just add to `~/.bashrc`:

    export STASH_DIRECTORY=~/Dropbox

Sample usage
------------

Display the synopsis:

    stash -h

Write the output of a command to the default stash:

    ps ux | stash

Dump the content of the default stash:

    stash

Write the output of a command to a custom stash and to standard output:

    ls | stash files | wc -l

Append the output of a command to a custom stash:

    uptime | stash -a log

List all the available stashes:

    stash -l

Drop a list of stashes by name (including the default one):

    stash -d files log default

Cleanup everything by removing every stash:

    stash -c
