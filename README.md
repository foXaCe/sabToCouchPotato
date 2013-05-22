nzbToMedia
================

Provides an efficient way to handle postprocessing for [CouchPotatoServer](https://couchpota.to/ "CouchPotatoServer") and [SickBeard](http://sickbeard.com/ "SickBeard")
when using one of the popular NZB download clients like [SABnzbd](http://sabnzbd.org/) and [NZBGet](http://nzbget.sourceforge.net/ "NZBGet") on low performance systems like a NAS. 
This script is based on sabToSickBeard (written by Nic Wolfe and supplied with SickBeard), with the support for NZBGet being added by [thorli](https://github.com/thorli "thorli") and further contributions by [schumi2004](https://github.com/schumi2004 "schumi2004") and [hugbug](https://sourceforge.net/apps/phpbb/nzbget/memberlist.php?mode=viewprofile&u=67 "hugbug").
Torrent suport added by [jkaberg](https://github.com/jkaberg "jkaberg") and [berkona](https://github.com/berkona "berkona")

Introduction
------------
Originally this was modifed from the SickBeard version to allow for "on-demand" renaming and not have My QNAP TS-412 NAS constantly scanning the download directory. 
Later, a few failed downloads prompted me to incorporate "failed download" handling.
Failed download handling is now provided for sabnzbd, by CouchPotatoServer; however on arm processors (e.g. small NAS systems) this can be un-reliable.

thorli's Synology DS211j was too weak to provide decent download rates with SABnzbd and CouchPotatoServer even by using sabToCouchPotato; His only alternative (as with many many QNAP and Synology users) was to switch to NZBGet which uses far less resources and helps to reach the full download speed. 

The renamer of CouchPotatoServer caused broken downloads by interfering with NZBGet while it was still unpacking the files. Hence the solution was thorli's version of sabToCouchPotato which has now been named "nzbToCouchPotato".

Failed download handling for SickBeard is available by using the development branch from fork [SickBeard-failed](https://github.com/Tolstyak/Sick-Beard.git "SickBeard-failed")
To use this feature, in autoProcessTV.cfg set the parameter "failed_fork=1". Default is 0 and will work with standard version of SickBeard and just ignores failed downloads.

Torrent support has been added with the assistance of jkaberg and berkona. Currently supports uTorrent, Transmissions, Deluge and possibly more.
To enable Torrent extraction, on Windows, you need to install [7-zip](http://www.7-zip.org/ "7-zip") or on *nix you need to install the following packages/commands.
	
	"unrar", "unzip", "tar", "7zr"
	note: "7zr" is available from the p7zip package. Available on optware.
	
Contribution
------------
We who have developed nzbToMedia believe in the openess of open-source, and as such we hope that any modifications will lead back to the [orignal repo](https://github.com/clinton-hall/nzbToMedia "orignal repo") via pull requests.

Founder: [clinton-hall](https://github.com/clinton-hall "clinton-hall")

Contributors: Can be viewed [here](https://github.com/clinton-hall/nzbToMedia/contributors "here")

In order to use the transcoding option you will need to install ffmpeg.
Installation instructions for this are available in the [wiki](https://github.com/clinton-hall/nzbToMedia/wiki/Transcoder "wiki")


Installation
------------

### Windows

Download the the compiled versions of this code from the links provided here [nzbToMedia installation](https://github.com/clinton-hall/nzbToMedia/wiki/installation)

### General

1. Clone or copy all files into a directory wherever you want to keep them (eg. /scripts/ in the home directory of your nzb client) 
   and change the permission accordingly so the download client can access these files.
	
	git clone git://github.com/clinton-hall/nzbToMedia.git

### Configuration

1. Rename the file autoProcessMedia.cfg.sample to autoProcessMedia.cfg and fill in the appropriate 
   fields in [SickBeard], [CouchPotato], [Torrent]as they apply to your installation.

2. Please read the wiki pages on this repo for further configuration settings appropriate to your system.

3. Please add to the wiki pages to help assist others ;)

### NZBGet (V11+)

1. Place the nzbToMedia folder inside the ppscripts folder. These scripts can now be configured via the web UI.

2. Run scripts (for all required categories) in this order.

	DeleteSamples.py, nzbToMedia*.py, Email.py, Logger.py

3. For Windows compiled versions, set the same config for all categories.

	DeleteSamples.bat, nzbToMedia.bat
 
### Issues

1. Please report all issues, or potential enhancements using the issues page on this repo.
