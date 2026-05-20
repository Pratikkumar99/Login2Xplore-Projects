# Student Enrollment System

A comprehensive Student Enrollment System built using the Login2Xplore API for storing and managing student records with full CRUD operations.

## Overview

This project demonstrates how to create a complete student enrollment system that interacts with the Login2Xplore cloud database API. The application allows users to add, view, and update student records with roll numbers, personal details, and enrollment information.

## Features

- **Add Student Records**: Create new student entries with unique Roll No, Full Name, Class, Birth Date, Address, and Enrollment Date
- **Auto-fetch Student Data**: Automatically retrieves existing student data when Roll No is entered
- **Update Student Records**: Modify existing student information
- **Form Validation**: Ensures all required fields are filled before submission
- **Smart Form Control**: Automatically enables/disables fields based on student existence
- **API Integration**: Uses Login2Xplore API with both IML (PUT/UPDATE) and IRL (GET) endpoints
- **Responsive Design**: Built with Bootstrap 3 for mobile-friendly interface
- **Real-time Feedback**: Alert messages for validation and operation status

## Technology Stack

- **HTML5**: Structure and layout
- **Bootstrap 3.4.1**: CSS framework for responsive design
- **jQuery 3.5.1**: JavaScript library for DOM manipulation and AJAX calls
- **JPDB Commons 0.0.3**: Login2Xplore JavaScript library for API interactions
- **Login2Xplore API**: Cloud database service for data persistence

## Project Structure

```
Micro Project Work/
├── index.html          # Main application file with form and JavaScript logic
└── README.md           # Project documentation
```

## Setup Instructions

1. **Clone or Download**: Obtain the project files
2. **Open in Browser**: Simply open `index.html` in a web browser
3. **No Build Process Required**: This is a static HTML application

## Usage

### Adding a New Student

1. Enter a unique **Roll No** in the first field
2. If the Roll No doesn't exist, the form fields will automatically enable
3. Enter the **Full Name**
4. Enter the **Class**
5. Select the **Birth Date**
6. Enter the **Address**
7. Select the **Enrollment Date**
8. Click the **Save** button
9. The data will be sent to the Login2Xplore API for storage

### Updating an Existing Student

1. Enter an existing **Roll No** in the first field
2. The system will automatically fetch and populate the student's data
3. Modify the desired fields
4. Click the **Update** button
5. The updated data will be sent to the Login2Xplore API

### Resetting the Form

Click the **Reset** button to clear all fields and return to the initial state.

### Form Validation

The application validates that:
- Roll No is not empty
- Full Name is not empty
- Class is not empty
- Birth Date is not empty
- Address is not empty
- Enrollment Date is not empty

If any field is empty, an alert will prompt the user to fill the required field.

## API Configuration

The application uses the following Login2Xplore API configuration:

- **Base URL**: `http://api.login2explore.com:5577`
- **IML Endpoint**: `/api/iml` (for PUT and UPDATE operations)
- **IRL Endpoint**: `/api/irl` (for GET operations)
- **Database Name**: `SCHOOL-DB`
- **Relation Name**: `STUDENT-TABLE`
- **Authentication Token**: Configured in the code (replace with your own token)

### API Request Formats

#### PUT Request (Save New Student)

```json
{
  "token": "YOUR_TOKEN",
  "dbName": "SCHOOL-DB",
  "cmd": "PUT",
  "rel": "STUDENT-TABLE",
  "jsonStr": {
    "rollNo": "roll_number",
    "fullName": "student_name",
    "studentClass": "class",
    "birthDate": "birth_date",
    "address": "address",
    "enrollmentDate": "enrollment_date"
  }
}
```

#### UPDATE Request (Update Existing Student)

```json
{
  "token": "YOUR_TOKEN",
  "dbName": "SCHOOL-DB",
  "cmd": "UPDATE",
  "rel": "STUDENT-TABLE",
  "jsonStr": {
    "rollNo": "roll_number",
    "fullName": "student_name",
    "studentClass": "class",
    "birthDate": "birth_date",
    "address": "address",
    "enrollmentDate": "enrollment_date"
  },
  "record": "roll_number"
}
```

#### GET Request (Fetch Student by Roll No)

```json
{
  "token": "YOUR_TOKEN",
  "dbName": "SCHOOL-DB",
  "cmd": "GET_BY_KEY",
  "rel": "STUDENT-TABLE",
  "jsonStr": {
    "rollNo": "roll_number"
  }
}
```

## Customization

### Updating API Token

To use your own Login2Xplore token, modify line 40 in `index.html`:

```javascript
var connToken = "YOUR_TOKEN_HERE";
```

### Changing Database/Relation Names

Modify the database and relation names at the top of the script:

```javascript
var dbName = "YOUR_DB_NAME";
var relName = "YOUR_RELATION_NAME";
```

## Key Functions

- **resetForm()**: Clears all form fields and disables input fields except Roll No
- **enableFields()**: Enables all form fields for data entry
- **validateData()**: Validates all form inputs and returns JSON string
- **getStudent()**: Fetches existing student data by Roll No using IRL endpoint
- **saveData()**: Creates new student record using PUT request via IML endpoint
- **updateData()**: Updates existing student record using UPDATE request via IML endpoint

## Form Behavior

### Initial State
- Only Roll No field is enabled
- All other fields are disabled
- Save, Update, and Reset buttons are disabled

### New Student Mode (Roll No doesn't exist)
- All fields become enabled
- Save button becomes enabled
- Update button remains disabled

### Existing Student Mode (Roll No exists)
- All fields become enabled and populate with existing data
- Roll No field becomes disabled
- Update button becomes enabled
- Save button remains disabled

## Browser Compatibility

- Chrome (recommended)
- Firefox
- Edge
- Safari

## Requirements

- Modern web browser with JavaScript enabled
- Internet connection (for API calls)
- Valid Login2Xplore API token
- JPDB Commons library (loaded from CDN)

## Future Enhancements

Potential improvements for this project:
- Delete student records functionality
- Search and filter students
- Display all students in a table view
- Export student data to CSV/PDF
- Better UI/UX with modern frameworks (React, Vue)
- Input validation for specific formats (email, phone)
- Loading indicators during API calls
- Pagination for large datasets
- Student photo upload functionality

## Contact

For questions or issues related to the Login2Xplore API, refer to the official Login2Xplore documentation.
