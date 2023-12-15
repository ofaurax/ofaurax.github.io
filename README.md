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

## Making zoom scren share work

Following
https://community.zoom.com/t5/Meetings/Wayland-screen-sharing-broken-with-GNOME-41-on-Fedora-35/m-p/67283/highlight/true/page/11

I manage to have it work in Chromium with:
```
systemctl --user start pipewire.service 
```

Replace `start` by `enable` so that's it's launched at startup

