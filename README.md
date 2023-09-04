# Fantasy_cricket_python_automation
This is the repository consisting code files to set up automated fantasy cricket contest with multiple people.
More information on the implementation is in link doc below
https://docs.google.com/document/d/1l_m8-rP3kcyZpWPO40F5XLaq2e4n91x5M9rWlB3MmLw/edit
The google sheet template is in the link below
https://docs.google.com/spreadsheets/d/1ivkgv13b1h9Zlqc9FcSdOuL6Gqt9SUj1sD_RIbyCA1A/edit#gid=0

## About Fantasy cricket and Fanzy app
Fantasy cricket is a part of the fantasy sports genre. It is an online game in which a virtual team of real cricket players is created and points are scored depending on how those players perform in real-life matches.
P.S: Both paid and non-paid fantasy sports are legal

From the *fanzy* app(free), members in the contest need to form as a group and put their respective teams consisting of 11 out of 22 players playing the actual cricket match. This has to be done before the cricket match starts. Based on the performance in the actual cricket match, points to all cricket players are given by app. And the highest points recepient as per the 11 membered team selected before is the winner.

## APP and API endpoint
1. The api endpoint used for this contest is [fanzy](https://a.fanzy.in/v5/tournaments).
2. Fanzy is an app available in [playstore](https://play.google.com/store/apps/details?id=com.gauthamns.fantasycricket).

## Need for this repo and code
Let us assume a group of friends decided to go for fantasy cricket with fanzy or similar platform for Indian Premier League(IPL). They also want to include fake/real money to make their contest more interesting. Fanzy doesn't manage proper analytics in the app. So, one has to fill the points and earnings each member obtained in notepad/google sheet *manually* after each match. 
There are a total of 60 matches in IPL. And this has to be done for 60 times just for one IPL tournament manually, which is error prone. And a member has to take up this task which includes manual effort.

With this repo, one has to link the fantasy contest provider (fanzy in this case) to google sheet. The code takes care of updating all information (points, earnings etc) in the google sheet. The code runs as a cron job daily to make this happen. All the members are notified with text message once the sheet updation is finished by code. The google sheet provides multiple managed realtime analytics like daily leader board, medals chart etc. And text message alerts are sent to every user after the script is run.

## Tech and softwares used:
1. Python (to write code files)
2. CircleCI (for continuous integration setup)
3. Twilio (For setting up notification alerts)
4. Implemented virtual machine 'instance schedule' and 'cloud functions' to start and stop virtual machine in Google Cloud Platform(GCP) before switching to circleCI to run the code.

## What to do to implement
(all the below steps with more information are shown in the [blog](https://docs.google.com/document/d/1l_m8-rP3kcyZpWPO40F5XLaq2e4n91x5M9rWlB3MmLw/edit))
1. Find the tournament ID (ex: IPL 2021) and player IDs from the fanzy api mentioned above
2. Create a new service account from google cloud/developer console. Add the downloaded service account .json key in the code path. 
4. Create a new google sheet with the template shown in the above link
3. Give edit access to the service account created in the google sheet created.
4. Update the information in variables.py file. (instructions mentioned in the file as comments)
5. Update config.yaml file cron expression as per your requirement
6. Add twilio environment variables *TWILIO_ACCOUNT_SID*, *TWILIO_AUTH_TOKEN* in circleci project settings

All the versions on how the code is modified and developed is in the commit history
Please go through the [blog](https://docs.google.com/document/d/1l_m8-rP3kcyZpWPO40F5XLaq2e4n91x5M9rWlB3MmLw/edit) for more information



