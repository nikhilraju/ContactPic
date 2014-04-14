README

 Contents of nr2483_nikhil_raju_hw2.zip:
 	* Project Folder: ContactPic 
 	* README.txt (this file)
	* ContactPic.apk



Steps Completed: 1-6

 Step 1: The UI contains a text field for input, a “Pick a Contact” button and a search button

 Step 2: For Pick a content, the contact name is retrieved from the Contacts.CONTACT_URI using an ACTION_PICK intent


 Step 3:
When the user clicks search, the REST API call is made using an HTTP Get Request in an Async Task
The URL is formed using the required  parameters as follows:
 http://api.flickr.com/services/rest/?method=flickr.photos.search&api_key={api key here}&tags={name here}&extras=date_taken,owner_name,description
 
 Step 4: The retrieved XML is parsed using a SAX Parser and the list of Photo result objects along with a list of URL’s for each photo is created

 Step 5:
A List View is used in the UI to display the photo results if found. These photos are loaded asynchronously and a lazy adapter is used which makes this step faster as the images get loaded as and when the user scrolls down thus avoiding unnecessary time wasted on fetching all images beforehand

 Step 6: When the user clicks an image intent is used to invoke a browser and show medium sized image of the thumbnail in the previous step


Steps not completed:

 Step 7 (Challenge/Bonus Points step)

	Watched online tutorials and attempted implementation of the pull to refresh 		functionality on the UI but could not get it to work in time for the submission. 

Overview:

The following functionalities are implemented:
 In case the user does not enter any contact information, a toast with an appropriate message is displayed to the user when he clicks on search

If the contact name contains spaces, the space in the string is replaced by %20 while forming the url because otherwise the application would crash if there are spaces

Some important Files in the project:

1) MainActivity.java:
This is the home screen of the application and contains the necessary UI elements to take input from the user. The input is passed using an Intent to the next activity where the URL is created and GET request, parsing and subsequent operations are done

2) FlickrAcitvity.java:
This is where bulk of the work for this application is done. An Async task is used because  HTTP GET Requests,retrieving images etc are network intensive operations which Android does not allow to be run on the Main Thread.
The “FlickrGetRequestTask” is used to retrieve images 

3) FlickrSAXParser.java:
This contains the logic for parsing the XML result for each URL.
It retrieves the required details such as owner,date, description, farm etc and stores it as attributes of a Photo object.
A list of the Photo objects in the result is also created along with a list of the corresponding URL’s


4) Photo.java 

is a class created to store required details such as owner,date, description, farm and other details needed to create the URL or details to be displayed for the output.
These are stored as attributes of the Photo object and the result is a set of Photo objects

5) LazyAdapter.java:
A lazy adapter is used which makes this step faster as the images get loaded as and when the user scrolls down thus avoiding unnecessary time wasted on fetching all images beforehand.
The photos are loaded asynchronously. and 


Implementation Details:


For Step 5:
 I have discussed this step with (Shrutika sd2841) and together we found the following online tutorial which explains how to use List View and implement a Lazy Adapter to load the images 
	http://www.youtube.com/watch?v=uRPj6d-9g0U

The code for loading the images has been used from the github repository mentioned in the above video:
https://github.com/thest1/LazyList

and modified as per the requirements for this application

Learnt following while working on this Homework:

 1) Basics of Android,ADT,application design,using AVD,debugging,understanding and using logcat
 2) UI Elements such as TextView,ImageView,Toast, ListView
 3) AsyncTask to carry out  tasks that require network resources or are computationally 	      expensive
 4) How to use Intent to pass control to various activities
 5) How to use XML Parsing in applications (used SAX Parser as I found it easier to understand compared to the PullParser mentioned in the HW instructions)
 6) Logo, splash screen and UI elements


