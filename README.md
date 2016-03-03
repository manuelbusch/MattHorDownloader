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

###1. Add a line in recordings.csv for each recording
```
Title of Recording|https://[uri]/[...]/watch.html?id=[id]
```
###2. Get the MDL-Value

Install the plugin "Tamper Data" with firefox or a similar plugin. 
Go to the page where the link to the OpenCast player is listed.
Start the plugin and begin the tamper mode. Now you have to click the link 
that opens the OpenCast player. The tamper will open a dialog 
with a URL like this:
```
https://[uri]/[...]/watch.html?id=[...]&mdl=[mdl]
```
Now copy the the mdl value, allow the request and stop the tamper mode. 
You need the mdl value in step 3. with get-episodes.

###3. Get required episode informations:
```
./get-episodes recordings.csv [mdl] > episodes.json
```
###4. Download all the tracks:
```
./track-download-params episodes.json [destination_dir] | ./track-download
```
###5. Create a mkv file for each episode:
```
./episode-mkvmerge episodes.json [source_dir] [destination_dir]
```
