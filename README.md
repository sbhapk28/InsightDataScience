# Procedure followed to make Systems-Puzzle work 

1. Installed Docker for windows - got problem with running the docker due to machines virtualization was not enabled. Enabled machine virtualization in BIOS setting to run the Windows docker
2. Downloaded the Repo from git hub 
3. Run the command mentioned in the System puzzle that installed Python, flaskapp, nginx and database
4. It was giving problem to build the flaskapp - after research it realized the Port 80 was used by windows IIS service
5. So changed the nginx listening port to 8095 also updated the flaskapp config file to listen server at port 8095
6. Now I was able to build the application and docker containers were created successfully but when I was trying to access url "localhost:8095" it was giving error "502 Bad Gateway"
7. After checking the code I updated the flask app.py run command function, I passed port 5001 to run function.
8. Rebuild the whole docker by command "docker-compose up --build -d" checked all docker containers are created and runing by command "docker ps"
9. Now I was able to access the flaskapp on url "localhost:8095"
10. Tried to add item into database but giving some error, so I investigated the code, I found some issues like below
 
 a. HTML Descritpion field length is only 4 but Database Description field length is 256 same with field label
 b. Now I was able to add the item into database but Success page was not showing Items table data properly
 c. So I created success.html and passed items list to the html page and created HTML template to show all records present into the items table
 
 # localhost:8095/success : Please visit this page which will show all items added into the "Items" table.