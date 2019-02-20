---
layout: post
title: Note taking with Google Apps
---

*Note taking workflow on Google Apps*

The best note taking workflow is the one you don't have to think about. If I can open up a folder with placeholders for all of the notes I will need to take for the day, I am way more likely to actually take notes. This workflow creates Google Docs for each event on my calendar for that day. 

The script includes a setup routine to create the necessary folders and text file. Each event Doc will be created in a folder called 'Today' in the same folder where the script is stored. Triggers are created for the project that will generate docs at 2am local time every day. A cleanup function will run to either archive modified files from the day before or delete unmodified docs from the previous day.

A file call `meetingTemplate` will be created that will be cloned as the body for each of the Docs created. This file can be edited to fit specific notetaking needs.

Here's the JS - I attach it to a GDoc. [google-scripts/cal2docs.gs at master · cloin/google-scripts](https://github.com/cloin/google-scripts/blob/master/cal2docs.gs) 

You should be able to paste the GS file contents into `Tools>Script editor`, reload the doc and there should be a menu called `Script menu` in the menu bar of the doc to run the setup function and then the create doc function. The setup routine creates the cron like triggers that create from docs from here on out. 
