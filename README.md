MattHorDownloader
=================

Version 1.0

## Information

MattHorDownloader allows you to download recordings for Opencast/Matterhorn
(http://www.opencast.org) with multiple video channels provided within the
moodle platform. You can watch the speech and the slides of each recording
synchronously by using vlc (https://www.videolan.org/vlc/). Just select
the second video channel within the video sub menu.

## Requirements

MattHorDownloader currently only runs on a unix system (shell, env, xargs,
wget). To use it on a windows system, you can use cygwin
(https://www.cygwin.com/). With Windows 10 you can use the Ubuntu Bash
(https://msdn.microsoft.com/commandline/wsl) (Not tested).

Requirements are: python3, shell, env, xargs, wget and mkvtoolnix.

## Install

With apt (Debian/Ubuntu and Windows 10 Ubuntu Bash):

Install requirements:

```
sudo apt install git python3 mkvtoolnix wget findutils

```

Clone the git project:

```
git clone https://github.com/manuelbusch/MattHorDownloader.git
```

## Disclaimer

No warranty! Use at your own risk!

## Usage


### 1. Create a pipe separated csv file recordings.csv without a header.

Add a line in recordings.csv for each recording

Example:

```
Title of Recording|https://[host]/[...]/watch.html?id=[id]
```
### 2. Identify the MDL-Value

You can use the web developer tools provided by many browsers to
identify the mdl value. Open the network analyzer and search for
the resource watch.html URL after clicking on the link opening 
the player inside moodle.

```
https://[host]/[...]/watch.html?id=[...]&mdl=[mdl]
```
### 3. Get required episode informations:
```
./get-episodes recordings.csv [mdl] > episodes.json
```
### 4. Download all the tracks:
```
./track-download-params episodes.json [--destination_dir DESTINATION_DIR] | ./track-download
```
### 5. Create a mkv file for each episode:
```
./episode-mkvmerge episodes.json [--source_dir SOURCE_DIR] [--destination_dir DESTINATION_DIR]
```

## Todo

* Insert table of contents to the matroska container
