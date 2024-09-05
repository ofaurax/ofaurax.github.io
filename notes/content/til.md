+++
title = 'TIL: Today I Learned'
date = 2024-09-05T12:05:00+02:00
+++

# TIL: Today I Learned

Inspired by https://github.com/jbranchaud/til


## AWS S3 without authentication

When using `aws s3`, it will complain if you have no credentials,
and ask for `aws configure`.

To bypass, use `--no-sign-request` (for example for accessing public
s3 storages)

Source:
https://dev.to/aws-builders/access-s3-public-data-without-credentials-4f06

## Update ssh host information

When an host change (e.g. reinstall), the ssh fingerprint change
and ssh complains (suspected man-in-the-middle).

To remove the old fingerprint: `ssh-keygen -R hostname`
On next ssh, you'll be able to take the new one

Source:
https://unix.stackexchange.com/questions/6533/is-there-an-easy-way-to-update-information-in-known-hosts-when-you-know-that-a-h

## Better grep

* ack
* rg (ripgrep)

## Making zoom screen share work

Following
https://community.zoom.com/t5/Meetings/Wayland-screen-sharing-broken-with-GNOME-41-on-Fedora-35/m-p/67283/highlight/true/page/11

I manage to have it work in Chromium with:
```
systemctl --user start pipewire.service
```

Replace `start` by `enable` so that's it's launched at startup

NB: I didn't manage to make it work with Firefox/Gnome using the
native window picker, only with Chromium

## Restrict Firefox memory usage using cgroups

1. Open a root shell in /sys/fs/cgroup
2. Create `firefox` (or any name) directory. The directory is
   populated with special files
3. Restrict memory.high to 8GB: `echo '8000000000' > memory.high`
4. Restrict memory.max to 9GB: `echo '9000000000' > memory.max`
5. Add firefox processes in this cgroup: `for p in $(pgrep -f firefox); do echo $p > cgroup.procs ; done`

The difference between `high` and `max` is: when reaching `high`, the
processes are not responding to input (seem frozen but continue to
process), and when reaching `max`, it starts to kill processes.


## git shortlog

Get a list of commit messages between 2 commits, ordered by author:
`git shortlog [COMMIT1]..[COMMIT2]`

## Go: use a local dir as dependency

If you have this:
```
github.com/bmc-toolbox/bmclib/v2 v2.2.0
```

Add this at then end of go.mod:
```
replace github.com/bmc-toolbox/bmclib/v2 v2.2.0 => ../bmclib
```

## dbus basics

Get the list of *services*: `busctl`

Get the *object* tree of a *service*: `busctl com.service.ServiceName`

Get *methods/interfaces* of an *object*: `busctl introspect
com.service.ServiceName /com/service/object_name`

## Emacs: search replace with newline

For example, you want to replace `<br>` or `\n` with a real newline in
a buffer.

Make search and replace, then `\n` then `C-q` `C-j` (quoted-insert,
newline)

## next tip
