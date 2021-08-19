# Grafana_postgres

## Purpose
- This readme will provide instructions in order to install and run Grafana and a Postgres database and connect them. 
We will be running a dockerfile for both items to create containers for them. 

## Requiremnets 
- Docker installed and running (This guide will show images from the Docker Desktop application)[Download here](https://grafana.com/docs/grafana/latest/installation/docker/)


## Step 1 - Creating our Grafana container
- version - 8.1.1
- This command will pull the latest version of grafana (8.1.1) if you choose to run a specific version add `:<version number>` after grafana/grafana.
- You may specify your port at this step in the process after the `-p`. In this case, grafana will be running on port 3000.
- Run this command in your terminal. 
```
 docker run -d --name=test_grafana -p 3000:3000 grafana/grafana

```
- After docker downloads the required files it will output the ID of the container and be running.
We can find it in out Docker application.

<img width="1259" alt="Screen Shot 2021-08-19 at 5 00 31 PM" src="https://user-images.githubusercontent.com/61709408/130150780-204617a9-ac48-47e1-aac2-39a58dab2203.png">

- If we hover over it it will show us a couple of options reharding the container. Click on open in browser to take us to the browser UI.   



<img width="1050" alt="Screen Shot 2021-08-19 at 5 09 38 PM" src="https://user-images.githubusercontent.com/61709408/130150976-e16cf8d3-6e17-41a6-bfc0-77618d14e6c7.png">

- We will be taken to our locally running grafana server hosted on port 3000. It can be reached by going to the URL : `http://localhost:3000/login`.   



-![Screen Shot 2021-08-19 at 5 11 46 PM](https://user-images.githubusercontent.com/61709408/130151220-54408c46-f7fb-42b4-9371-a0dbbee44393.png)

## Step 2 Logging in to Grafana
##  - By Default the Username is `admin` and password is `admin`
- Grafana will ask you to change your password once logged in for the first time. 


## Step 3 - Creating our postgresql container
- version - 12
- This command will pull version 12 of postgres. This is the most recent veriosn that grafana supports. You may choose from versions 9.3 - 12. 
- If you choose to run a specific version add `:<version number>` after `-d postgres:` .
- Docker will be running on port 5432 by default.
- Run this command in your terminal. 
`docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres:12`
- After it is downloaded it will be vailable in our docker application

### This is a brand new postgres server, be sure to create a Database, a schema , and a table populated with data. To connect we need at least a database created.. 

## Step 4 - Connecting grafana to postgresql container
- While in the grafana web page, hover over the side bar and choose Data sources.
- When the next page loads clock on Add Data source 
- Scroll down until you postgresql and click on select. 

<img width="1792" alt="Screen Shot 2021-08-19 at 5 40 51 PM" src="https://user-images.githubusercontent.com/61709408/130155509-6a408ca7-bcd2-4cf7-acaa-28b32d4b9294.png">
.  




<img width="1451" alt="Screen Shot 2021-08-19 at 5 42 03 PM" src="https://user-images.githubusercontent.com/61709408/130155564-7e7872b3-87e1-4671-975f-140039bfd2d3.png">

.  



<img width="901" alt="Screen Shot 2021-08-19 at 5 42 52 PM" src="https://user-images.githubusercontent.com/61709408/130155617-f6fc7206-2a19-4736-ae30-3f23a97e7e81.png">

## Configure our data source

<img width="1787" alt="Screen Shot 2021-08-19 at 5 46 45 PM" src="https://user-images.githubusercontent.com/61709408/130155653-220b96e3-1413-44b3-a456-33ac67fe596e.png">


- The next page should be filled out according to the informationon your end.

* Name : the name you want grafana to show for this data source.
* Host : The hostname and port of where your application is running on. 
   * Localhost not working? Unsure of what your hostname is? Try running this command on your terminal and try that!
   * `$ hostname`.
* Databse :  This is the actual name of a database within your postgresql container. This is not the name we called our container in docker.
* user : The name of a user and the password beloging to the database.
* TSL/SSl Mode : Configure this based on your needs. Or select disable if you wish.
* Version : Choose to the postgresql version you chose to donwload.

# Click on save and test when your done. If the connection is good then it should say so. Click back after.

<img width="409" alt="Screen Shot 2021-08-19 at 10 41 28 AM" src="https://user-images.githubusercontent.com/61709408/130155859-6a2f0bf8-61d0-4d36-9829-1b3f958886be.png">


## You have succesfully connected grafana to Postgres




