---
title: "Organize Files using Python"
date: 2021-08-05
---

shutil module lets you copy, move, rename, and delete files
{% highlight python %}
# Import the modules
>>> import shutil, os
>>> from pathlib import Path
# Set the variable p to the home path
>>> p = Path.home()
# Copy ~/'spam.txt'/ to directory ~/some_folder/ - This assumes that the some_folder directory already exists
>>> shutil.copy(p/'spam.txt'/,p/'some_folder')
# Copy contents of ~/eggs.txt to ~/some_folder/eggs2.txt
>>> shutil.copy(p/'eggs.txt',p/'some_folder/eggs2.txt)
# Copy all content in ~/some_folder to ~/some_folder_backup
>>> shutil.copytree(p/'some_folder',p/'some_folder_backup')
# Move ~/bacon.txt into directory ~/eggs/ - This assumes that the eggs directory already exists
>>> shutil.move('~/bacon.txt','~/eggs')
# The file bacon.txt is moved and renamed to new_bacon.txt
>>> shutil.move('C:\\bacon.txt', 'C:\\eggs\\new_bacon.txt')

# os.unlink with delete a file, os.rmdir will delete a folder - THESE CALLS PERMANENTLY DELETE FILES AND DIRECTORIES.
# when using either of these options, comment out the unlink/rmdir calls and use the print command to see what will be deleted
>>> import os
>>> from pathlib import Path
>>> for filename in Path.home().glob('*.rxt'):
>>>     #os.unlink(filename)
>>>     print(filename)

# send2trash can be used to send items to trash instead of deleting them
pip install --user send2trash
# Create a file called bacon.txt, write to the file, close and move the file to trash
>>> import send2trash
>>> baconFile = open('bacon.txt', 'a')   # creates the file
>>> baconFile.write('Bacon is not a vegetable.')
25
>>> baconFile.close()
>>> send2trash.send2trash('bacon.txt')

# Print current directory, subfolders, and file inside current directory using os.walk
import os

for folderName, subfolders, filenames in os.walk('C:\\delicious'):
    print('The current folder is ' + folderName)

    for subfolder in subfolders:
        print('SUBFOLDER OF ' + folderName + ': ' + subfolder)

    for filename in filenames:
        print('FILE INSIDE ' + folderName + ': '+ filename)

    print('')
