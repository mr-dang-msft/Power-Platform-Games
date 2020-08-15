# Power Platform Games
Samples of games and game support tools developed on Microsoft Power Platform

# Nookidex: a companion app for Animal Crossing
It is difficult to know which critters can be found at any given time in Animal Crossing. Reading and sorting tables on internet articles is inefficient. The Animal Crossing companion app solves this problem by providing a one-click experience to filter out fish, sea creatures, and bugs to only those that are currently available. It also has other features to augment the gaming experience in Animal Crossing.
| File name | Description | 
| --- | :-- | 
| Nookidex_20200807191732.zip | v1.03: Added houseware, settings, villager favorites |
| ACNHViewer_20200806020502.zip | v1.02: Added Turnip price tracker |
| ACNHViewer_20200802202013.zip | v1.00: App package to import into Power Apps |
| AnimalCrossing.swagger.json | Swagger file for creating a custom connector |

![A screenshot of the Animal Crossing companion app showing a screen for sea creatures. At the top of the screen is a header with a title for sea creatures. Below that are a set of drop down menus for filtering sea creatures. Below that is a grid showing the resulting filter of sea creatures.](https://powerblob.blob.core.windows.net/powerapps/acnhapp_sea.png "Sea Creatures screen")

### Setup
##### Importing the custom connector
1. Download all files for the Animal Crossing companion app.
2. Visit [make.powerapps.com](https://make.powerapps.com/home). From the left pane, click 'Data' and then 'Custom Connectors.'
3. In the Custom Connector page, from the top right, click 'New custom connector' and then 'Import an OpenAPI file.'
4. Browse for the .swagger.json file that was downloaded earlier.
5. Name the custom connector AnimalCrossing. Create the custom connector.

##### Importing the app
6. Visit [make.powerapps.com](https://make.powerapps.com/home). From the left pane, click 'Apps.'
7. In the Apps page, click 'Import canvas app.'
8. Click Upload and browse for the .zip file that was downloaded earlier.
9. In the page for Import package, find the row for the AnimalCrossing custom connector.
10. Under the column 'Import setup,' click 'Select during import.' Select the AnimalCrossing custom connector made in the previous steps.
11. Click Import.

### Credits
The Animal Crossing companion app and its custom connector use data and images from the [ACNH API](http://acnhapi.com/) by [Alexis Lours](mailto:admin@acnhapi.com). 

# Chess for Power Apps
I am releasing v1 of Chess for Power Apps. It is actually my third attempt at creating it on the weekends. Each time I've made it more and more efficient, and each time, it teaches me something new to take back to my bizapps. 

I am an advocate of learning a skill within a relevant context. Chess is a game that is both timeless to play and to create. So it was an excellent backdrop to practice making apps with a context I was familiar with in terms of rules, gameplay, and design. The game involves many opportunities to filter: finding which squares a piece can move to, identifying which squares keep a king in check, checking which moves may count towards en passant, etc.

Within the app, I hope you will see many examples of these patterns in context-- and with comments!
* Filtering tables with multiple conditions
* Left joining tables using Ungroup()
* Validating and executing commands
* Multiplayer support: both synchronous and asynchronous gameplay
* Using SVG to make more efficient graphics
* and more!

Below you will find instructions on how to set up the data source and import the app for yourself. What you choose to do with the app is up to you!

Start by downloading these required files:

| File name | Description | 
| --- | :-- | 
| Chess.Deploy_20200815093400.zip | Flow for setting up tables |
| Chess for PowerApps.msapp | v1 Chess for Power Apps (msapp file) |

### Importing the data source
This chess app uses SharePoint as a data source. The included flow will provision the lists needed for the game. Feel free to use an alternative data source with the same schema.
1. Go to [flow.microsoft.com](https://flow.microsoft.com). In the left pane, select 'My flows.'
2. From the top menu, click Import.
3. Click Upload and browse for the Chess.Deploy zip file. Click Import.
4. If this is your first time importing the app, you may need to create a connection to SharePoint by selecting "Select during import" and following the instructions on the screen.
5. Click import.
6. Edit the flow.
7. Locate the action for 'Initialize variable.' Set its value to a SharePoint address where you want the lists to be created. Save the flow.
8. Run the flow once. It will create the lists. Attempting to run the flow again may fail as the lists may already exist.

### Importing the app
9. Visit [make.powerapps.com](https://make.powerapps.com/home). From the left pane, click 'Apps.'
10. From the top menu of the Apps page, click 'New app' > Canvas.
11. When the Power Apps studio opens, click File > Open and browse for the msapp file that was downloaded earlier. Open it.
12. In the Power Apps studio, open the data pane from the left side.
13. Remove the existing connections to the SharePoint lists by clicking the ellipsis beside each one and clicking Remove. These need to be replaced with your own lists.
14. From the data pane, click 'Add data', search for and select your SharePoint connection.
15. In the pane that appears on the right hand side, search for the site you had created using the deployment flow earlier.
16. Select the lists for this app: GameServer, GameList, GamePlayerData (the third list is not used). Click Connect.
17. From the left pane, return to the tree view. Select the App object.
18. Expand the formula bar for the OnSelect property of the App object. Scroll to the end where there is a section for admins. Replace the existing email with that of whoever would like to own this app.
19. Save and publish the app.

At this point, if you would like to have push notifications in the app, skip this next section (steps 20-24) and proceed to step 25. If you do NOT want push notifications, continue with step 20.

### Configuring notifications
##### Steps for removing push notifications
20. At the top of the tree view is a search bar. Search for 'end'. Select the control ToggleMoveEnd.
21. Go to the OnCheck property of ToggleMoveEnd. Scroll about midway to a section of the formula for Notification Phase.
22. Delete the formula starting with a condition for notifications. Or modify it to perform the kind of alert of your choice.
23. Search the tree view for a control called ButtonForfeitConfirm. Scroll to the bottom of its OnSelect property and remove the formula for sending a notification for forfeiture.
24. Remove the connection to Power Apps notification from the data pane as well if you do not want the notifications.

##### Steps for maintaining push notifications
25. In another browser tab, return to [make.powerapps.com](https://make.powerapps.com/home). From the left pane, go to the Apps page.
26. Click the ellipsis beside the Chess app and go to its Details. Copy the app id from this page.
27. From the left pane, expand Data and then go to the page for Connections.
28. Create a new connection for Power Apps notification. Paste in the app id you copied earlier. Save the connection.
29. Before leaving this page, search for the same connection again. This time, edit it and give it a descriptive name. This is important as you may have multiple connections to Power Apps notifcations.
30. Return to the browser tab with the Power Apps studio. Remove the existing connection to the Power Apps notification. Then add the connection you just created. 
31. Save and publish the app.

With the same app id copied, one final step is to add it to the Game List on SharePoint.
32. Go to the SharePoint site that you created with the flow. Locate the list for GameList. 
33. Add a new item with "Chess" as the Title (no quotes). And paste in the app id as the app id. Save the item.
