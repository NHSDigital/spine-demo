NRL Workshop ReadMe
===================

Setting Up
----------
1.	Download the repository from Github. Feel free to pair up with someone if you don't have a laptop.
2.	Download and install Postman at - https://www.postman.com/downloads/

   + 2a. If using Linux follow steps 2a and 2b. Extract the tar.gz file in your chosen location. In the terminal move to the directory with your tar.gz file you downloaded. You can use the command **tar -C /{extract path} -zxvf {yourfile}.tar.gz** to extract your tar file to a chosen extract path. 
  
   + 2b - Launch Postman by running - **./{path to your extracted Postman files}/Postman/app/Postman**
 
3. Launch Postman and click on the **Settings** icon (the wrench in the top right corner). Make sure **SSL certificate verification** is turned **OFF**. 
4.	On Postman click the import button (top left) and import **NRL.postman_collection.json file** from the repo. You should see an NRL folder on the left sidebar. You may need to switch to the Collections tab on the left if you don't see it.
5.	Go to the NHS number spreadsheet(https://docs.google.com/spreadsheets/d/1jzXrC_5nWPcoq5n5fhU4qPk-nFtUT9-VIvK-rjW_t2c/edit?usp=sharing). Select your test NHS number to use. Copy this somewhere safe and put Y in the "In use?" column on the spreadsheet.

**NOTE: Certificate checks have been removed from the server to allow simpler workshop access.**

Create a pointer
----------------
1.	Go to the NRL collection folder in Postman and select the **POST – Create Pointer**.
2.	Everything has been configured for you apart from the request body. Switch to the **Body** view (this is just under the POST URL field) and click the **raw** radio button. This should be empty and will need adding to in the next steps.
3.	As this is a FHIR API you can choose to use either **nrl_create_pointer.xml** or the **nrl_create_pointer.json** template as your request body. This is from the repo you downloaded. Edit the template to use your chosen NHS number in the Subject -> Reference URL value. The URL value should look something like "https://demographics.spineservices.nhs.uk/STU3/Patient/{your test NHS number}".
4. Continue to edit the template to include the type of document for your pointer. Look at the type -> coding -> code value and the type -> coding -> display value. These fields will need to be added to. As this is a test you can pick any matching code/display value from the table below

| Code | Display |
| :-------: | :-------: |
| 736253002 | Mental health crisis plan |
| 736253003 | Mental health report |
| 736253004 | Maternity record |
| 736253005 | Child health plan |
| 736253006 | Cancer treatment plan |
| 736253007 | Diabetes treatment plan |
| 736253008 | Urgent care plan |

It should like this once you have added the code and display values:

JSON
```json
  "type": {
    "coding": [
      {
        "system": "http://snomed.info/sct",
        "code": "736253002",
        "display": "Mental health crisis plan"
      }
    ]
  }
```

XML
```xml
	<type>
		<coding>
			<system value="http://snomed.info/sct"/>
			<code value="736253002"/>
			<display value="Mental health crisis plan"/>
		</coding>
	</type>
```

5. Copy and paste your edited template into the request body for your POST. Make sure you select the dropdown type to either **XML or JSON** depending on your template.

6. Press Send. Check the response outcome to see if the diagnostic value says **"Successfully created resource DocumentReference"**. If you get this then congratulations you have created your NRL pointer! 

If you would like to see your pointer on the mobile Summary Care Record Application, go back to the NHS number spreadsheet and put Y in the Ready to view column. We will display these pointers later in the workshop.

If you don't get this response please double check your request body and try again. Incorrect spelling or extra spaces could be your issue. Feel free to ask for help or to ask any questions. 

Now you can try to retrive those pointer details, delete it (unless you want to see it on the the Summary Care Record later) or create another pointer for the same or a different NHS number. 


Retrieve a pointer
------------------
1.	Go to the NRL collection folder in Postman and select the **GET by subject**.
2.	Change the GET URL ending to /Patient/{Your Test NHS Number}
3.	Press Send and look at the response outcome to see if your pointer details are there for your patient.

Remove a pointer
----------------
1.	Go to the NRL collection folder in Postman and select the **Delete – Remove Pointer**.
2.	Change the DELETE URL ending to /DocumentReference/{Your Pointer ID}. In order to get the pointer ID see the instructions in Retrieve a pointer and look for your pointer's ID.
3.	Press Send and look at the response outcome to see if your pointer has been deleted.


