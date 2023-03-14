
# Unit 3: Habit Tracker
![Habit Tracker](https://user-images.githubusercontent.com/111819437/221088557-8b25c774-0b8f-4644-879f-42737e64fa18.png)
Fig.1 Authoral design

# Criteria A: Planning


## Problem definition
Sabuhi Abassov, an ambitious and hard-working first-year International Baccalaureate (IB) student at UWC ISAK Japan, has a lot on his plate. With a rigorous academic curriculum, extracurricular activities, and a bustling social life, his schedule is completely jam-packed which made it challenging for him to have productive days and maintain a consistent routine. Despite his best efforts to stay organized and productive, Sabuhi has been struggling to keep up with his daily habits and maintain a consistent routine. As a result, Sabuhi is in need for a solution to help him monitor his habits and improve his overall lifestyle.

## Proposed Solution
### Design Statement
Recognizing the difficulties Sabuhi has been facing with productivity I decided to develop an Habit Tracker. This tracker will allow Sabuhi to mark his daily activities, monitor his progress, and track his habits to ensure that he stays on track with his goals.The Habit Tracker will be tailored to Sabuhi's needs and will be designed to help him focus on the areas that require improvement. By using this tool, Sabuhi can identify which habits are hindering his productivity and which ones are helping him achieve his goals. Additionally, the Habit Tracker will provide a notes session for each day to allow him reflect on his day and a space to addhow he is feeling 8uy
### RATIONALE
To make the solution I will use the program language Python, because is a highly versatile programming that can be used for various applications, including web development, scientific computing, data analysis, and artificial intelligence. It has a supportive and engaged community, straightforward syntax, and is well-suited for quickly building applications with fewer errors.

I will also use the Kivy MD library to make the interface because it enables the creation of cross-platform applications for Android, iOS, and Windows. It is user-friendly and provides various customization options for creating unique applications with less effort.

To store the information I will use the SQL lite database,because it is optimized for efficiently managing and storing large amounts of data, which makes it a reliable choice for applications that need to handle and scale with growing amounts of data. It enables the storage of structured data that can be easily queried and analyzed, while also providing data integrity and transaction management features to ensure data accuracy and consistency.



## Design Statement

## Success Criteria
1. The solution should enable users to track their daily habits, including working out, studying, reading, journaling, water intake and sleeping.
2. The solution must be designed with security and privacy in mind, with measures to protect the user's data.
3. The solution must iclude a notes session for each day.
4. The solution must provide a way for the user to vizualize their progress.
5. The solutions must provide a session to monitorize the mental health of the user.
6. The solution must provide an option to delete days.

# Criteria B: Design
## System Diagram
![Habit Tracker (1)](https://user-images.githubusercontent.com/111819437/221175995-de796e99-0cd0-4adc-b9dc-2a47f8e016a4.png)
Fig1.Figure 1 - The System diagram for the application is illustrated in Figure 1,for the application. As shown in the figure 1, the application uses PyCharm and the libraries: KivyMD Library,Connect_database and Secure_password to develop the program. The arrows represent the data that is stored in the database Project.db, using the SQLite database engine.

## Wireframe
![Screen Shot 2023-03-11 at 17 59 32](https://user-images.githubusercontent.com/111819437/224475360-a310079e-ca8e-404a-8c1f-27ccd9935d21.png)

## UML Diagram

## ER Diagram
![Habit Tracker (2)](https://user-images.githubusercontent.com/111819437/224590115-dbef85b4-d4eb-4be8-860b-931aa6b0109c.png)


## Flow Diagram



## Test Plan
| Description | Type | Inputs | Outputs | 
| ----------- | ---- | ------ | ------- |




## Record of Tasks
| Task No 	| Planned Action                                                                                                                 	| Planned Outcome                                                                                                       	| Time estimate 	| Target completion date 	| Criterion 	|
|---------	|--------------------------------------------------------------------------------------------------------------------------------	|-----------------------------------------------------------------------------------------------------------------------	|---------------	|------------------------	|-----------	|
| 1       	| meeting with client                                                                                                            	| Start collecting the context of the problem                                                                           	| 6min          	| 7 february             	| A         	|
| 2       	| Write the problem definition                                                                                                   	| To have a clear ideia for the proposed solution                                                                       	| 15 min        	| 7 february             	| A         	|
| 3       	| Write the design statement - Proposed solution                                                                                 	| To have a better idea on how the application is going to look like                                                    	| 20 min        	| 9 february             	| A         	|
| 4       	| Define the success criterias with client                                                                                       	| To have a clear idea about the features in the application                                                            	| 20 min        	| 9 february             	| A         	|
| 5       	| Rationale for proposed solution                                                                                                	| To have a clear idea about the tools that are going to be used.                                                       	| 20 min        	| 9 february             	| A         	|
| 6       	| Meet with client for criteria A acceptance                                                                                     	| To make clear the project statements between the client and developer                                                 	| 10 min        	| 10 february            	| A         	|
| 7       	| Drawn the system diagram                                                                                                       	| To have a clear idea of the hardware and software requirements for the proposed solution                              	| 1 hour        	| 10 february            	| B         	|
| 8       	| Draw the wireframe                                                                                                             	| Have a clear view of how the app is going to look like                                                                	| 2 hour        	| 10 february            	| B         	|
| 9       	| Create the py and kv code for the login page                                                                                   	| Make the user able to login in the program                                                                            	| 1 hour        	| 13 february            	| C         	|
| 10      	| Create the database for the program and the table user                                                                         	| Save the user's data                                                                                                  	| 20 min        	| 13 february            	| C         	|
| 11      	| Create the py and kv code for register page                                                                                    	| Sign up page                                                                                                          	| 1 hours       	| 15 february            	| C         	|
| 12      	| Create a hash function for password                                                                                            	| To fill the criteria to protect users data                                                                            	| 30 min        	| 17 february            	| C         	|
| 13      	| Create the py and kv code for main page                                                                                        	| Page with the features-"Add new day", "check your progres" and "Log out"                                              	| 1 hour        	| 19 february            	| C         	|
| 14      	| Make the "add" page to add new days to the tracker                                                                             	| add new days to the database                                                                                          	| 1 hour        	| 19 february            	| C         	|
| 15      	| make the validation for the input in the features  - Checkboxes,notes sessions, overall slider and date picker on the add page 	| Make sure that the user enter the correct input                                                                       	| 1 hour        	| 20 february            	| C         	|
| 16      	| Make the progress page                                                                                                         	| Make the user able to see their progress                                                                              	| 30 minutes    	| 23 february            	| C         	|
| 17      	| Meet with the client again to present the application                                                                          	| Receive feedback on the program                                                                                       	| 30 minutes    	| 25 february            	| A         	|
| 18      	| Add pop up dialogs on each page as a client request                                                                            	| Make the user able to know when the login/registration is correct and when adding a day to the database was sucsseful 	| 1 hour        	| 26 february            	| C         	|
| 19      	| Start working on documentation - List of techiniques                                                                           	| Make a list of all thechiniques used on the project                                                                   	| 30 minutes    	| 27 february            	| B         	|
| 20      	| Make the UML diagram                                                                                                           	| Make the uml diagram with all class and explain it                                                                    	| 1 hour        	| 27 february            	| B         	|
| 21      	| Make the flowdiagrans                                                                                                          	| Draw 3 flodiagrans and explain it                                                                                     	| 1 hour        	| 28 february            	| B         	|
| 22      	| Create the test plan                                                                                                           	| Make sure that the code has no errors                                                                                 	| 30 min        	| 1 march                	| B         	|
| 23      	| Improve the coding practices                                                                                                   	| Check the variables names, classes names and comments                                                                 	| 1 hour        	| 1 march                	| B         	|
| 24      	| Add the development of each success criterias                                                                                  	| Write how the criteria was developed                                                                                  	| 2 hours       	| 2 march                	| B         	|
| 25      	| Improve the documentation - criteria C                                                                                         	| Add more explanations                                                                                                 	| 30 minutes    	| 3 march                	| C         	|
| 26      	| Fix the errors pointed on the test plan                                                                                        	| Improve the code functionality                                                                                        	| 3 hours       	| 6 march                	| C         	|
| 27      	| Present the final product to client                                                                                            	| Gte final approve                                                                                                     	| 20 minutes    	| 8 march                	|           	|
| 28      	| Record video of program working                                                                                                	| Video of program working with explanations about the functionality                                                    	| 1 hour        	| 7 march                	| C         	|

**Table 2** 




# Criteria D: Functionality
## A 7 min video demonstrating the proposed solution with narration


