
- Browse the web app & found these PHP file endpoints (contact.php, application.php, image.php)
- File upload function at apply.php (no file type filter)
- LFI in api/image.php?p= (fuzz the payload) (use file_get_contents, so no PHP execution, READ only)
- Able to read source code --> application.php leaks uploaded file endpoint and file name encoding format (md5)
- contact.php source code leaks ?region= parameter (there is a filter for . and /, bypass with double URL encoding)
- Create a PHP shell and upload. md5sum shell.php (to know the file name)
- Load the uploaded file path in the contact.php page with ?region=