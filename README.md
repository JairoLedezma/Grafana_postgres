# Grafana_postgres

## Purpose
- This readme will provide instructions in order to install and run Grafana and a Postgres database and connect them. 
We will be running a dockerfile for both items to create containers for them. 

## Requiremnets 
- Docker installed and running (This guide will show images from the Docker Desktop application)[Download here](https://grafana.com/docs/grafana/latest/installation/docker/)


#### Step 1 - Creating our Grafana container
- version - 8.1.1
- This command will pull the latest version of grafana (8.1.1) if you choose to run a specific version add `:<version number>` after grafana/grafana.
- You may specify your port at this step in the process after the `-p`. In this case, grafana will be running on port 3000.
- Run this command in your terminal. 
```
 docker run -d --name=test_grafana -p 3000:3000 grafana/grafana

```
- After docker downloads the required files it will output the ID of the container and be running.
We can find it in out Docker application.



