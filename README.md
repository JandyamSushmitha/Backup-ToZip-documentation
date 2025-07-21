## To create a backup of a folder by compressing all its contents  into a ZIP file.

Step-by-Step Algorithm
Step 1: Start

Step 2: Accept the path of the folder to be backed up (input folder path)

Step 3: Check if the input folder exists
  • If not, display an error message and terminate
  • If yes, continue

Step 4: Generate a unique ZIP file name using the current date and time
  • Format: "backup_YYYYMMDD_HHMMSS.zip"

Step 5: Create a new ZIP file with the generated name

Step 6: For each file in the folder and its subfolders:
  a. Get the full file path
  b. Compute the relative path (relative to the input folder)
  c. Add the file to the ZIP archive using the relative path

Step 7: Finalize and close the ZIP file

Step 8: Display a success message with the path of the created ZIP file

Step 9: End

🔄 Flowchart Summary (optional for visual aid)
pgsql
Copy
Edit
[Start]
   ↓
[Input Folder Path]
   ↓
[Does folder exist?] → [No] → [Show Error & Exit]
         ↓ Yes
[Generate ZIP filename with timestamp]
   ↓
[Create ZIP file]
   ↓
[For each file in folder & subfolders]
      ↓
[Add file to ZIP with relative path]
   ↓
[End loop]
   ↓
[Close ZIP file]
   ↓
[Display success message]
   ↓
[End]



# Backup of folder into a zip file

# Copies the whole contents of any folder into a zip file whose filename increaments

# File format should be like this filename_number.zip (number should be increamented)

def backup(folder):
	# Backup the content of folder into a zip file

	folder = os.path.abspath(folder)

	number = 1

	while True:
		zip_name = os.path.basename(folder) + '_' + str(number) + '.zip'

		if not os.path.exists(zip_name):
			break
		number = number + 1

		print ("Creating file %s" %(zip_name))

		backupzip = zipfile.ZipFile(zip_name,'w')

		# Walking through the whole directory

		for foldername, subfolders, filenames in os.walk(folder):
			print ('Adding the file %s'%(foldername))
			backupzip.write(foldername)

		backupzip.close()

		print ('Succeeded')

		
