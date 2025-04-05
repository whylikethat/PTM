
# Personal Task Manager

This application is a task management system built using C# and integrates with Google Sheets for storing and retrieving tasks. The app supports task creation, task viewing, task editing, and task deletion, while also sending email notifications when tasks are deleted.

## Features:
- View, add, edit, and delete tasks.
- Integrates with Google Sheets to store task information.
- Sends email notifications when a task is deleted.

## Dependencies:

The following dependencies are required to run the application:

- **.NET Framework**: Ensure you have .NET SDK installed (Version: 9.0 or later).
- **Google API Client**: The app uses Google Sheets API to interact with Google Sheets. You will need to set up Google Sheets API and use the required credentials.
- **SMTP Server**: The app uses an SMTP server to send email notifications when tasks are deleted.

## Setup Instructions:

### 1. Clone the Repository:

To clone this repository to your local machine, run the following command:

```bash
git clone https://github.com/yourusername/yourrepository.git
```

### 2. Configure Google Sheets Credentials:

To access and interact with Google Sheets, you need to create a project in Google Cloud, enable the Sheets API, and set up a service account.

#### Steps:
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (or select an existing one).
3. Enable the **Google Sheets API**.
4. Create **Service Account Credentials** for the application (a JSON file).
5. Download the JSON file containing your credentials.
6. Place this file in the **Credentials** folder in the project directory.

In your code, replace the path to your credentials file in the following line:

```csharp
private static string CredentialPath = "Credentials/personal-task-manager-455322-b0b9d85b4021.json"; // Adjust the path
```

#### Modify Google Sheet ID and Sheet Name:

In the `viewTask` form, and anywhere else you need to access the sheet, change the **Spreadsheet ID** and **Sheet Name** to match your Google Sheet:

```csharp
private static string SpreadsheetId = "YOUR_GOOGLE_SHEET_ID"; // Replace with your Google Sheet ID
private static string SheetName = "Tasks"; // Replace with the actual sheet name
```

You can find the **Spreadsheet ID** in the Google Sheets URL: 
```
https://docs.google.com/spreadsheets/d/YOUR_GOOGLE_SHEET_ID/edit
```

### 3. Configure SMTP Information:

The application sends email notifications when a task is deleted. You need to configure the **SMTP Server** settings in the following section of the code:

```csharp
SmtpClient smtp = new SmtpClient("smtp.yourmailprovider.com"); // Replace with your SMTP provider
smtp.Port = 587;
smtp.Credentials = new NetworkCredential("your-email@example.com", "your-email-password");
smtp.EnableSsl = true;
```

Make sure you replace the following placeholders:
- `smtp.yourmailprovider.com` with your SMTP server address.
- `your-email@example.com` with your email address.
- `your-email-password` with your email account password.

### 4. Build and Run the Application:

Once the Google Sheets API and SMTP information have been configured, you can build and run the application.

#### Steps:
1. Open the project in Visual Studio.
2. Press **Ctrl + Shift + B** to build the project.
3. Press **F5** to run the application.

## How the Application Works:

### 1. Add Task:

To add a task:
- Enter the task's name, priority, description, and contact email.
- Press the "Add" button, which will create a new task in the Google Sheet and the application’s grid.

### 2. View Task:

The "View Task" form will show all tasks in the Google Sheet in a table. It displays the task name, priority, description, and contact email. Each row also includes "Edit" and "Delete" buttons.

### 3. Edit Task:

To edit a task:
- Click the "Edit" button on the respective row.
- A form will appear with the current task data, where you can make modifications.
- Once changes are made, the task data is updated in both the grid and the Google Sheet.

### 4. Delete Task:

To delete a task:
- Click the "Delete" button on the respective row.
- A confirmation message will appear.
- If confirmed, the task will be removed from both the grid and the Google Sheet.
- An email notification will be sent to the task’s contact email with a subject of "Task Name" and the body containing the description of the task.
