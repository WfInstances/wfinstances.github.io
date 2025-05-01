Please see https://wfinstances.github.io/ for the WfInstances Browser home page for the user and developer guide. 

Below is a summarized outlook of our progress and the discussions in the sponsor meetings between [our team](https://github.com/orgs/WfInstances/repositories) and [Professor Henri Casanova](https://henricasanova.github.io/)

## Meeting Minutes
#### Team: Jianlong Chen, Kenneth de Guzman

---
### Meeting 1 (Week: 1/21 - 1/27)

Date: Tuesday, 1/21/25

Business:
- Project was introduced 
- Went over scope of project
- Discussed issues and project deliverables 

Actions: 
- Created WfInstances organization for team
- Forked WfInstances-browser repo
- Ran the app and populated the database
- Added a usage report button that opens a popup with placeholder text
---
### Meeting 2 (Week: 1/28 - 2/3)

Date: Tuesday, 1/28/25

Business: 
- Talked about what usage report button should display to user
- Discussed ways to connect backend and frontend
- Went over how the API fetches data

Actions: 
- Created a new issue for making button display data to user
- Added a new totals endpoint to usage/router.py under api
- Modified UsageStatsModal.tsx to fetch data from the totals endpoint
- Went over how to show data better (graph, tabs for separate collections)
- Created button for user survey questionnaire
---
### Meeting 3 (Week: 2/4 - 2/10)

Date: Tuesday, 2/4/25 

Business: 
- Modified database to get accurate dump of usage stats
- Talked about ways to show location of where people are using the system (world map from IPs)
- Continued discussing potential ways to do the visualization of usage data

Actions:
- Created a new API endpoint for weekly usage data grouped by their type
- Implemented a linen chart graph for showing the frequency of what is used on the site
- Added buttons to switch between the three different usage types (downloads, visualizations, simulations)
---
### Meeting 4 (Week: 2/11 - 2/17)

Date: Tuesday, 2/11/25

Business:
- Discussed ways to add IP geolocation
- Went over setting up ipinfo_token to convert IP to a country name
- Sidebar should show countries that use what features of the site most

Actions:
- Implemented the feature for a sidebar to show top countries that use features the most
- Edited get_ip_country_name in service.py to take in IP and return country name
- Added get_top_countries function in service.py to return top 10 countries where features are used most
- Added new endpoints for showing all distinct IPs and their country names and for showing top countries based on combined usage
---
### Meeting 5 (Week: 2/18 - 2/24)

Date: Tuesday, 2/18/25

Business: 
- Short meeting to talk about next steps for project
- Went over plan to add timescale feature to zoom in on graph 

Actions:
- Changed the usage graph to show data by month 
- Added another line in graph for distinct IPs for a month
- Fetch all data in parallel to make it faster
---
### Meeting 6 (Week: 2/25 - 3/3)

Date: Tuesday, 2/25/25

Business: 
- Discussed a redesign to retrieve WfCommons workflow .json files through the git Python package
- Use git clone and git pull to update the workflow instances
- Cron job to git pull every hour instead of every 7 days

Actions: 
- Added timescale feature to zoom in on the usage graph
- Make graph legend use lines instead of square/rectangle for representation
- Change modal size and chart zoom/pan sensitivity
---
### Meeting 7 (Week: 3/4 - 3/10)

Date: Tuesday, 3/4/25

Business: 
- Talked about making the user survey an occasional pop-up instead of a modal on the navbar
- Discussed adding a survey database with a collection to keep track of clicks for visualizations, simulations and downloads
- A satisfaction update that triggers the pop-up survey will appear on the 5th, 50th and 500th event
- Discussed adding a satisfaction database to keep track of the distribution of scores from the user survey

Actions:
- Implemented the new approach for retrieving the WfCommons workflow instances
- Git cloning instance of repo for WfInstances functions as intended
- Clones repo if it does not exist locally
---
### Meeting 8 (Week: 3/11 - 3/17)

Date: Tuesday, 3/11/25

Business:
- No meeting next week on 3/18/25 (Spring Break)
- Discussed changing the zoom/pan feature of the graph to instead use a filter date range
- Discussed editing the survey to ask the user two questions about the usefulness and usability of the app

Actions: 
- Added a surveys collection to account for total user clicks that triggers the pop-up survey
- Survey currently asks the user to rate the app with a number from 1 to 10
- Implemented the filter date range feature for analyzing the graph's usage stats
---
### Meeting 9 (Week: 3/25 - 3/31)

Date: Tuesday, 3/25/25

Business: 
- Talked about editing the pop-up survey to remove the success alert when submitting the survey
- Discussed adding a feature to the README of the wfcommons/WfInstances repo that has the workflow instances
- Discussed developing a GitHub action to display WfInstances Browser usage data

Actions:
- Renamed main repo "wfinstances-browser" to "wfinstances-browser-first-fork" (development repo was not fork of original repo from wfcommons GitHub)
- Moved and copied the files, commits and project board over to the new wfinstances-browser repo
- Implemented the satisfaction database to for keeping track of score distribution
- User survey now asks for two ratings for the app; one for usefulness and the other for usability
---
### Meeting 10 (Week: 4/1 - 4/7)

Date: Tuesday, 4/1/25

Business: 
- Talked more about creating a GitHub action for showing usage data of the WfInstances Browser on the wfcommons/WfInstances repo
- Discussed using shields.io to display badges for total number of downloads, visualizations, simulations, and users

Actions:
- Developed a GitHub action that periodically updates the README of the wfcommons/WfInstances repo
- README uses shields.io badges to show usage report from WfInstances Browser
- Shows total number of users, visualizations, simulations, and downloads 
---
### Meeting 11 (Week: 4/8 - 4/14)

Date: Tuesday, 4/8/25

Business: 
- Discussed the conclusion of the project
- Talked about beginning to work a draft for the poster

Actions:
- Started to work on creating a draft version for the poster
---
### Meeting 12 (Week: 4/15 - 4/22)

Date: Tuesday, 4/15/22

Business: 
- Meeting to discuss progress on poster draft
- Discussed how to best orient the components of the poster

Actions: 
- Modified the layout of the included sections
- Completed polishments for final version of the poster
