# BIKESHARE TORONTO ANALYTICS + STRAVA CONNECTION


### Overview
**NOTE: This is an unofficial doc, not sanctioned by BikeShare TO and there is no partnership**

Think of this as a kind of Spotify Wrapped, but for BikeShare TO. BikeShare TO doesn't have any usage stats / analytics, so I thought I'd take a crack at building it out myself.

Additionally, it can also connect to a Strava account and post rides there.


### Current functionality
1. Login to BikeShare TO (via parsing website's HTML)
2. Get trip history (via parsing website's HTML), comes back 50 at a time so have to interate through
3. Get station location from OpenData TO
4. Match trip history to station GPS coordinates
5. Cleans data: Removes trips with same start and end station, removes trips with null end location (broken), finds missing stations from OpenData TO list, and matches to manually created dictionary with station name and GPS coordinates
6. Calculate distance of every trip from Google Maps API, and average speed for each trip
7. Calculate number of trips per month, total and average distance per month, find top 5 most common routes
8. Caching / saving functionality, to prevent unnecessary API calls. Stores data in a caching.json file, then checks against that to only pull new trips from PBSC and get the distance from Google Maps for only those trips. 
9. Year in Review creation: Using the template, programatically inserts the user-specific variables and graphs 
10. Login to Strava, connect 

### Future functionality
1. (Possibly) Extract out of a jupyter notebook, could host on a website

### How to use:
1. Download this repo
2. Ensure you have jupyter notebook and python installed (ask ChatGPT for help if needed)
3. Install dependencies, listed below
4. Create a Google Developer account, and get a Google Maps API key. This should be free for directions, or at least free for several thousand monthly requests. 
5. Create a env.py file. In there create:
- USERNAME = {your BikeShare username}
- PASSWORD = {your BikeShare password}
- MAPS_API_KEY = your Google Maps API Key

### Known Deficienes
1. BikeShare TO occasionally changes the stations, and therefore the lookup will fail. I have created a manual lookup based on station name, where I have added the Lat and Lon coordinates. There is code already to find the unmatched trips, you'll just need to manually add the coordinates for the station that you have that doesn't have a match.

### Dependencies
beautifulsoup4
env
googlemaps
matplotlib
panda
Requests


