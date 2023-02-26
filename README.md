# Flickr2DayOne

After being present for many years on [Flickr](https://www.flickr.com/photos/lucas3d), I decided to import all my 980 photos with descriptions, GPS, tags and comments on Day One. I didn't find a solution for this process, so I decided to use my favourite tool, Node-Red.
 
There is the result of the importation with a small hand change (moving the picture to the top of the entry).

![DayOne](DayOne.png)

## Prerequirements

Of cause you need [Node-Red](https://nodered.org). Be carfull, this sofwarre is very adictif ! :-)
If I was a better programing person, I will code it on python :-)

You need to isntall the [Day One CLI](https://dayoneapp.com/guides/tips-and-tutorials/command-line-interface-cli/) on your Mac:
```
sudo bash /Applications/Day\ One.app/Contents/Resources/install_cli.sh
```
You need to download your data on the Flickr website. You can use "Download all your content (Flickr Data)" on the [Flickr Help](https://www.flickrhelp.com/hc/en-us/articles/4404079675156-Downloading-content-from-Flickr). This is composed of a zip file of th JSON files and one or multiple zip files for the photos (dependind of the size of the Flickr library).

Create the folder /data/flickr/ with permission 777 in your Node-Red.
On my side, Node-Red run in a Docker container on my Synology NAS, my local path of the JSON files is:
```
/Volumes/docker/nodered/flickr/
```
Copy the Flickr's JSON files in this folder.

You need to extrast the zip files of the photos and copy them in your computer (not in Node-Red docker).
For me this path is:
```
~/Documents/DayOne/Flickr/Photos/
```

## GPS -> Timezone

GPS data need to be converted in Timezone. After using deferents services, I decided to use [TimezoneDB](https://timezonedb.com/register]). It's free with a registration. After creating your account, get your API key and add it in the node "prep request".

The free version have a limite of request (one every second). This "limitation" can slow down the process for very large librray. On my side, it take 50 minutes to process my 980 photos. 

## Output

The flow will ouput two type of file of each photo:
* sh : the CLI command to generate the entry
* md : text ot the entry

You can check the number of files generated in the terminal using "ls | wc -l" in the output folder: 
```
ls | wc -l /Volumes/docker/nodered/flickr/output/sh/
```
When this part is done, you use de bottom section to merge the sh files.
```
/Volumes/docker/nodered/flickr/merge/flickr.sh
```
You can execute this scripte to create on the the entries.

## The flow

![Flickr2DayOne Flow](Flickr2DayOne_flow.png)

The code: ![Flickr2DayOne Json](Flickr2DayOne.json)

Feel free to contact me with any questions.
