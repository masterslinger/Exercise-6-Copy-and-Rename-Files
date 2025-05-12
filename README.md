# Exercise-6-Copy-and-Rename-Files
~~~
Name : M.JohnPall
Reg.No : 212224040140  
~~~
## Aim
To create a UiPath workflow that copies all files from a source folder to a destination folder and renames them by appending a timestamp to each file name.

## Materials Required
UiPath Studio (Community or Enterprise Edition)

Windows OS

Two folders on your system:

Source Folder (e.g., C:\Users\YourName\Documents\SourceFiles)

Destination Folder (e.g., C:\Users\YourName\Documents\RenamedFiles)

Basic understanding of file operations and string manipulation

## Procedure
Step 1: Create a New Process
Open UiPath Studio and create a new process named CopyRenameFiles.

Step 2: Create Input Variables
Create the following variables in the Variables panel:

Name : Type	Default Value (optional)
sourceFolder : String	"C:\Users\YourName\Documents\SourceFiles"
destFolder : String	"C:\Users\YourName\Documents\RenamedFiles"
files : String[]	(leave blank)

Step 3 : Get All Files from Source Folder
Drag an Assign activity:
~~~
files = Directory.GetFiles(sourceFolder)
~~~

Step 4: Use For Each to Loop Through Files
 i. Add a For Each activity.
 ii. ForEach item: file In files
 iii. Set TypeArgument to String.

Step 5: Inside the Loop – Generate Timestamp
Add an Assign activity inside the loop:
~~~
timeStamp = Now.ToString("yyyyMMdd_HHmmss")
Create a timeStamp variable of type String.
~~~

Step 6: Get File Name and Extension

Add two Assign activities:
fileName = Path.GetFileNameWithoutExtension(file)
extension = Path.GetExtension(file)
(Create fileName and extension variables of type String)

Step 7: Build New File Name
Add Assign:
~~~
newFileName = fileName + "_" + timeStamp + extension
(Create newFileName as a String variable)
~~~
Step 8: Copy File to Destination Folder
1. Add another Assign:
~~~
destPath = Path.Combine(destFolder, newFileName)
(Create destPath as a String variable)
~~~
2. Then use Copy File activity:
From: file
To: destPath

## OUTPUT:
After execution, every file in the source folder will be copied to the destination folder and renamed like:

![Screenshot 2025-05-11 211134](https://github.com/user-attachments/assets/14acd684-8ff9-4f71-a94d-d21c4cc753e7)

![Screenshot 2025-05-11 211205](https://github.com/user-attachments/assets/dc6e8de1-c169-4514-918f-5ebbd392a119)

![image](https://github.com/user-attachments/assets/e47b084f-ca82-4257-b382-1aac5eb5f11f)

![image](https://github.com/user-attachments/assets/9ac35cba-e81f-44c6-bdf9-41c0268eee70)

## Result:
The UiPath workflow successfully reads all files from a source folder, appends a timestamp to each file name, and copies them to a new destination folder.
