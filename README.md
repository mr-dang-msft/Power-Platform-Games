# Power Platform Games
Samples of games developed on Microsoft Power Platform

### Animal Crossing companion app
| File name | Description | 
| --- | :-- | 
| ACNHViewer_20200802202013.zip | App package to import into Power Apps |
| AnimalCrossing.swagger.json | Swagger file for creating a custom connector |

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
