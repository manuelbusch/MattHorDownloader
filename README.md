#MattHorDownloader

##Information

MattHorDownloader allows to download recordings from MatterHorn.

##Requirements

MattHorDownloader currently only works with a unix system (xargs, wget).

Requirements are: python3, shell, xargs and wget.

##Disclaimer

No warranty! Use at your own risk!

##Usage

Create a csv file recordings.csv without header with the format "title|url".

Here you have to add a line for each recording.

 Title of Recording|https://[uri]/[...]/watch.html?id=[id]
 
Get required episode informations:

 ./get-episodes recordings.csv > episodes.json

Download all the tracks:
 ./track-download-paramenters episodes.json [destination] | ./track-download