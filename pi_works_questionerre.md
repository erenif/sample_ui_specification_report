# User Interface Specification Document for User Management Screen

## 1. Introduction

This user interface is designed for administrators to manage users within the system. It will include a table to show already registered users, several inputs and buttons to add new users.

## 2. Requirements

### 2.1 - Functional Requirements

* Display the user information in a table that includes rows user ID, user name, user email and enabled.
* Enable user to filter and sort according to the criteria selected on each column.
* Enable user to add new user to the system.
* Enable user to edit the existing user in the system.
* Allow user to display only enabled user profiles on the table.

### 2.2 - Nonfunctional Requirements

* The table should be constructed with the data retrieved from database.
* New user data should be sent to the database.
* The table should be reconstructed with the initial state of the database when new user have registered.
* The new user input should be filled and role should be selected to add a new user.

## 3. User Interface Overview

* There are 2 main parts of the user interface which are user information table and new user form. Considering that, the interface has seperated into 2 parts, vertically.
* The user information table with 4 columns has placed on the left of the interface which will also include filter and sort buttons for each column.
* The new user form include 4 input fields, 1 dropdown menu and 1 checkbox. It has placed on the right of the interface.
* An extra area has also added on the top of the interface which include new user, save user buttons and hide disabled user checkbox. New user button and hide disabled user checkbox have placed on left of the top area and the save user button have placed on right of the top area.

## 4. Components

### 4.1 - User List

__Columns:__

* **_ID:_** A unique identification number for each user.
* **_User Name:_** The determined user name for the user.
* **_Email:_** The email that designated to the user.
* **_Enabled:_** A boolean indicator that shows the user profile has activated or not.

__Buttons:__

* **_Filter Buttons:_** Enables to filter user data in each column according to a criteria which have determined via a pop-up menu when the button have clicked.
* **_Sort Buttons:_** Allows sorting the user data in each column numerically for the ID column, alphabetically for the Username and Email columns, and by logical values for the Enabled column.
* **_Hide Disabled Users Checkbox:_** The “Hide Disabled Users” checkbox allows displaying only the users with “true” value on the Enabled column.

### 4.2 - New User Form

__Input Fields:__
* **_User Name:_** Text input for user name.
* **_Display Name:_** Text input for the name displayed when each user logged in.
* **_Phone:_** Numeric input for the phone number of the user.
* **_User Roles:_** A dropdown which has 3 options which are guest, admin and superadmin.
* **_Enabled:_** A checkbox that returns true to "Enabled" field when its clicked and returns false, otherwise.

__Buttons:__

* **_Save User Button:_** Saves the new user information into the database.
* **_New User Button:_** Clears the new user input fields.

## 5. Behavior Analysis

### 5.1 - Initial State

The interface will start to work with following actions, when it's just started.

1. The user information table will be constructed with the existing user information on the database.
2. The table should be unsorted and unfiltered in initial state.
3. The new user form fields will start empty.
4. The user roles dropdown menu should initially display “Select user roles…” as the default option.
5. Hide disabled user and enabled checkboxes should be unchecked initial state.

### 5.2  - Adding New User

The interface will respond to user with following actions, when the user tries to add new user into the system.

1. If all the inputs have filled properly and the save user button has pressed, the new user data will be sent to the database and the user information table will be updated accordingly.
2. If the input fields haven't filled properly and the save user button pressed, the following actions will be taken according to the mistake have been made.
    1. All input fields on new user form should be filled, otherwise the interface will return a pop up error box which warns about incomplete fields.
    2. The display name should only include letters and space between letters. If interface faces with a character in another data type, it will return a pop up error to the user.
    3. Phone number should be written with 10 digit format without country prefix. If interface faces with non-numeric characters or non-valid input according to the used format, the interface will return a pop-up error message which warns about the entered phone number is not valid.
3. The new user form will be cleared and return to its initial state, as it appeared when the interface first loaded, when the new user button is pressed.

### 5.3 - Filtering And Sorting on User Information Table

__Filtering:__ 

Filtering process can be made according to criterias can be selected for each column.

* **_ID Column:_** Filtering on ID column can be made with providing a valid range of numbers. When the filter button on ID column have pressed, a pop up box occurs.It includes 2 fields for the range input, 1 apply button and a text that asks for a valid ID number range. If user enters a valid range and presses apply button, only the users that has ID numbers in provided range, will be listed. If the user enters a range of numbers that is not valid and presses on apply button, the interface will return a pop up error that indicates a non-valid ID number range.

* **_User Name and Email Columns:_** Filtering on user name and email columns can be made with providing a valid prefix that will be searched for all data. When the filter button pressed on each column, a pop up box will occur. The pop up box will include an input field for prefix that will be searched, an apply button and a text that asks for a prefix to filter. When a prefix has entered on the input field on pop up and the apply button has pressed, the user data that has the provided prefix will be listed. If there is no user that have data which does not start with provided prefix, then empty list will be returned.

* **_Enabled Column:_** Filtering on enabled column can be made with selecting a boolean value. When the filter button ob Enabled column have pressed, a pop up occurs. The pop up includes a dropdown menu which has true and false boolean values as options, an apply button and a text that asks for the boolean value to filter the data. After a boolean value have selected and the apply button have pressed, the user data with the provided boolean value on enabled column will be listed. If there is no user that have the selected boolean value on enabled column, then empty list will be returned.

The filtering operation can be turned off with pressing the filter button for each column, cleaning the entered or selected fields on occuring pop-up box and pressing apply button on pop-up box.

__Sorting:__

Sorting operation can be made according to the only one column data. When the sort button pressed on a column, the list will be sorted accoring to the data on that column. 

After that if the sort button pressed on the same column, the list will be sorted on inverse order according to the data on same column.

If the sort button pressed on different column, the list will be sorted according to only the data on that column and the operation will go like this.

The user data can be sorted by each column with their criterias.

* **_ID Column:_** The data is sorted according to the numeric values of ID numbers on ID column. If the sort button on ID column clicked for once, the user data will be sorted with increasing ordered ID numbers. If the button clicked twice without click on different sort button, the user data will be sorted with decreasing ordered ID numbers.

* **_User Name and Email Column:_** The data is sorted alphabetically for the Username and Email columns. For both columns, if the sort button is clicked once, the user data will be sorted alphabetically based on the data in the corresponding column. If the same sort button is clicked again without clicking with other columns’ sort buttons, the user data will be sorted in reverse alphabetical order based on the data in that column. This operation functions same for both the Username and Email columns since both contain string data.

* **_Enabled Column:_** The data is sorted based on the boolean values in the Enabled column of the user data. If the sort button for the Enabled column is clicked once, the user data will be sorted with users having a “true” value appearing first, followed by users with a “false” value. If the same sort button is clicked again without clicking any other sort buttons, the user data will be sorted in reverse order, with users having a “false” value appearing first and users with a “true” value coming after.

