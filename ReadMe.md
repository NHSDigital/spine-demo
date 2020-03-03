NRL Workshop ReadMe
===================

Setting Up
----------
1.	Download the repository from Github. Feel free to pair up with someone if you don't have a laptop.
2.	Download and install Postman at - https://www.postman.com/downloads/

   + 2a. If using Linux follow steps 2a and 2b. Extract the tar.gz file in your chosen location. In the terminal move to the directory with your tar.gz file you downloaded. You can use the command **tar -C /{extract path} -zxvf {yourfile}.tar.gz** to extract your tar file to a chosen extract path. 
  
   + 2b - Launch Postman by running - **./{path to your extracted Postman files}/Postman/app/Postman**
 
3. Launch Postman and click on the **Settings** icon (the wrench in the top right corner). Make sure **SSL certificate verification** is turned **OFF**. 
4.	Launch Postman and import the **NRL.postman_collection.json file** from the repository. You should see an NRL folder on the left sidebar.
5.	Go to the NHS number spreadsheet(https://docs.google.com/spreadsheets/d/1jzXrC_5nWPcoq5n5fhU4qPk-nFtUT9-VIvK-rjW_t2c/edit?usp=sharing). Select your NHS number to use. Copy this somewhere safe and put Y if you’re using it.

**NOTE: Certificate checks have been removed from the server to allow simpler workshop access.**

Create a pointer
----------------
1.	Go to the NRL collection folder in Postman and select the **POST – Create Pointer**.
2.	Everything has been configured for you apart from the request body. Switch to the **Body** view (this is just under the POST url field) and click the **raw** radio button. This should be empty and will need adding to.
3.	Choose to use either nrl_create_pointer.xml or the nrl_create_pointer.json template as your request body. Edit the template to use your chosen NHS number in the Subject -> Reference URL value. 
4. Edit the template to include the type of document for your pointer. Look at type -> coding -> code/display and add one of the below
code/display values:
   
- "code": "736253002"
   "description": "Mental health crisis plan"
      
- "code": "736253003",
   "description": "Mental health report",
 
- "code": "736253004",
  "description": "Maternity record",
 
-	"code": "736253005",
   "description": "Child health plan",
 
-	"code": "736253006",
   "description": "Cancer treatment plan",
 
-	"code": "736253007",
   "description": "Diabetes treatment plan",
 
-	"code": "736253008",
   "description": "Urgent care plan",

5. Copy and paste your edited template into the request Body for your POST. Make sure you select the dropdown type to either **XML or JSON** depending on your template.

6. Change the ending of the POST URL in Postman to use your NHS number you copied earlier e.g. /Patient/{Your Test NHS Number} and press Send. Check the response outcome to see if the diagnostic value says "Successfully created resource DocumentReference". If you get this then congratulations you have created your NRL pointer! Now you can try to retrive those pointer details or delete it next.

If you don't get this response please double check your request body and try again. Incorrect spelling or extra spaces could be your issue. Feel free to ask for help or to ask any questions. 

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


