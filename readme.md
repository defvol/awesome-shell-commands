# awesome-shell-commands [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

> A curated list of tasks done from the command line


## Contents

- [Hardware specs](#hardware-specs)
- [Media](#media)
- [Misc](#misc)
- [Networking](#networking)
- [Operating system](#operating-system)
  - [Disk](#disk)
- [Programmer](#programmer)
- [Security](#security)


## Hardware specs

Querying the OS to get hardware info.

- Connected usb devices: `lsusb`
- Details on a usb device: `lsusb -d vendorId:productId -v`
- Get graphic controllers: `lspci | grep -i vga`
- Get graphic controllers (detailed): `lshw -C video`

## Media

From GIFs to movie editing.

- Download video from youtube: `youtube-dl https://www.youtube.com/watch?v=tN12Tg5ttpk -f mp4`
- Extract audio from video: `ffmpeg -i ytcracker\ -\ meganerd-tN12Tg5ttpk.mp4 meganerd.mp3`
- Play mp3: `ffplay meganerd.mp3` `mplayer meganerd.mp3`

### File conversion

- GIF to MP4 and viceversa: `ffmpeg -f gif -i infile.gif outfile.mp4`
- OGV to MP4: `ffmpeg -i out.ogv -strict -2 out.mp4`
- PNG to PDF: `convert grid.png -gravity center grid.pdf`
- Make a GIF from a screencast:
```sh
ffmpeg -i mem-01.ogv frames/ffout%03d.png
convert -loop 0 frames/ffout* mem-01.gif
convert mem-01.gif -fuzz 10% -layers Optimize optimized.gif
```

### Image editing

- Resize your 100MB smartphone picture: `convert IMG_2000.jpg -resize 1024x IMG_2000_resized.jpg`

### Video editing

- Clip video (starting from second 3): `ffmpeg -i take-3.mp4 -ss 00:00:03 -t 00:02:04 output.mp4`
- [Crop video](https://video.stackexchange.com/questions/4563/how-can-i-crop-a-video-with-ffmpeg#4571): `ffmpeg -i in.mp4 -filter:v "crop=out_w:out_h:x:y" out.mp4`
- Speed video up: `ffmpeg -i take-4.mp4 -filter:v "setpts=0.5*PTS" take-4-faster.mp4`
- Remove audio from video: `ffmpeg -i loud.mp4 -c copy -an muted.mp4`
- Resize video: `ffmpeg -i larger.mp4 -filter:v scale=720:-1 -c:a copy smaller.mp4`
- Pull video metadata: `exiftool take.mp4`
- Timelapse a video:
```sh
ffmpeg -i input.mp4 -r 1 -f image2 frames/%05d.png
ffmpeg -i frames/%05d.png timelapse.mp4
```

## Misc

KEWL

- Compress a directory: `tar -zcvf archive-name.tar.gz directory-name`
- Zip a directory: `zip -r foo.zip foo/`
- Delete old files: `rm $(ls -lh *csv | grep "Dec 18" | cut -d' ' -f11)`
- Nyancat: `nc -v nyancat.dakko.us 23`
- Record X11 action: `cnee --record -o automate-this.xnr --mouse --events-to-record 1000 --time 2`
- Replay X11 action: `cnee --replay -f automate-this.xnr --time 2`
- [Rotate the screen](https://askubuntu.com/questions/95812/how-can-i-rotate-my-display-in-the-most-easy-way): `xrandr --output HDMI-1 --rotate inverted`

## Networking

Connect, scan, and ping the interwebz.

- Connect to VPN: `nmcli con up id sub.kewlvpn.lol`
- Check avail networks: `nmcli con`
- Incognito browsing: `firefox --private-window` `chromium-browser --incognito`

## Operating system

Querying info about the OS

- Architecture: `uname -m`
- Distro: `cat /etc/*release`
- Distro name: `lsb_release -cs`
- Find process running on a specific port: `ss -lptn 'sport = :3000'`
- Most recent kernel messages: `dmesg | tail`
- Packages installed (debian|ubuntu): `dpkg -l`
- List all processes sorted by memory: `ps aux --sort -rss`
- Specific package installed: `dpkg -l nvidia*`
- Watch memory every 5 seconds: `watch -n 5 free -m`

### Disk

- Mounted partitions (in human-friendly units): `df -h`
- Summary of disk space used by directories: `du -hs *`
- [List virtualbox disks](https://myshittycode.com/2013/11/23/virtualbox-failed-to-delete-the-storage-unit-of-the-hard-disk-pathhard-disk-vdi-cannot-close-medium-pathhard-disk-vdi-because-it-has-n-child-media/): `VBoxManage list hdds`
- [Close a stuck virtual box disk so you can remove it](https://myshittycode.com/2013/11/23/virtualbox-failed-to-delete-the-storage-unit-of-the-hard-disk-pathhard-disk-vdi-cannot-close-medium-pathhard-disk-vdi-because-it-has-n-child-media/): `VBoxManage closemedium disk 633abeef-c3a0-43b0-b371-1238adeac4c`

## Programmer

Optimizing workflow for the lazy programmer

- Delete all node_modules recursively: `find . -name 'node_modules' -type d -prune -exec rm -rf '{}' +`
- Delete all containers named like mongo: `docker rm $(docker ps -a | grep mongo | cut -f 1 -d' ')`
- Stop all containers: `docker stop $(docker ps -a -q)`
- Remove all containers: `docker rm $(docker ps -a -q)`
- Remove all images: `docker rmi $(docker images -q)`
- [Get latest git-commit id](https://stackoverflow.com/questions/19176359/how-to-get-the-last-commit-id-of-a-remote-repo-using-curl-like-command#19176626): `echo $(git log --format="%h" -n 1)`
- Updating author in git history:
```sh
git rebase -i -p <commit-to-start-from>
git commit --amend --author="John Snow <jsnow@thewall.com>"
```

## Security

- Add password to PDF: `pdftk [mydoc].pdf output [mydoc.128].pdf owner_pw [foo] user_pw [baz]`
- Symmetric encryption using GPG: `gpg -c filename`
- Encrypt a zipfile: `zip --encrypt file.zip.enc file`

## Contribute

Contributions welcome! Read the [contribution guidelines](contributing.md) first.


## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](http://creativecommons.org/publicdomain/zero/1.0)

To the extent possible under law,  has waived all copyright and
related or neighboring rights to this work.
