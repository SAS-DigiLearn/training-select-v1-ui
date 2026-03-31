# SAS Role Specific Learning Dashboard

Overview

This project is a role-based learning dashboard designed to help users quickly find the training content relevant to their job role.

The interface works in a similar way to a Virtual Learning Environment (VLE) by guiding users through a simple selection process:

Choose a Department
Choose an Area
Choose a Role
View the learning sites or modules assigned to that role
Track progress by marking items as Completed
Save a favourite role for quick access next time

The goal of the project is to make learning content easier to find and manage by presenting it in a clear, structured, and user-friendly way.

What the dashboard does

The dashboard:

Displays learning content specific to a selected role
Uses structured data files to control what content appears
Allows users to track completion progress
Saves user selections locally in the browser
Provides quick access to frequently used roles
Opens learning links directly in a new tab

No logins or databases are required – everything is stored locally on the user's device.

How the system is structured

The dashboard is built using three main parts:

1. HTML (Structure)

Defines what appears on the page:

Page header with title and logo
Dropdown menus for selecting role information
Buttons for saving and viewing favourite roles
Cards displaying learning content
Completion toggle switches

This forms the visible layout of the dashboard.

2. CSS (Styling)

Controls how the dashboard looks:

Clean card layout similar to modern VLE platforms
Colour coding for different content types
Rounded buttons and panels
Responsive layout that adapts to screen size
Toggle switch styling for completion tracking

The colour scheme highlights key actions and keeps the interface consistent.

3. JavaScript (Functionality)

Controls how the dashboard behaves:

Loads data files
Filters content based on user selections
Saves user progress
Dynamically updates the page without reloading

This is what makes the page interactive.

Data files used by the dashboard

The system uses three CSV files (simple spreadsheet-style files):

courses.csv

Contains the learning content.

Each row represents either:

an eLearning module
a learning site containing multiple modules

Example fields:

course_id – unique identifier
site – display name of the content
url – link to the training
category – whether it is a single module or full site
roles.csv

Defines the organisational structure.

Each role is linked to:

department
area
role name
role ID

This allows the dropdown filters to work in sequence.

role_course_map.csv

Connects roles to learning content.

Each row states:

which course belongs to which role

This allows the dashboard to show only relevant learning items.

How the page loads information

When the page opens:

The system loads all three CSV files
The Department dropdown is populated
If the user has visited before, their previous selections are restored
Saved roles are displayed if one exists

This happens automatically without user input.

Role selection process

The dropdown menus follow a structured order:

Step 1 – Department selection

The user chooses a department.

The system then filters available areas related to that department.

Step 2 – Area selection

The user chooses an area within the department.

The system then filters the available roles related to that area.

Step 3 – Role selection

The user selects their role.

The system then:

Finds all courses mapped to that role
Generates learning cards
Displays launch buttons
Displays completion tracking toggles
Learning cards

Each learning item appears as a card containing:

Title

Name of the learning content

Content type label

Indicates whether the item is:

Individual Module
Site (Multiple Modules)
Launch button

Opens the learning content in a new browser tab.

Completion toggle

Allows the user to track progress.

Switching the toggle:

changes status between "Outstanding" and "Completed"
saves progress automatically
Saving progress

The dashboard uses browser local storage.

This means:

progress is saved automatically
no login is required
selections remain after refreshing the page
progress is specific to the device and browser used

Example saved items:

selected department
selected area
selected role
completion status for each learning item
favourite role
Favourite role feature

Users can save one role as a favourite.

Benefits:

quickly return to the most commonly used role
avoids repeated navigation through dropdowns
can be changed or removed at any time

Buttons included:

Save Role

Stores the currently selected role

View Saved Role

Automatically loads the saved role and its learning content

Change Role

Clears selections and allows a new role to be chosen

How completion tracking works

Each learning item includes a toggle switch.

States:

Outstanding – learning not yet completed
Completed – learning marked as done

The system stores the completion state using a unique combination of:

role ID + course ID

This ensures progress is tracked correctly even if multiple roles share similar content.

Visual design approach

The layout is designed to feel familiar to users of learning platforms.

Key design choices:

card-based layout improves readability
consistent button styling improves usability
colour highlights key actions
spacing improves accessibility
simple typography improves clarity
Benefits of this approach
For users
simple navigation
clear overview of required learning
ability to track progress
reduced time searching for content
For administrators
easy to update content via CSV files
no need to modify code when adding new courses
scalable structure for new roles or departments
lightweight and easy to host
File structure overview

Typical project folder:

index.html
logo.png

courses.csv
roles.csv
role_course_map.csv
