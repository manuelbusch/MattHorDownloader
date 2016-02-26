#MattHorDownloader

##Information

MattHorDownloader allows to download recordings from Opencast/Matterhorn (http://www.opencast.org).

##Requirements

MattHorDownloader currently only works with a unix system (shell, env, xargs, wget). For the use with a windows system, you can use cygwin (https://www.cygwin.com/).

Requirements are: python3, shell, env, xargs, wget and mkvtoolnix.

##Install

With apt (Debian/Ubuntu):

```
sudo apt-get install git python3 mkvtoolnix wget findutils

git clone https://github.com/manuelbusch/MattHorDownloader.git
```
##Disclaimer

No warranty! Use at your own risk!

##Usage

Create a csv file recordings.csv without header with the format "title|url".

Here you have to add a line for each recording.
```
Title of Recording|https://[uri]/[...]/watch.html?id=[id]
```
Get required episode informations:
```
./get-episodes recordings.csv > episodes.json
```
Download all the tracks:
```
./track-download-paramenters episodes.json [destination_dir] | ./track-download
```
Create a mkv file for each episode:
```
./episode-mkvmerge-params episodes.json [source_dir] [destination_dir] | ./episode-mkvmerge
```
