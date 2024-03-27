# DROPBOX Uploader

This app takes all the content and structure of the folder
it is ran in and uploads it to your dropbox account. (Apps/<"Your app name">)

## HOW TO USE

What you'll need: 
   Your dropbox app access token.
   Python 3

1. Make sure you have the dropbox module. 'pip install dropbox'.
   (Open a terminal and run python first. " python "/" python3 ")

2. Create an app under your own dropbox account in the "App Console".
   (https://www.dropbox.com/developers/apps)

   a. API type: "Scoped Access API".
   b. Access: "App Folder"
   c. On the permissions tab. In the Files and folders section.
   check "files.content.write"). Submit button on the lower right.
   d. Back on the settings tab. Click the "generate access token"
   button and copy it.

3. Run the script.
   (e.g " python3 dropbox_uploader.py ")
   
4. Paste the access token into the terminal.

5. Accept/Change the folder name and the upload begins.
   Existing files and folders are overwritten.

6. There's an IGNORE_LIST in the script that you can add to
   should you need to exclude any specific files.

7. The uploaded folder with it's content will be in your "Apps" folder, under the name
   of whatever you chose to name your app.

## HOW IT WORKS

1. Dropbox interface class:
   -Parameters: TOKEN and DBX(dropbox api object)
   -Grabs access token from user and creates dropbox
   object from api. Script does not store user token.
   -Also responsible for calling the upload_file method
   from api. With the file to upload as an argument

2. Directory class:
   -Parameters: dropbox_directory and local_directory(where script is)
   -Gets local directory using os.path,
   stores name of the dropbox_directory.

3. verifies the access token by checking length and
   catching (BadInput and AuthError) errors from the
   api.

4. The user is then allowed to keep the suggested
   directory name (same as the local directory) or rename it.

5. Iterates through local directory and calls
   upload_file on each file. excluding this script itself.

Please look at the code documentaion for specifics.
