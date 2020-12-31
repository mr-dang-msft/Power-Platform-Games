# Power Platform Games
Samples of games and game support tools developed on Microsoft Power Platform

# Mr. Dang's Isometric Dojo
Have you seen the progress I've been making on my isometric game? Does it make you want to make your own? The Isometric Dojo contains some of the patterns I have in my own game and you can make it your own. It is not meant to be a game that you play but that you create.

In v1.01 you will find comments in many of the formulas. This is meant for you to see the common patterns used to make the game.

[![Isometric Dojo](https://pbs.twimg.com/media/EqfDqq9VEAU9LVH?format=jpg&name=4096x4096)](https://twitter.com/mrdang/status/1344267986526322690)

### Version history
| File name | Description | 
| --- | :-- | 
| Isometric_Dojo_v1.01.msapp | v1.01: Simplified tile instructions, added mini-game |
| Isometric_Dojo_v1.0.msapp | v1.0: Initial version |

### Setup
##### Prepare the tiles
The app uses artwork that is free with attribution. Please follow these instructions to download the art and host it on your own storage.
1. Download the wooden tiles (groundtiles_wood.png): https://jaqmarti.itch.io/isometric-groundtile-library
2. Upload groundtiles_wood.png to cloud storage of your choice and copy its URL.

Copyright/Attribution Notice:
Isometric Groundtile Library by Jaqueline Martin - www.patreon.com/jaqmarti

##### Prepare the sprites
3. Download the crusader sprites (isometric_Mini-Crusader.zip): https://remos.itch.io/mini-crusader
4. Extract the folder from isometric_Mini-Crusader.zip. 
5. Rename the folder with images of the crusder getting hit from "got-hit" to "gothit" to match the image files.
6. Upload the folders for the sprite to cloud storage of your choice and copy the path of the folder.

Copyright/Attribution Notice:
Isometric Mini-Crusader by Bleed - [remusprites.carbonmade.com](https://remusprites.carbonmade.com/)

##### Configure the app
7. Download the msapp file from this repository (Isometric_Dojo_v1.01.msapp): https://github.com/mr-dang-msft/Power-Platform-Games/blob/master/Isometric_Dojo_v1.01.msapp.
8. Open the Power Apps studio (create.powerapps.com) and login.
9. Go to File > Open > Browse then locate and open Isometric_Dojo_v1.01.msapp.
10. Click the App object from the tree view.
11. Go to the OnStart property of the App object. Expand the formula bar and revise the OnStart property to update the variables for:
* varBlobURL: Paste in a base URL that goes ahead of the folder for sprites.
* varSpritesFolder: Paste in the path to the folder with sprites.
* varTilesheet: Paste in the URL to go directly to groundtiles_wood.png.
13. Select the ellipsis beside the App object in the tree view. Click Run OnStart.
14. Save the app.
15. Play the app.
16. Customize the app and make it yours!

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
1. Download the most updated files for the Animal Crossing companion app (v1.03).
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

Start by downloading the Chess.Deploy flow and the latest version of Chess for Power Apps:

| File name | Description | 
| --- | :-- | 
| Chess.Deploy_20200815093400.zip | Flow for setting up tables |
| Chess.Invite_20200815233705.zip | Flow for inviting players to a match (optional) |
| Chess_for_Power_Apps_v1.03.msapp | v1.03 Chess for Power Apps (most recent), fixed a guest user bug |
| Chess_for_Power_Apps_v1.02.msapp | v1.02 Chess for Power Apps, fixed an iOS bug |

The import consists of these major steps:
* Importing the data source
* Importing the app
* Optional: Enabling guest access
* Optional: Enabling invitations by adaptive card
* Optional: Enabling push notifications

Before proceeding, be sure to have a connection to SharePoint if you do not have one already. You can follow instructions on the Docs site to [add a connection](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-manage-connections).

### Importing the data source
This chess app uses SharePoint as a data source. The included flow will provision the lists needed for the game. Feel free to use an alternative data source with the same schema. Most fields are simply text.
1. Go to [flow.microsoft.com](https://flow.microsoft.com). In the left pane, select 'My flows.'
2. From the top menu, click Import.
3. Click Upload and browse for the Chess.Deploy zip file. Click Import.
4. If this is your first time importing the app, you may need to create a connection to SharePoint by selecting "Select during import" and following the instructions on the screen.
5. Click import.
6. Edit the flow.
7. Locate the action for 'Initialize variable.' Set its value to a SharePoint address where you want the lists to be created. Save the flow.
8. Run the flow once by clicking Test or going back to the flow's details page and clicking Run. It will create the necessary lists. Attempting to run the flow again may fail as the lists may already exist.

### Importing the app
9. Visit [make.powerapps.com](https://make.powerapps.com/home). From the left pane, click 'Apps.'
10. From the top menu of the Apps page, click 'New app' > Canvas.
11. When the Power Apps studio opens, click File > Open and browse for the .msapp file that was downloaded earlier. Open it.
12. Open the data pane from the left side by clicking the cylinder icon.
13. From the data pane, click 'Add data', search for and select your SharePoint connection.
14. In the pane that appears on the right hand side, search for the site in which you had created the lists using the deployment flow earlier.
15. Select the lists for this app: GameServer, GameList, GamePlayerData. Click Connect.
16. From the left pane, return to the tree view by clicking the layers icon. Select the App object at the top of the tree view.
17. Expand the formula bar for the OnSelect property of the App object. Scroll to the end where there is a section for admins. Replace the existing email with that of whoever would like to manage this app. Note that this does enable them to debug and manipulate games for testing.
18. Save and publish the app. Do not close the studio yet if you plan to implement the optional features.
19. The app may likely still be in an error state because you had just added connections. You can try clearing the errors by selecting the ellipsis beside the App object in the tree view and click 'Re-run OnStart actions.'

The app is ready for use, but you may want to enable some extra features: guest access, invitations, and push notifications. These are optional, but add much value to the app experience.

External guests may want to play a match of chess with you. Luckily there are not too many steps to enabling this feature as much of the logic is handled in the app. It is only a matter of sharing the underlying data and app with guests.

### Optional: Enabling guest access
1. Open a browser tab to the SharePoint site where the lists for the GameServer were created.
2. At the top right of SharePoint, click the settings icon and then Site Permissions.
3. From the table of different roles, click the Site Members and add a invite the desired guest user(s) by their email address. Keep this browser tab open if you plan on enabling invitations.
4. Open a browser tab to [make.powerapps.com](https://make.powerapps.com/home) and go to the Apps page.
5. Find the Chess app, click the ellipsis beside it and click Share.
6. In the pane that appears on the right, input the email address of the guest(s) who received access to the SharePoint site. It is possible to paste in a list of emails delimited by a semi-colon.

### Optional: Enabling invitations by adaptive card
1. Open a browser tab to [flow.microsoft.com](https://flow.microsoft.com) and go to the 'My flows' tab.
2. From the top menu, click Import.
3. Click Upload and browse for the Chess.Invite zip file. Click Import.
4. If this is your first time working in Power Automate, you may need to create a connection to Microsoft Teams and Office 365 by selecting "Select during import" and following the instructions on the screen.
5. Click import. You can close this tab to Power Automate as there is nothing to update in the flow.
6. Open a browser tab to [make.powerapps.com](https://make.powerapps.com/home) and go to the Apps page.
7. Find the Chess app, click the ellipsis beside it and click Details.
8. Under the heading for Web link is a link structured like so: 
```
https://apps.powerapps.com/play/{appId}?tenantId={tenantId}
```
9. Note down the app id and tenant id as both will be needed. The tenant id is the unique identifier that follows the parameter 'tenantId='.
10. If the app is still open in the Power Apps studio, select the App object from the tree view.
11. Go to the OnStart property of the App object and revise the variable for varTenantId and paste the tenant id between the quotes:
```csharp
Set(varTenantId,"tenant_id_goes_here");
```
12. Structure the variable for the app id in the same way:
```csharp
Set(varAppId,"app_id_goes_here");
```
13. Insert a button anywhere on the screen as a placeholder. It will hold the flow we want for now.
14. With the button selected, go to the ribbon and click Actions > Power Automate. 
15. In the pane that appears on the right, scroll and select the Chess.Invite flow that you imported at the beginning of this section. This adds the flow to the app. Delete the placeholder button for now since we will use existing formulas elsewhere in the app for calling the flow.
16. In the tree view, search for the control ButtonCreateGame. Go to its OnSelect property.
17. In the OnSelect property for ButtonCreateGame, expand the formula bar and scroll down to the section for Send Invitation. There is a formula that has been commented out between the symbols /* */. 
18. Uncomment the formula for sending an invitation by erasing the /* */ that sandwich it.
19. Save and publish the app.

### Optional: Enabling push notifications
1. In a browser tab, return to [make.powerapps.com](https://make.powerapps.com/home). From the left pane, go to the Apps page.
2. Click the ellipsis beside the Chess app and go to its Details. Copy the app id from this page. (You may have this already if you had done it in another step.)
3. From the left pane, expand Data and then go to the page for Connections.
4. Create a new connection for Power Apps notification. Paste in the app id you copied earlier. Save the connection.
5. Before leaving this page, search for the same connection for notifications again. This time, edit it and give it a descriptive name. This is important as you may have multiple connections to Power Apps notifcations.
6. Open the Chess app in the Power Apps studio. You can go to the Apps page, select the ellipsis beside the Chess app and click Edit.
7. In the Power Apps studio, open the data pane by clicking the cylinder icon on the left.
8. Add the connection to the Power Apps notification that you created at the beginning of this section.
9. At the top of the tree view is a search bar. Search for the control called ToggleMoveEnd and select it.
10. Go to the OnCheck property of ToggleMoveEnd. Scroll about midway to a section of the formula for Notification Phase.
11. It includes a section of the formula that has been commented out that looks like the following:
```csharp
If(
    CheckboxNotifications.Value,
    With(
        {
            opponent: LookUp(colPlayerData,Id<>varUser.id)
        },
        PowerAppsNotification.SendPushNotification(
            {
                recipients: [opponent.UserPrincipalName],
                openApp: true,
                params: 
                    Table(
                        {key: "matchid", value: selectedMatch.ID}
                    ),
                message: "..."
            }
        )
    )
)
```
12. Uncomment the formula by erasing the /* */ symbols that sandwich the formula.
13. Search the tree view for a control called ButtonForfeitConfirm. Scroll to the bottom of its OnSelect property and uncomment the formula for sending a notification for forfeiture.
```csharp
With(
    {
        opponent: Coalesce(LookUp(colPlayerData,Id<>varUser.id),First(colPlayerData))
    },
    PowerAppsNotification.SendPushNotification(
        {
            recipients: [opponent.UserPrincipalName],
            openApp: true,
            params: 
                Table(
                    {key: "matchid", value: selectedMatch.ID}
                ),
            message: varUser.displayName & " has forfeited the chess match."
        }
    )
)
```
14. Save and Publish the app.

