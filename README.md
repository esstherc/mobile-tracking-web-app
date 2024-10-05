# Mobile Tracker UI and Data Visualization Project
![UserInterface](https://github.com/esstherc/mobile-tracking-web-app/blob/main/images/user-interface-1.jpg)
![UserInterface](https://github.com/esstherc/mobile-tracking-web-app/blob/main/images/user-interface-2.png)
## Workflow
![Flowchart](https://github.com/esstherc/mobile-tracking-web-app/blob/main/images/Flowchart.jpg)

I used Figma to design the UI of our mobile tracker. The navigation bar consists of five components:

	1.	Back to homepage icon button
	2.	Instruction scroll down button
	3.	Path visualization page (displays map)
	4.	Space-time path page (displays routes in a space-time cube)
	5.	Login button (navigates to the tracking page)

After completing the UI design, we integrated the following functions in start-tracking.html:

	•	Mobile tracking and webpage tracking: Tracks and stores location information every 30 seconds.
	•	User ID validation: Prompt function verifies the user ID before generating tracking results.
	•	Geolocation tracking: Retrieves and logs the user’s current position at intervals of 30 seconds.
	•	Data storage: Location data is stored in data.csv and formatted as a JSON file using a custom writeToCSV function.
	•	UI update: The user’s current location is displayed and refreshed every 30 seconds.
	•	Route visualization: The tracked routes are visualized on the Path Visualization page, with an animation that changes the tracking button’s shape every second.

The CSV file serves as the database for storing location and timestamp information during the geolocation process. A PHP script is used to convert CSV data into JSON files for use in Mapbox.

## Data Collection and Transmission

The data collection begins with the geolocation of the user, achieved through the myGeoLocator function. Once authenticated using a valid user ID, the function:

	•	Extracts the current latitude and longitude of the device using the HTML Geolocation API.
	•	The method for extracting geolocation (e.g., GPS, cell towers) varies depending on the environment and device.

This query runs every 30 seconds via the extractPosition function while the webpage is active. The position and timestamp are recorded in a .csv file using the writeToCSV function, allowing for session-based location tracking.

To test the tracking functionality, use the following user ID: 260917220.

## Map Creation

The geographic display of results was implemented using Mapbox with data converted from CSV to JSON via PHP. Key steps:

	•	Modified PHP scripts to include timestamps within the JSON output for time-based data visualization.
	•	Applied custom CSS for the legend, navigation menu, and map to enhance user experience and ensure the map fits well on the screen.
	•	Implemented the add.layer command in Mapbox to display routes using varying shades of green for visual consistency with the website.
	•	Added interactive buttons pointing to the tail of each route and a visibility toggle for map layers.
	•	Implemented pop-ups using GeoJSON data, displaying the start and end points of each route along with the timestamp.

## Challenges

	•	Displaying accurate routes: Due to limitations in coordinate harvesting, the displayed routes sometimes showed erratic curves, even in straight paths. Static positions occasionally jumped unpredictably.

## Yanbing’s Reflection

The process of extracting personal location data was simpler than expected, requiring only a few lines of code. However, it’s important to recognize two prerequisites for geolocation:

	1.	Location services must be enabled, and the app must have access to location data.
	2.	User permission is required to share location data, which may depend on the browser and device settings.

During testing, I encountered issues when the location-sharing reminder didn’t appear, due to disabled settings in Chrome. This emphasizes the importance of device settings in protecting privacy. It’s clear that while this app couldn’t track location with the screen off, other apps may still collect user data even when in the background.

In conclusion, location data can be easily extracted and analyzed. Users should remain cautious when sharing location information with apps.
