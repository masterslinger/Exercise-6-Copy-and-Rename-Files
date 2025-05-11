# Exercise-6-Copy-and-Rename-Files
~~~
Name : W Allen Johnston Ozario  
Reg.No : 21222411004  
~~~
🎯 Aim
To create a UiPath workflow that copies all files from a source folder to a destination folder and renames them by appending a timestamp to each file name.

🧰 Materials Required
UiPath Studio (Community or Enterprise Edition)

Windows OS

Two folders on your system:

Source Folder (e.g., C:\Users\YourName\Documents\SourceFiles)

Destination Folder (e.g., C:\Users\YourName\Documents\RenamedFiles)

Basic understanding of file operations and string manipulation

🛠 Procedure
✅ Step 1: Create a New Process
Open UiPath Studio and create a new process named CopyRenameFiles.

✅ Step 2: Create Input Variables
Create the following variables in the Variables panel:

Name	Type	Default Value (optional)
sourceFolder	String	"C:\Users\YourName\Documents\SourceFiles"
destFolder	String	"C:\Users\YourName\Documents\RenamedFiles"
files	String[]	(leave blank)

✅ Step 3: Get All Files from Source Folder
Drag an Assign activity:

vb
Copy code
files = Directory.GetFiles(sourceFolder)
✅ Step 4: Use For Each to Loop Through Files
Add a For Each activity.

ForEach item: file In files

Set TypeArgument to String.

✅ Step 5: Inside the Loop – Generate Timestamp
Add an Assign activity inside the loop:

vb
Copy code
timeStamp = Now.ToString("yyyyMMdd_HHmmss")
Create a timeStamp variable of type String.

✅ Step 6: Get File Name and Extension
Add two Assign activities:

fileName = Path.GetFileNameWithoutExtension(file)

extension = Path.GetExtension(file)

(Create fileName and extension variables of type String)

✅ Step 7: Build New File Name
Add Assign:

vb
Copy code
newFileName = fileName + "_" + timeStamp + extension
(Create newFileName as a String variable)

✅ Step 8: Copy File to Destination Folder
Add another Assign:

vb
Copy code
destPath = Path.Combine(destFolder, newFileName)
(Create destPath as a String variable)

Then use Copy File activity:

From: file

To: destPath

🖥 OUTPUT:
After execution, every file in the source folder will be copied to the destination folder and renamed like:

Copy code
Report_20250511_191201.pdf  
Image_20250511_191202.png  
Notes_20250511_191203.docx  
✅ Result:
The UiPath workflow successfully reads all files from a source folder, appends a timestamp to each file name, and copies them to a new destination folder.
