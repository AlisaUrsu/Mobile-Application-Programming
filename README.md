# Mobile-Application-Programming

This mobile application is designed to make writing and organizing crochet patterns easier and faster for crochet enthusiasts who want a more efficient way to manage their projects.
### Writing patterns
When creating a pattern, users can add a title, specify categories for the project (amigurumi, blanket, scarf, granny square etc.), the estimated time needed for crocheting and add a list with the materials needed for the pattern, such as the type of yarn, hooks, and other supplies. Besides adding normal notes on the pattern, the application provides an efficient way for writing the rows needed for the project. By pressing the button "Add rows", a special "keyboard" appears with buttons representing the abbreviations of common stitches like "sc" (single crochet), "dc" (double crochet) and many others, so users can only tap them instead of writing them manually. Based on the inputs, the application will calculate the total number of stitches in real time, ensuring the stitch count is accurate. The application will automatically increment the rows for users after they press an arrow.
### Dashboard
The main screen of the application features a dashboard where users can see all their patterns in one place. Clicking a pattern opens it read-only mode to review it without changing anything or to start working on the project. When clicking a button, users can either edit or delete the pattern. There is also a "Write a new pattern" button on the dashboard that lets users start working on their patterns.

## Domain details
### Pattern
- name: string - the title of the crochet pattern
- materials: text - a list of materials used for the pattern 
- time taken: int - total time spent on the pattern (in minutes)
- steps: text - detailed instructions for the pattern (including rows and additional notes).
- created at: datetime - the date the pattern was created
- updated at: datetime the date the pattern was last modified
### Category
- name:	string	- name of the category 
- description: text	- a brief description of the category 
### Stitches
- abbreviation:	string - abbreviation for the stitch (e.g., "sc", "dc").
- full_name: string -	full name of the stitch 
- description: text	- a description of how to perform the stitch
### Pattern_Categories
A pattern can have 
- pattern_id:	int -	foreign key referencing the Pattern table.
- category_id: int - foreign key referencing the Categories table.
Stitches and categories cannot be modified by users.

## Action - CRUD operations
1. Create
Pattern Creation: Users can write a new pattern by entering the pattern name, category, materials, time taken, and detailed steps.
Each step of the pattern will automatically increment the round number for clarity.
After saving, the pattern will be stored in the local database (and synced with the server when online).
2. Read
Pattern Reading:

Users can view a list of all their patterns, search by name or filter by category.
When selecting a pattern, they will see the full details (steps, materials, time taken, etc.).
The patterns are retrieved from the local database and synced with the server when online.
Update
Pattern Update:

Users can edit their existing patterns (e.g., adding more steps or updating the materials list).
The app will automatically save the updated pattern to the local database, syncing changes to the server when online.
Delete
Pattern Deletion:

Users can delete a pattern if they no longer need it.
The pattern will be removed from the local database and the server.
