## Table of Contents

* [Overview](#overview)
* [User Guide](#user-guide)
* [Developer Guide](#developer-guide)
* [Development History](#development-history)
* [Team](#team)

## Overview

The WfInstances Browser is a web application that allows users to browse, select, and visualize the available [workflow instances](https://github.com/wfcommons/WfInstances) provided by the [WFCommons Project](https://wfcommons.org). It is currently live in deployment at [https://wfinstances.ics.hawaii.edu/](https://wfinstances.ics.hawaii.edu/).

## User Guide

In the WfInstances Browser, users are able to download, visualize, and simulate workflow instances. Additional modals are located on the navbar for usage report, app help, an about section, and the option to toggle between light and dark mode. 

## Developer Guide

To run the server for production, you will need [Docker Desktop](https://www.docker.com/).

Running with Docker; 

Dependencies:
- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

Edit/use one of the `.env-*` files to configure the deployment, and then:

```bash
$ docker-compose --env-file <.env file> build  --no-cache
$ docker-compose up [-d]
```

The above will not run any Nginx front-end. If you want to do so, you must add the `--profile with-my-own-nginx` argument to the `docker-compose` commands above.

The database is empty the first time you launch the browser. To populate the database with metrics from the official [WfCommons WfInstances GitHub repo](https://github.com/wfcommons/WfInstances), run this command in a terminal on the machine running the server:
```
curl -X PUT http://localhost:8081/metrics/private/github/wfcommons/WfInstances
```

REST API documentation is available at: [http://localhost:8081/docs](http://localhost:8081/docs)

(The above assumes WFINSTANCES_API_PORT=8081 is the configured port for the backend, as condigured in the `.env-*` file in use.)

## Development History 

### issue-001: Usage Stats Modal
- Created the modal for usage report and added it to the navbar
- Imported button icon from React Bootstrap
- Opens a modal which will store app usage information

### issue-002: UI shows data from API fetch 
- Created new API endpoint to show total count each for downloads, visualizations and simlulations
- Usage report displays data fetched from url route: .../usage/public/totals
- Modal shows total number of downloads, visualizations and simulations

### issue-003: User Survey 
- Created a button that opens a questionnaire modal within the navbar
- Imported pencil icon for button from React Bootstrap
- Currently is not connected to a database
- Asks the user for to provide a name, email, and app feedback

### issue-004: API endpoint for weekly usage
- Created new endpoint to get weekly usage data grouped by their type (download, visualization, simulation)
- Also retrieves the number of unique IPs per week 

### issue-005: Graph Visualization
- Implemented a graph feature using Chart.js to visualize the total count of what was used in the app 
- Fetches weekly data for downloads, visualizations, and simulations based on the selected type
- Buttons allow to toggle between the three different types of usage

### issue-006: IPInfo IP Geolocation Tracking
- Enabled IP geolocation to see which countries use the app the most
- Resolves user IP to a country name

### issue-007: Sidebar for the top usage countries
- Added a sidebar within the usage report modal that displays the countries that have used the app the most
- Uses IP geolocation from previous issue to resolve a user's IP to a country name if they used an app feature
- Displays top ten countries based on combined usage (downloads, visualization, simulation)

### issue-008: Timescale feature
- Implemented a timescale feature for the graph
- Users can zoom/pan out of the chart to see data from a particular time more in-depth

### issue-009: UI adjustments
- Updated the UI to make it look more cohesive and easier to navigate
- Data is fetched in parallel to make it faster
- Graph is made bigger (left side for the graph, right side for the top countries sidebar)
- Section for totals at the bottom of the modal's left column for combined count each for downloads, visualizations, and simulations

### issue-010: API endpoint for monthly usage
- Changed how data is retrieved from weekly to monthly usage
- Created new endpoint to get monthly usage data grouped by their type (download, visualization, simulation)

### issue-011: Random Survey Pop-up
- A random survey will pop-up when user has used download, visualization, and simulation on the 5th, 50th and 500th event
- Asks two questions to give the app a rating based on usability and usefulness
- “On a scale of 1 to 10 how would you rate the usefulness of this application?” when occasionally prompted
- “On a scale of 1 to 10 how would you rate the usability of this application?” when occasionally prompted
- Added a survey database to account for total user clicks, IP, and rating number

### issue-012: Updated the graph's legend
- Changed chart legend to use a line representation instead of a square
- Used rgba(75, 192, 192, 0.2) for download/visualization/simulation solid line
- Used rgba(255, 99, 132, 0.2) for unique IPs dotted line
- Updated pan feature so you can pan both left/right and up/down on the graph

### issue-013: Redesign of workflow instances retrieval
- Use git clone and git pull to update the workflow instances
- Cron job to git pull every hour instead of every 7 days
- Git cloning instance of repo for WfInstances functions as intended
- Clones repo if it does not exist locally

### issue-014: Filter the graph's date range
- Replaced the zoom/pan feature of the graph to have a filter date range instead
- Allows users to select MM/YY - MM/YY range to view the timescale only within that scope

### issue-015: Satisfaction database
- Implemented a satisfaction database to store the results of the user survey ratings
- Ratings range from 1 to 10
- The collection is used to keep track of score distribution for app features (simulations, visualizations, general usage)

## Team 

1. [Jianlong Chen](https://jianlongchenn.github.io/)
2. [Kenneth de Guzman](https://k-deguz.github.io/)

## Organization

> Github Organization: [View](https://github.com/orgs/WfInstances/repositories)
