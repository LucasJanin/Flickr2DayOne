# Flickr2DayOne

After being present for many years on Flickr, I decided to import all my photos with descriptions, GPS, tags and comments on Day One.
I didn't find a solution for this process so I decided to use my favourite tool, Node Red to code this process.

First, you need to download toy data on the Flickr website. You can use "Download all your content (Flickr Data)" on this page: 
https://www.flickrhelp.com/hc/en-us/articles/4404079675156-Downloading-content-from-Flickr 

Create the folder /data/flickr/ with permission 777
Copy the Flcikr's JSON files in /data/flickr/ in your Node-Red

You need to create an account on geonames.org. This will use to get the timezone from the GPS data. This is the slower part of the process. Maybe, a better way is possible to achieve this part.
Add your username in the field of the "lookup timezone" node.

The data is stored in two files:
* /data/flickr/flickr.txt : Photos with GPS data (can be directly imported Day One)
* /data/flickr/flickrNTZ.txt : Photos without GPS data ("???" need to be fixed by hand in the text file before importation on Day One)

After you can import the two files on Day One.
  
Unfortunately, I wasn't able to import a JSON file on Day One, so I used "Plain Text File" what's limited.
So, some of the jobs need to be done "by hand":

* Add the GPS coordinates to the post (this will fix the time of the post. Note day saving isn't supported in this version)
* Add the photo to the post
  * Open the link to the direct image
  * Right-click and use "Copy Image" (in Firefox)
  * Right-click and use "Past" in the Day One post
  * Cleanup of the texts you don't like to keep
  
In my case, I have 980 photos, so it takes me time to do the "by hand" process but you don't need to do it at one time :-)

Feel free to contact me with any questions.
