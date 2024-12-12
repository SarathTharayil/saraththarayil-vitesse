---
title: Blog Title
description: Your blog description, which is long text, can be an introduction to the post or a paragraph of the post.
image:
    src: "../public/View1.png"
    alt: "Image"
date: 2024-05-01
---
## Introduction

In the modern job market, keeping track of multiple applications can quickly become overwhelming. As a solution, I developed a **Job Applications Tracker** using **Streamlit**, a Python-based framework for creating interactive web applications. This app helps users organize their job application details efficiently, with features like **adding, editing, and deleting applications**, as well as **backup and restore options**. The app can export data to **CSV**, **JSON**, and **JSX formats**, making it highly versatile for integration with personal websites or dashboards.

In this blog, I'll walk you through the key functionalities of the app, its design considerations, and how it achieves seamless data management. By the end, you’ll have a comprehensive understanding of how this app works and how you can customize it for your needs.

The tracker feeds the a blog page to show the current working of the streamlit app. See this <a href="/blog/job-applications" title="blog">blog</a>. The app is deployed <a href="https://jobtracker.streamlit.app/" target= "_blank" title="blog">here</a>.

---

## Core Functionalities

The **Job Applications Tracker** revolves around a user-friendly interface with several key features:

1. **Add New Job Application**: Users can input details such as company, designation, application status, job type, application date, salary range, contract type, and application links.
2. **Edit Existing Application**: Modify any field of an existing job application.
3. **Delete Applications**: Remove outdated or irrelevant entries.
4. **Backup and Restore**: Save a backup of the data and restore it when needed.
5. **Export to Multiple Formats**: Save data in CSV, JSON, and JSX formats for further use or integration.
6. **Dynamic UI Updates**: Real-time data refreshes ensure an updated display of all applications without requiring manual reloads.

---

## Implementation Highlights

### File and Data Management

The app uses **pandas** for data manipulation and **shutil** for file handling. Three file formats—CSV, JSON, and JSX—serve different purposes:
- **CSV**: Default storage for job applications, providing a straightforward way to view and manipulate the data.
- **JSON**: Ensures compatibility with web-based systems and APIs.
- **JSX**: Generates a React-compatible file for direct integration with web applications.

To ensure reliability, the app creates a backup file (`job_applications_backup.csv`) and allows users to restore the main data file if needed.

---

### Adding Applications

The **Add New Job Application** form is located in the sidebar. It captures all essential details such as:
- **Company Name**
- **Designation**
- **Application Status** (e.g., "In Progress," "Rejected")
- **Job Type** (e.g., "Remote," "In-Office")
- **Date of Application**
- **Salary Range**
- **Contract Type**
- **Closing Date**

The app validates inputs to ensure:
1. No duplicate entries for the same company-designation pair.
2. Mandatory fields like **Company** and **Designation** are provided.

Upon submission, the new application is appended to the existing data and saved across all formats.

---

### Editing and Deleting Applications

A **dropdown menu** on the main page allows users to select an application based on its **company and designation**. Once selected, users can:
- Modify any field in a form.
- Delete the application entirely if it's no longer relevant.

These actions dynamically update the data stored in CSV, JSON, and JSX formats, ensuring consistency.

---

### JSX Integration

The JSX export functionality generates a React-compatible file containing all job applications as an array of objects. This feature is particularly useful for developers who wish to integrate the tracker with their websites. The JSX file is stored in a customizable directory, and its last modification time is displayed on the app's main page for transparency.

---

### Backup and Restore

Data reliability is critical. The app allows users to:
- **Backup Data**: Save the current CSV file to a separate backup location.
- **Restore Data**: Recover the main file using the backup if accidental deletion or corruption occurs.

These operations are seamless, ensuring users never lose their data.

---

## Technical Overview

### App Layout

The app uses a **wide layout** to make the most of the screen space, with a sidebar for adding applications and a main page for data display and actions.

#### Sidebar
The sidebar includes:
- **Add New Application Form**: Form fields with dropdowns and text inputs.
- **Submit Button**: Adds a validated application to the data file.

#### Main Page
The main page displays:
- **Job Applications Table**: A pandas DataFrame rendered with column names in title case.
- **Action Buttons**: Includes options to **Refresh**, **Clear**, **Restore**, **Backup**, and **Export to JSX**.

### Key Functions

1. **`save_data(df)`**: Saves the DataFrame to all three formats—CSV, JSON, and JSX—ensuring all formats stay synchronized.
2. **`generate_jsx_file(job_data)`**: Converts job applications to a JavaScript array for use in React applications. Each application object is formatted with key-value pairs.
3. **`clear_csv()`**: Empties the CSV file while retaining the column structure, providing a clean slate for new entries.
4. **`restore_csv_from_backup()`**: Copies the backup file to the original location without deleting the backup, ensuring data recovery.

---

## Code Snippet: JSX Export Example

The following snippet illustrates how job application data is converted into JSX format:

```javascript
export const jobApplications = [
  {
    company: 'OpenAI',
    designation: 'Data Scientist',
    status: 'In Progress',
    type: 'Remote',
    dateApplied: '2024-12-01',
    link: 'https://openai.com/careers',
    salary: '100,000+',
    contract: 'Permanent',
    closingDate: '2024-12-15',
  },
  {
    company: 'Google',
    designation: 'Machine Learning Engineer',
    status: 'Interview',
    type: 'Hybrid',
    dateApplied: '2024-11-20',
    link: 'https://google.com/careers',
    salary: '120,000+',
    contract: 'Permanent',
    closingDate: '2024-12-10',
  },
]
```
---

## Challenges and Solutions

### Real-Time Updates
- **Challenge**: Keeping the data table updated without manual page refreshes.
- **Solution**: Leveraged `st.experimental_set_query_params` to trigger updates dynamically.

### Data Consistency
- **Challenge**: Synchronizing changes across CSV, JSON, and JSX formats.
- **Solution**: Centralized the save logic in the `save_data()` function to ensure all formats are updated simultaneously.

### Handling Duplicate Entries
- **Challenge**: Preventing duplicate company-designation pairs.
- **Solution**: Added validation in the **Add Application Form** to check for existing entries before submission.

---

## Future Improvements

- **Advanced Filtering**: Allow users to filter applications based on fields like salary, status, or contract type.
- **Analytics Dashboard**: Provide insights such as the number of applications by status or average time taken for responses.
- **Mobile Responsiveness**: Optimize the app layout for better usability on mobile devices.
- **Multi-User Support**: Enable secure logins for multiple users to track their applications separately.

---

## Conclusion

The **Job Applications Tracker** is a powerful tool for job seekers, streamlining the process of tracking and managing applications. Its robust features, intuitive interface, and seamless data management make it an excellent choice for anyone navigating the job market. By integrating tools like pandas, Streamlit, and React, this app bridges the gap between technical functionality and user experience.

Feel free to explore the code, adapt it to your needs, or use it as inspiration for your projects. **Happy coding!**
