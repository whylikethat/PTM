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

### 2. Configure Google Sheets Credentials:
To access and interact with Google Sheets, you need to create a project in Google Cloud, enable the Sheets API, and set up a service account.

Steps:
Go to the Google Cloud Console.

Create a new project (or select an existing one).

Enable the Google Sheets API.

Create Service Account Credentials for the application (a JSON file).

Download the JSON file containing your credentials.

Place this file in the Credentials folder in the project directory.

In your code, replace the path to your credentials file in the following line:
