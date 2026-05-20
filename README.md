# Login2Xplore DEMO Project

A simple demo project built using the Login2Xplore API for storing and managing employee records.

## Overview

This project demonstrates how to create a basic employee management system that interacts with the Login2Xplore cloud database API. The application allows users to add employee records with unique IDs, names, and email addresses.

## Features

- **Add Employee Records**: Create new employee entries with unique Employee ID, Name, and Email
- **Form Validation**: Ensures all required fields are filled before submission
- **API Integration**: Uses Login2Xplore API for data storage and retrieval
- **Responsive Design**: Built with Bootstrap 3 for mobile-friendly interface
- **Real-time Feedback**: Alert messages for validation and operation status

## Technology Stack

- **HTML5**: Structure and layout
- **Bootstrap 3.4.1**: CSS framework for responsive design
- **jQuery 3.5.1**: JavaScript library for DOM manipulation and AJAX calls
- **Login2Xplore API**: Cloud database service for data persistence

## Project Structure

```
login2explore Project/
├── index.html          # Main application file with form and JavaScript logic
```

## Setup Instructions

1. **Clone or Download**: Obtain the project files
2. **Open in Browser**: Simply open `index.html` in a web browser
3. **No Build Process Required**: This is a static HTML application

## Usage

### Adding an Employee

1. Enter a unique **Employee ID** in the first field
2. Enter the **Employee Name**
3. Enter the **Employee Email**
4. Click the **Save** button
5. The data will be sent to the Login2Xplore API for storage

### Form Validation

The application validates that:
- Employee ID is not empty
- Employee Name is not empty
- Employee Email is not empty

If any field is empty, an alert will prompt the user to fill the required field.

## API Configuration

The application uses the following Login2Xplore API configuration:

- **Base URL**: `http://api.login2explore.com:5577`
- **API Endpoint**: `/api/iml`
- **Database Name**: `SAMPLE`
- **Relation Name**: `EMP-REL`
- **Authentication Token**: Configured in the code (replace with your own token)

### API Request Format

The application creates PUT requests in the following JSON format:

```json
{
  "token": "YOUR_TOKEN",
  "dbName": "SAMPLE",
  "cmd": "PUT",
  "rel": "EMP-REL",
  "jsonStr": {
    "empId": "employee_id",
    "empName": "employee_name",
    "empEmail": "employee_email"
  }
}
```

## Customization

### Updating API Token

To use your own Login2Xplore token, modify line 113 in `index.html`:

```javascript
var putReqStr = createPUTRequest("YOUR_TOKEN_HERE",
    jsonStr, "SAMPLE", "EMP-REL");
```

### Changing Database/Relation Names

Modify the database and relation names in the `saveEmployee()` function:

```javascript
var putReqStr = createPUTRequest("YOUR_TOKEN",
    jsonStr, "YOUR_DB_NAME", "YOUR_RELATION_NAME");
```

## Key Functions

- **validateAndGetFormData()**: Validates form inputs and returns JSON string
- **createPUTRequest()**: Constructs the API request payload
- **executeCommand()**: Executes the API call using AJAX
- **resetForm()**: Clears the form fields after successful submission
- **saveEmployee()**: Main function that orchestrates the save process

## Browser Compatibility

- Chrome (recommended)
- Firefox
- Edge
- Safari

## Requirements

- Modern web browser with JavaScript enabled
- Internet connection (for API calls)
- Valid Login2Xplore API token

## Future Enhancements

Potential improvements for this project:
- Update and Delete employee records
- Search functionality
- Display all employees in a table
- Better UI/UX with modern frameworks
- Input validation for email format
- Loading indicators during API calls

This project is provided as-is for educational purposes.

## Contact

For questions or issues related to the Login2Xplore API, refer to the official Login2Xplore documentation.
