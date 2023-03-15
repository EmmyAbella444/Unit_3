
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

To create a comprehensive and effective solution, I have decided to use Python as the primary programming language. Python is an incredibly versatile programming language that can be used for a wide range of applications, such as web development, scientific computing, data analysis, and artificial intelligence. This is possible because Python has a supportive and engaged community that provides comprehensive documentation, making it easy to learn and use.

Furthermore, Python has a straightforward syntax that is easy to read and write, which makes it well-suited for quickly building applications with fewer errors. This ensures that the solution I create will be efficient, reliable, and easily maintainable in the long term.

In addition to Python, I will be using the Kivy MD library to create the program's user interface. This library enables the creation of cross-platform applications for Android, iOS, and Windows, which is essential in today's digital landscape. It provides a wide range of customization options, making it possible to create unique and visually appealing applications with minimal effort. Furthermore, the Kivy MD library is user-friendly, allowing me to create an intuitive user interface that will enhance the user experience.

To store the data, I will be using the SQLite database engine. This database engine is optimized for efficiently managing and storing large amounts of data, which makes it a reliable choice for applications that need to handle and scale with growing amounts of data. The SQLite database engine enables the storage of structured data that can be easily queried and analyzed, while also providing data integrity and transaction management features to ensure data accuracy and consistency. This will enable me to create a robust and reliable solution that can handle a significant amount of data while maintaining data accuracy and consistency.


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

Figure 2 depicts the system diagram of the application. The application use PyCharm as well as the KivyMD Library, Connect_database, and Secure_password libraries to create the program. The arrows in the diagram indicate the data that is stored in the Project.db database, which utilizes the SQLite database engine.


## Wireframe
![Screen Shot 2023-03-11 at 17 59 32](https://user-images.githubusercontent.com/111819437/224475360-a310079e-ca8e-404a-8c1f-27ccd9935d21.png)

Figure 3 illustrates the wireframe design of the program interface. Upon accessing the Login screen, the user is presented with two options: to log in or register. Opting to register will redirect the user to the Registration page, featuring text fields prompting for a username, email, and password. After successful registration, the user is directed back to the Login screen. Once the user logs in successfully, they will be directed to the Main screen, which features three options: "Add new day," "Check your progress," and "Log out." Choosing "Add new day" leads the user to the "Add" page, where they can input data in the checkboxes and text fields and then choosing to add the new entry to the database or return to the Main screen. Selecting the "Check your progress" button in the Main screen takes the user to the Progress page, where a table displays the user's progress. Here, the user can view their progress, delete an entry, or return to the Main screen. Lastly, the "Log out" button on the Main screen logs the user out and redirects them to the Login screen.

## UML Diagram
![uml (1)](https://user-images.githubusercontent.com/111819437/225409035-09811463-3d0b-4280-97f1-1a20b9f4c71d.png)
Thefigure 4 is a UML (Unified Modeling Language) class diagram, which is a type of diagram used in software engineering to visualize the structure and relationships of object-oriented programming (OOP) classes. This UML illustrates. In the diagram, each class is represented by a rectangle containing the class name, attributes, and methods. Arrows between the classes denote inheritance relationships.

## ER Diagram
![Habit Tracker (2)](https://user-images.githubusercontent.com/111819437/224590115-dbef85b4-d4eb-4be8-860b-931aa6b0109c.png)

In Figure 5, it is illustrated the Entity Relationship (ER) diagram for the application, which provides a visual representation of the database schema. The ER diagram shows the two tables that exist within the database: "users" and "habits"
The first table is called "users," and it is responsible for storing all user-related information such as their username, email, and password. This table is essential for the application's functionality since it enables users to register and log in to the program, allowing them to access their data and track their progress over time.
The second table is called "habits," and it stores information about the users' habits, such as sleep, water intake, reading, journaling, gym , studying, overall, total ,notes, date, id, and user. The habits table is closely related to the users' table since each user will have their set of habits and associated data stored within this table.
By using a database schema with two tables, we can ensure that the data is organized, easy to manage, and efficient to query. The users' table stores all user data, which enables efficient user management, while the habits table allows the program to track and analyze each user's progress over time. This organized data will help the application function more effectively, enabling users to easily track their progress and achieve their goals.

## Flow Diagrans
## Flow diagram to create a new table
![flow diagram 1 (1)](https://user-images.githubusercontent.com/111819437/225429434-8b775e10-0902-45bc-8ea4-fbca3556b70b.png)

The figure 6 is a flowchart fot the create_table method that creates a database table called HABITS using SQL. The query variable contains an SQL command that creates the HABITS table with several columns, including id, user, date, gym, studying, sleeping, reading, journaling, water, notes, overall, and total. The id column is set as the primary key, which means that it uniquely identifies each row in the table. The if not exists clause in the CREATE TABLE command ensures that the table is only created if it doesn't already exist. This prevents an error from occurring if the table is already present in the databaseand then executes the SQL command and creates the HABITS table in the database.

## Flow diagram fo the log in function
![flow diagram 2 (1)](https://user-images.githubusercontent.com/111819437/225430359-613aa6c9-e5a7-4a12-a8f5-006a83721d42.png)

The figure 7 is a flowchart for the log in function that first,retrieves the inputted username and password from the relevant text input fields. Then, it queries the database for a user with the matching username, using a SELECT statement.If a matching user is found in the database, the code checks whether the inputted password is correct by comparing it with the hashed password stored in the database. If the password is correct, the user ID associated with that account is retrieved from the database and assigned as an attribute to the MainScreen instance. Then, the application's current screen is changed to the main screen. Finally, the input fields are reset.If no matching user is found in the database or the password is incorrect, an error message is displayed using a dialog box. The input fields are also reset in this case to allow the user to try again.

## Flow diagram for save function
![flow diagram 2 (2)](https://user-images.githubusercontent.com/111819437/225434915-132a21c9-5990-446d-9743-cda07ae56578.png)
The figure 8 is a flowchart for the function save that begins by retrieving the values entered by the user for the date, notes, and overall rating. It then retrieves the user id and the values of checkboxes that indicate the user's progress in different areas (e.g. gym, studying, sleeping, etc.). It calculates the total of the checkboxes to get an total progress score. Next, the function checks to make sure that all the required fields have been filled in by the user. If any of them are missing, an error message is displayed and the function returns without saving the progress data.The function then checks the database to see if progress data has already been added for the current day by the user. If it has, an error message is displayed and the function returns without saving the progress data.If progress data has not already been added for the current day, the function inserts the progress data into the database. Finally, a success message is displayed to the user to indicate that their progress has been saved.





## Test Plan
| Description                                 	| Type                            	| Inputs                                                                             	| Outputs                                                                                                  	|
|---------------------------------------------	|---------------------------------	|------------------------------------------------------------------------------------	|----------------------------------------------------------------------------------------------------------	|
| Test if the program runs without any error  	| Functional: Integration testing 	| Run program                                                                        	| Program runs with 0 exit code                                                                            	|
| Test if registration page works             	| Functional: Integration testing 	| Register, Sabuhi, 2024.sabuhi.abossov@uwcisak.jp, Sabuhi@123, Sabuhi@123, Register 	| It added the information to the database, showed pop up diaolog and bring user to the log in page        	|
| Test if log in page works                   	| Functional: Integration testing 	| Sabuhi, 2024.sabuhi.abossov@uwcisak.jp, Sabuhi@123,Log in                          	| It checked the information on the database, showed pop up diaolog and bring user to the main screen page 	|
| Test if add new day work                    	| Functional: Integration testing 	| Checkboxes, Notes, slider date picker, add new day                                 	| It added the new item to the database                                                                    	|
| Check if table shows the correct data       	| Non-functional: Load testing    	| Log in, Check your progress                                                        	| It shows the correct data inputted by that user                                                          	|



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

# Criteria C: Development
## Existing tools

| Software/Development tools    	| Coding Structure Tools        	| Libraries         	|
|-------------------------------	|-------------------------------	|-------------------	|
| PyCharm professional 2022.3.2 	| OOP Structures (classes)      	| Kivymd.app        	|
| Python                        	| SQL requests                  	| sqlite3           	|
| SQlite                        	| Database                      	| passlib           	|
| KivyMD                        	| Encryption                    	| re                	|
| Github Copilot                	| For loops                     	| database_handler  	|
|                                 	| If-else statements            	| encrypto_password 	|
|                               	| ORM (Object Relation Mapping) 	|                   	|
|                               	| Index                         	|                   	|

## Development
### Success criteria 1: The solution should enable users to track their daily habits, including working out, studying, reading, journaling, water intake and sleeping.
To fullfill this criteria I created a a screen that enables users to track their daily habits, such as working out, studying, reading, journaling, water intake, and sleeping. The screen uses the KivyMD library to create six checkboxes for users to check the habits they achieved. And also a text field for the user to input their daily reflections, a sliders to track how the user is feeling that day and a date picker to select the date.The show_date_picker method displays a date picker dialog when called. The on_save method is called when the user selects a date from the date picker dialog, and it sets the selected date to the date field on the screen.

Each checkbox has an ID assigned to it, and when clicked, the checkbox_click method is called with the checkbox instance, its value, and an index for the habit (0 to 5).The checks list stores the checkbox values (0 or 1) for all the habits, with the int() function to convert the boolean value of the checkbox (self.active) to an integer value (1 or 0). The save method retrieves the date, notes, overall rating, user ID, and habit values from the corresponding fields and checkboxes. It then calculates the total value of habits achieved and validates the date, note, and overall rating fields. If any of these fields are empty, an error message is displayed. If progress for the given date has already been added, another error message is displayed. Otherwise, the progress is inserted into the HABITS table in the database.

In summary, this code creates a screen with checkboxes for tracking daily habits and provides functionality for saving the progress to a database.
```.py
# Create a class for the screen
class add(MDScreen):
    # Initialize list to keep track of checkbox values
    checks = [0, 0, 0, 0, 0, 0]

    # Method to handle checkbox clicks
    def checkbox_click(self, instance, value, habits):
        # Update the value in the checks list based on checkbox clicked
        add.checks[habits] = int(value)

    # Method to save user's progress
    def save(self):
        # Get values entered by user
        day = self.ids.date.text
        note = self.ids.notes.text
        overal = self.ids.overal.text

        # Get user id and checkbox values 
        user_id = self.parent.get_screen('MainScreen').user_id
        gym = add.checks[0]
        study = add.checks[1]
        sleep = add.checks[2]
        read = add.checks[3]
        journal = add.checks[4]
        water = add.checks[5]

        # Calculate the total of the checkboxes
        total = gym + study + sleep + read + journal + water

        # If any of the required fields are missing, display an error dialog and return
        if not day or not note or not overal:
            dialog = MDDialog(title="Error", text="Please enter a valid date, note and overall rating")
            dialog.open()
            return

        # Check if progress for the current day has already been added
        db = database_handler("Project.db")
        query = f"SELECT id FROM HABITS WHERE user='{user_id}' AND date='{day}'"
        result = db.search(query)
        db.close()

        # If progress for the current day has already been added, display an error dialog and return
        if result:
            dialog = MDDialog(title="Error", text="You have already added progress for this date")
            dialog.open()
            return

        # Insert progress data into the database
        query = f"""INSERT INTO HABITS (user, date, gym, studying, sleeping, reading, journaling, water, notes,overal,total)
                    VALUES ('{user_id}', '{day}', '{gym}', '{study}', '{sleep}', '{read}', '{journal}', '{water}', '{note}','{overal}','{total}')"""
        db = database_handler("Project.db")
        db.run_save(query)
        db.close()

        # Display a success dialog
        dialog = MDDialog(title="Success", text="Congrats you updated your progress!")
        dialog.open()

    # Method to display a date picker dialog
    def show_date_picker(self):
        date_dialog = MDDatePicker()
        date_dialog.bind(on_save=self.on_save)
        date_dialog.open()

    # Method to update the selected date in the text field
    def on_save(self, instance, value, date_range):
        self.instance = instance
        self.value = value
        self.date_range = date_range
        self.ids.date.text = str(value)
```
### Success criteria 2:The solution must be designed with security and privacy in mind, with measures to protect the user's data.
To protect users data I created a log in and registration system focusing on security, using the following methods:
-Password hashing: When a user registers, their password is hashed before being stored in the database. This is important because it ensures that even if an attacker gains access to the database, they won't be able to see the user's actual password.
-Regular expression pattern matching: The code includes regular expression pattern matching to ensure that the user enters a valid email address and a strong password that meets specific criteria. This helps to prevent malicious attacks that rely on weak passwords or email spoofing.
-Error handling: The code includes error handling to catch any exceptions that might occur during the login or registration process. This helps to prevent sensitive information from being leaked in error messages.
-Dialogue boxes: The code displays dialogue boxes for certain actions, such as when a user successfully registers or enters an incorrect username or password. This helps to prevent sensitive information from being displayed on the screen.


```.py
# Define the LoginScreen class that inherits from MDScreen
class LoginScreen(MDScreen):

    # Method for trying to login
    def try_login(self):
    # Get the input username and password
    uname = self.ids.uname.text
    passwd = self.ids.passwd.text

    # Connect to the database
    db = database_handler(namedb="Project.db")
    
    # Search for the user in the database
    query = f"SELECT id, password FROM users WHERE username = '{uname}'"
    result = db.search(query)

    # Check if the user exists and the password is correct
    if result and pwd_config.identify(result[0][1]) and check_password(result[0][1], passwd):
        # If the user exists and the password is correct, get the user ID from the database
        user_id = result[0][0]  
        
        # Set the user ID as an attribute of the MainScreen instance
        self.parent.get_screen('MainScreen').user_id = user_id  
        
        # Switch to the MainScreen
        self.parent.current = "MainScreen"
        
        # Reset the input fields
        self.ids.uname.text = ""
        self.ids.passwd.text = ""

    else:
        # If the user does not exist or the password is incorrect, show an error dialog
        dialog = MDDialog(title="Incorrect password or username. Try again")
        dialog.open()
        
        # Reset the input fields
        self.ids.uname.text = ""
        self.ids.passwd.text = ""

```
The LoginScreen class has a method try_login() which is called when the user tries to login. It first retrieves the username and password entered by the user from the input fields. Then it connects to a database named "Project.db" and searches for a user with the given username in the database. If the user is found and the entered password matches with the password stored in the database, it retrieves the user ID from the database and sets it as an attribute of the MainScreen instance. Finally, it switches to the MainScreen and resets the input fields. If the user is not found or the password is incorrect, it shows an error dialog and resets the input fields.
```.py
class RegistrationScreen(MDScreen):
    def try_register(self):
        # Regular expressions for password and email patterns
        pattern = "^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$"
        email_pattern = "r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'"

        # Get the user input for username, email, password and password check
        uname = self.ids.uname_in.text
        email = self.ids.email_in.text
        passwd = self.ids.passwd_in.text
        passwd_check = self.ids.passwd_check.text

        # Check if the user input for username is empty
        if uname == "":
            self.ids.uname_in.hint_text = "Do not forget your username !"

        # Check if the user input for email matches the email pattern
        if not re.match(email_pattern, email):
            # Email is not valid
            self.ids.email_in.hint_text = "Enter a valid email !"

        # Check if the user input for password matches the password pattern
        if re.match(pattern, passwd):
            print("Valid password")
            # Check if the password and the password check fields match
            if passwd != passwd_check:
                # Passwords do not match, set error flags and show hint text
                self.ids.passwd_check.error = True
                self.ids.passwd.error = True
                self.ids.passwd_check.hint_text= "The passwords must match"
            else:  # Passwords match
                # Hash the password and insert user details into the database
                hash = hash_password(passwd)
                db = database_handler(namedb="Project.db")
                query = f"INSERT into users (email,password, username) values('{email}', '{hash}','{uname}')"
                db.run_save(query)
                db.close()
                # Show success dialog and switch to LoginScreen
                print("Registration completed")
                self.parent.current = "LoginScreen"
                dialog = MDDialog(title="Congrats you created your account!")
                dialog.open()
        else:
            # Password does not meet requirements, show error dialog
            dialog = MDDialog(title="Password doesn't meet the requirements",
                              text="The password entered must be:\n- At least 8 characters,\n- One capital letter,\n- One lowercase letter,\n- One symbol: !@#$%^&*()_+")
            dialog.open()
            return
```
The RegistrationScreen class has a method try_register() which is called when the user tries to register a new account. It first checks if the user has entered a valid username, email, password, and password check. Then it checks if the entered password meets certain requirements such as length, one capital letter, one lowercase letter, and one symbol. If the password meets the requirements and the password and password check fields match, it hashes the password and inserts the user details into the database. Finally, it shows a success dialog and switches to the LoginScreen. If the password does not meet the requirements or the passwords do not match, it shows an error dialog.


```.py
class TableScreen(MDScreen):
    # Class variable
    data_table = None

    def on_pre_enter(self, *args):
        # Create a data table with defined properties
        self.data_table = MDDataTable(
            size_hint=(.8, .5),
            pos_hint={"center_x": .5, "center_y": .5},
            use_pagination=False,
            check=True,
            # Define column names and widths
            column_data=[("id", 20),
                         ("USER", 20),
                         ("DATE", 20),
                         ("GYM", 20),
                         ("STUDY", 20),
                         ("SLEEP", 20),
                         ("READ", 20),
                         ("JOURNAL", 20),
                         ("WATER", 20),
                         ("NOTES", 20),
                         ("OVERALL", 20),
                         ("TOTAL", 20),

                         ]
        )

        # Bind row and check press events to their respective functions
        self.data_table.bind(on_row_press=self.row_pressed)
        self.data_table.bind(on_check_press=self.check_pressed)

        # Add the table to the GUI
        self.add_widget(self.data_table)

        # Call the update function to populate the table with data
        self.update()

    # Function to be called when a row is pressed
    def row_pressed(self, table, row):
        print("a row was pressed", row.text)

    # Function to be called when a check mark is pressed
    def check_pressed(self, table, current_row):
        print("a check mark was pressed", current_row)

    # Function to delete checked rows from the table and database
    def delete(self):
        checked_rows = self.data_table.get_row_checks()
        db = database_handler("Project.db")
        for r in checked_rows:
            id = r[0]
            query = f"delete from HABITS where id={id}"
            db.run_save(query)
        db.close()
        self.update()

    # Function to update the data table with habit data for the current user
    def update(self):
        # Get the current user ID from the main screen
        user_id = self.parent.get_screen('MainScreen').user_id

        # Query the database for habit data for the current user
        query = f"SELECT * FROM HABITS WHERE user={user_id}"
        db = database_handler("Project.db")
        data = db.search(query)
        db.close()

        # Update the data table with the retrieved data
        self.data_table.update_row_data(None, data)
        
  ```
The applications also protect user data by querying the database to retrieve only the information that pertains to the specific user who is currently logged in. This is achieved through the update method, where the user's ID is retrieved from the parent screen (MainScreen) and used in a database query to retrieve only rows from the HABITS table that have the matching user value. The retrieved data is then used to update the rows in the MDDataTable instance, ensuring that only the user's relevant data is displayed in the table.
By only displaying the relevant data for each user, the code helps to protect the privacy and security of their data by preventing other users from seeing or accessing their information.


### Success criteria 3: The solution must include a notes session for each day.
I have satisfied the criteria by implementing KivyMD widgets to create a label and a text field. The label prompts the user to input their notes by displaying the text "How was your day?" Additionally, the input is validated to detect cases where the user has not written anything and displays an error dialog accordingly.
```.kv
MDLabel:
                text:"How was your day?"
                font_size: 15
                halign:"center"
                md_bg_color:"#EEE9DA"

            MDTextField:

                id: notes
                text_color: "#050505"
                multiline: True
                size_hint_y: None
                height: dp(150)
                size_hint_x: None
                width: dp(200)
                pos_hint: {"center_x": .5, "center_y": .9}
```

### Success criteria 4: The solution must provide a way for the user to vizualize their progress.
To fulfill this criteria, I have created a screen named "TableScreen" which contains a data table to visualize the progress of the user. The table is implemented using KivyMD's MDDataTable widget. The screen also includes functions to handle events when a row or check mark is pressed. To improve the users experience while using the app,I created a function to delete a row, whena ow is checked , it gets the checked rows using the get_row_checks method of the data table widget and deletes them from the database using an SQL query.

Finally, the update function is used to populate the table with data. It first retrieves the user ID from the main screen and then queries the database for habit data for that user. The data is then updated in the table using the update_row_data method of the data table widge, and only showing the data of that specific user.
KV file:
```.kv
<TableScreen>:
    FitImage:
        source:"inicio.png"

    MDLabel:
        text: "YOUR PROGRESS"
        font_size: 30
        halign: "center"
        pos_hint: {"center_x": .5, "center_y": .8}

    MDRoundFlatIconButton:
        id: delete
        text: "Delete one day"
        md_bg_color:"#c7f0d0"
        on_press:root.delete()
        pos_hint: {"center_x": .8, "center_y": .2}

    MDBoxLayout:
        orientation: "horizontal"
        size_hint: 1,.2

        MDRoundFlatIconButton:
            text: "GO BACK"
            md_bg_color: "#c7f0d0"
            icon: "logout"
            on_press: root.parent.current = "MainScreen"
            text_color: 'FFFFFF'
            pos_hint: {"center_x": .1, "center_y": .15}
```
PY file:
```.py
class TableScreen(MDScreen):
    # Class variable
    data_table = None

    def on_pre_enter(self, *args):
        # Create a data table with defined properties
        self.data_table = MDDataTable(
            size_hint=(.8, .5),
            pos_hint={"center_x": .5, "center_y": .5},
            use_pagination=False,
            check=True,
            # Define column names and widths
            column_data=[("id", 20),
                         ("USER", 20),
                         ("DATE", 20),
                         ("GYM", 20),
                         ("STUDY", 20),
                         ("SLEEP", 20),
                         ("READ", 20),
                         ("JOURNAL", 20),
                         ("WATER", 20),
                         ("NOTES", 20),
                         ("OVERALL", 20),
                         ("TOTAL", 20),

                         ]
        )

        # Bind row and check press events to their respective functions
        self.data_table.bind(on_row_press=self.row_pressed)
        self.data_table.bind(on_check_press=self.check_pressed)

        # Add the table to the GUI
        self.add_widget(self.data_table)

        # Call the update function to populate the table with data
        self.update()

    # Function to be called when a row is pressed
    def row_pressed(self, table, row):
        print("a row was pressed", row.text)

    # Function to be called when a check mark is pressed
    def check_pressed(self, table, current_row):
        print("a check mark was pressed", current_row)

    # Function to delete checked rows from the table and database
    def delete(self):
        checked_rows = self.data_table.get_row_checks()
        db = database_handler("Project.db")
        for r in checked_rows:
            id = r[0]
            query = f"delete from HABITS where id={id}"
            db.run_save(query)
        db.close()
        self.update()

    # Function to update the data table with habit data for the current user
    def update(self):
        # Get the current user ID from the main screen
        user_id = self.parent.get_screen('MainScreen').user_id

        # Query the database for habit data for the current user
        query = f"SELECT * FROM HABITS WHERE user={user_id}"
        db = database_handler("Project.db")
        data = db.search(query)
        db.close()

        # Update the data table with the retrieved data
        self.data_table.update_row_data(None, data)

```
# Criteria D: Functionality
## A 7 min video demonstrating the proposed solution with narration

### Citations
"Why Choose Python." Python.org, Python Software Foundation, https://www.python.org/about/gettingstarted/. Accessed 9 Mar. 2023.

Lucidchart. "Diagram Maker & Visual Solution." Lucidchart, Lucid Software Inc., 2023, https://www.lucidchart.com/. Acessed 9 Mar. 2023 

Free Design Tool: Presentations, Video, Social Media | Canva, https://www.canva.com/. Accessed 9 March 2023.

JetBrains. PyCharm Professional. Version 2023.3.2, JetBrains, 2023. Accessed Mar. 9 2023 

“Building a Simple Application using KivyMD in Python.” GeeksforGeeks, 7 June 2022, https://www.geeksforgeeks.org/building-a-simple-application-using-kivymd-in-python/. Accessed 9 March 2023.

Elder, John. “Creating A Login Screen With KivyMD – Python Kivy GUI Tutorial #44 – KivyCoder.com.” KivyCoder.com, 22 March 2021, https://kivycoder.com/creating-a-login-screen-with-kivymd-python-kivy-gui-tutorial-44/. Accessed 9 March 2023.

“SQL Tutorial.” W3Schools, https://www.w3schools.com/sql/default.asp. Accessed 9 March 2023.

“Text Field — KivyMD documentation.” KivyMD's documentation, https://kivymd.readthedocs.io/en/0.104.1/components/text-field/index.html. Accessed 9 March 2023.
