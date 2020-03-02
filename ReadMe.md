NRL Workshop ReadMe
===================

Setting Up
----------
1.	Download the repository from Github. Feel free to pair up with someone if you don't have a laptop.
2.	Download and install Postman at - https://www.postman.com/downloads/

  2a. If using Linux follow steps 2a and 2b. Extract the tar.gz file in your chosen location. In the terminal move to the directory with your tar.gz file you downloaded. You can use the command **tar -C /{extract path} -zxvf {yourfile}.tar.gz** to extract your tar file to a chosen extract path. 
  2b - Launch Postman by running - **./{path to your extracted Postman files}/Postman/app/Postman**
  
3.	Launch Postman and import the **NRL.postman_collection.json file** from the repository. You should see an NRL folder on the left sidebar.
4.	Go to the NHS number spreadsheet(https://docs.google.com/spreadsheets/d/1jzXrC_5nWPcoq5n5fhU4qPk-nFtUT9-VIvK-rjW_t2c/edit?usp=sharing).

Select your NHS number to use. Copy this somewhere safe and put Y if you’re using it.

NOTE: Certificate checks have been removed from the server to allow simpler workshop access.
-----

Create a pointer
----------------
1.	Go to the NRL collection folder in Postman and select the “POST – Create Pointer”.
2.	Everything has been configured for you apart from the request body.
3.	Use the template nrl_create_pointer.xml or the json template. Edit the template to use your chosen NHS number in the Subject -> Reference URL value. Change the URL to use your NHS number you copied earlier e.g. /Patient/{Your Test NHS Number} 

Retrieve a pointer
------------------
1.	Go to the NRL collection folder in Postman and select the “GET by subject”.
2.	Change the GET URL ending to /Patient/{Your Test NHS Number}
3.	Press Send and check to see if your Record details are there for your patient.

Remove a pointer
----------------
1.	Go to the NRL collection folder in Postman and select the “Delete – Remove Pointer”.
2.	Change the DELETE URL ending to /Patient/{Your Pointer ID}. In order to get the pointer ID see the instructions in Retrieve a pointer.
3.	Press Send and check to see if your pointer has been removed.


