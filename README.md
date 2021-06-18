# NewsCrawler
A news-database that is regularly updated where we can search and filter for certain articles.

This repo contains a web scraper that crawls the url: https://www.spiegel.de/international/ and extract its news entries. All the entries are stored systematically in a postgres database via docker. After every 15 minutes, the crawler is triggered automatically.

Installation Guide
Step 1: Install Database via docker
-----------------------------------

1. Launch docker.

2. Pull latest DB image by running the following command in your terminal:
docker pull postgres:latest

3. Use the following command to run DB container:
docker run --restart always -d --name dm-postgres -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -p 4000:5432 postgres

Step 2: Setup Code
------------------

1. Download the code

2. The code directory contains a requirements.txt file that contains all the required libraries that need to be executed

3. To install the libraries via requirements file, execute the following command:
pip3 install -r requirements.txt

4. To execute the code, run the following command:
python3 main.py

Step 3: Schedule crawler to run every 15 minutes
----------------------------------------------

1. Set cronjob by running the following command:
crontab -e          (OPENS CRONTAB EDITOR)

2. Write the following command in the opened cron tab
*/15 * * * * /usr/bin/python3 /code/main.py >> /var/log/cron.log 2>&1 ("/var/log/cron.log 2>&1" is optional if you want to get the logs)

3. Save & close.

Note: Step 3 is for Linux. 

Now, you are all set. That's it. :)
