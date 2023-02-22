# Flickr2DayOne

After being present for many years on [Flickr](https://www.flickr.com/photos/lucas3d), I decided to import all my 980 photos with descriptions, GPS, tags and comments on Day One. I didn't find a solution for this process, so I decided to use my favourite tool, Node-Red.

![Flickr2DayOne Flow](Flickr2DayOne_flow.png)

The code: ![Flickr2DayOne Json](Flickr2DayOne.json)

First, you need to download toy data on the Flickr website. You can use "Download all your content (Flickr Data)" on the [Flickr Help](https://www.flickrhelp.com/hc/en-us/articles/4404079675156-Downloading-content-from-Flickr).

Create the folder /data/flickr/ with permission 777 in your Node-Red.
Copy the Flickr's JSON files in this folder.

## GPS data

First, I used [geonames.org](http://geonames.org) but it was creating error and Node Red instabilities.
I move using [Google Time Zone API](https://developers.google.com/maps/documentation/timezone/overview). 

### Pre-requisites

You must enable the Google APIs.
In the Google Developer Console under "Api & auth" select "APIs"
Search for "Time Zone API" click on it and then click "Enable API"
or see - https://code.google.com/apis/console
You need to activate your account (need to be completed).
Copy you API key and place it the code of the "prep request" node.

### Process

This will use to get the timezone from the GPS data. This is the slower part of the process and this request create eorr after an certain number of requests. I decided to split de process of the JSON files in 10 parts to help. For now, just retry multiple time until all the bastch is processed. You can check the files numer in linux/mac terminal using "ls | wc -l" in the output folder (/data/flickr/output).

It's definitely a temporal solution.
I'm sure it existe a better way to achieve this part. I open for subjection.

## Output

When this part is done, you use de bottom section to merge the files in two files:
* /data/flickr/merge/flickr_TZ.txt : Photos with GPS data (can be directly imported Day One)
* /data/flickr/merge/flickr_NTZ.txt : Photos without GPS data ("???" need to be fixed by hand in the text file before importation on Day One)

After you can import the two files on Day One.

## By Hand Fixes

Unfortunately, I wasn't able to import a JSON file on Day One, so I used "Plain Text File" what's limited.
So, some part of the jobs need to be done "by hand". You can filter the posts using "flickrImport" to easy find all the poste to fix.

* Add the GPS coordinates to the post
  * Copy location data present in the post (like "34.120273,-118.183643")
  * Right-click the bottom bar of the post
  * Select "location / Edit"
  * Past it in the search field
  * Click on the "Search Result"
  * Click "Ok"
    * This will fix the time of the post
    * Note: I still have some offset in beween the reeal time and Day One time. I add an extra hour, this is look working for part of my photos.
    
* Add the photo to the post
  * Open the link to the direct image
  * Right-click and use "Copy Image" (in Firefox)
  * Right-click and use "Past" in the Day One post

* Cleanup of the texts you don't like to keep
 
## Result 
 
In my case, I have 980 photos, so it takes me time to do the "by hand" process, but you don't need to do it at one time :-).
There is the result of the importation with some hand integration.

![DayOne](DayOne.png)


Feel free to contact me with any questions.
