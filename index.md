## Table of contents

* [Overview](#overview)
* [User Guide](#user-guide)
* [Developer Guide](#developer-guide)
* [Remix Development](#remix-development)
* [Development History](#development-history)
* [Walkthrough videos](#walkthrough-videos)
* [Example enhancements](#example-enhancements)
* [Team](#team)

## Overview

The WfInstances browser is a web application that allows users to browse, select, and visualize the available [Workflow Instances](https://github.com/wfcommons/WfInstances) provided by the [WFCommons Project](https://wfcommons.org). 

## User Guide

Users are able to download, visualize, and simulate workflow instances. There are additional buttons for features located on the navbar for: usage statistics report, user survey, site support, an about section and an option for a light/dark mode. 

## Developer Guide

To run the server for production, you will need [Docker Desktop](https://www.docker.com/).

1. Download the [repo](https://github.com/WfInstances/wfinstances-browser) onto your local machine from GitHub.
2. Go into your local machine's directory where the wfinstances-browser is located. (cd ...)
3. Run the command:
```
docker-compose up
```

This will build Docker images, run containers and starts a Web server on which
the browser can be accessed at [http://localhost](http://localhost).

The database is empty the first time you launch the browser. To populate the database with metrics from the official [WfCommons WfInstances GitHub repo](https://github.com/wfcommons/WfInstances), run this command in a terminal on the machine running the server:
```
curl -X PUT http://localhost:8081/metrics/private/github/wfcommons/WfInstances
```

## Remix Development 

Making changes to the UI is supported by Remix's hot reloading so that there is faster iteration and rapid development without doing a full rebuild. 

1. Go in the directory where the repo is located on your local macine (cd ...)
2. From your terminal:

```sh
npm run dev
```

This starts your app in development mode, rebuilding assets on file changes.

3. Build your app for production:

```sh
npm run build
```
4. Then run the app in production mode:

```sh
npm start
```

5. Pick a host to deploy it to.

If you're familiar with deploying node applications, the built-in Remix app server is production-ready.

Make sure to deploy the output of `remix build`

- `build/`
- `public/build/`


## Development History 

### Issue-001: Usage statistics 

- Implemented the usage report button onto the navbar
- Has a button icon
- Opens a popup where usage stats information are shown

### Issue-002: UI shows data from API fetch 

- Created new API endpoint to show total count each for downloads, visualizations and simlulations
- Usage report shows data fetched from localhost/usage/public/totals
- Button shows total number of downloads, visualizations and simulations

### Issue-003: User survey 

- Implemented the questionnaire button onto the navbar
- Not connected to collection yet
- Asks for name, email, and feedback

### Issue-004: Weekly usage API endpoint

- Created new endpoint to get weekly usage data grouped by their type (download, visualization, simulation)

### Issue-005: Line chart graph

- Implemented a graph using Chart.js to visualize the total count of what was used in the site 
- Fetches weekly data for downloads, visualizations, and simulations based on selected type
- Has buttons to switch between the three different types of usage

## Walkthrough videos

...

## Example enhancements

1. Git clone of repo and keep JSONs locally. Refactor way we look at workflow instances and disable outside route of we get usage statistics
2. Add rating system to user survey
3. Add collection for rating system used in user survey
4. Show unique IPs on a world map based on what they used on the site

## Team 

1. [Jianlong Chen](https://jianlongchenn.github.io/)
2. [Kenneth de Guzman](https://k-deguz.github.io/)

## Organization

> Github Organization: [View](https://github.com/orgs/WfInstances/repositories)
