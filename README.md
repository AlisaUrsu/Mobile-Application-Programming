# Mobile-Application-Programming

This mobile application is designed to make writing and organizing crochet patterns easier and faster for crochet enthusiasts who want a more efficient way to manage their projects.
### Writing patterns
When creating a pattern, users can add a title, specify categories for the project (amigurumi, blanket, scarf, granny square etc.), the estimated time needed for crocheting, a list with the materials needed for the pattern, such as the type of yarn, hooks, and other supplies. Besides adding normal notes on the pattern, the application provides an efficient way for writing the rows needed for the project. By pressing the button "Add rows", a special "keyboard" appears with buttons representing the abbreviations of common stitches like "sc" (single crochet), "dc" (double crochet) and many others, so users can only tap them instead of writing them manually. Based on the inputs, the application will calculate the total number of stitches in real time, ensuring the stitch count is accurate. The application will automatically increment the rows for users after they press an arrow.
### Dashboard
The main screen of the application features a dashboard where users can see all their patterns in one place. Clicking a pattern opens it read-only mode to review it without changing anything or to start working on the project. When clicking a button, users can either edit or delete the pattern. There is also a "Write a new pattern" button on the dashboard that lets users start working on their patterns.

## Domain details
### Pattern
- name: string - the title of the crochet pattern
- materials: text - a list of materials used for the pattern 
- time taken: int - total time spent on the pattern (in minutes)
- steps: text - detailed instructions for the pattern (including rows and additional notes)
- created at: datetime - the date the pattern was created
- updated at: datetime - the date the pattern was last modified
### Category
- name:	string - name of the category 
- description: text	- a brief description of the category 
### Stitches
- abbreviation:	string - abbreviation for the stitch (e.g., "sc", "dc").
- full_name: string -	full name of the stitch 
- description: text	- a description of how to perform the stitch
### Pattern_Categories
A pattern can belong to multiple categories, so a many to many table between Pattern and Categories is needed.
- pattern_id:	int -	foreign key referencing the Pattern table.
- category_id: int - foreign key referencing the Categories table.

Stitches and categories cannot be modified by users.

## Action - CRUD operations
- create: users can add a pattern by writing in a window that works as a note taking application that lets user personalize their patterns. Each row of the pattern will be automatically incrementented and the number of stitches automatically calculated.
- read: users can view a list of all their patterns, search by name or filter by category. When selecting a pattern, they will see the full details (steps, materials, time taken, etc.).
- update: users can edit their existing patterns (e.g., adding more steps or updating the materials list).
- delete: users can delete a pattern if they no longer need it.

### Persistance Details
Every CRUD operation persists on the local database and will be synced with the server when online. The application stores all data in a local database on the device, ensuring users can access their data even when offline.
After creating and saving a pattern, it will be stored in the local database and and synced with the server when online. The patterns are retrieved from the local database and synced with the server when online. The application will automatically save the updated pattern/will delete the pattern to/from the local database and the changes will be synced with server when online.

### Offline Handling
When the application detects that the user is offline, it goes in read-only mode.
- read: users can see the list of patterns and choose to open and read one
- create: users cannot write any patterns while offline, a dialog displaying "You are currently offline. Creating new patterns will be available when you’re back online." will show
- update: users cannot edit any patterns while offline, a dialog displaying "You are currently offline. Editing this pattern will be available when you’re back online." will show
- delete: users cannot delete any patterns while offline, a dialog displaying "You are currently offline. Deleting this pattern will be available when you’re back online." will show

## Application Mock
![Frame 278 (1)](https://github.com/user-attachments/assets/c315e55d-41ce-4d49-8486-4d655e898481)
![Frame 279](https://github.com/user-attachments/assets/c45d91b1-6510-40e7-a220-a5e8359d212a)

