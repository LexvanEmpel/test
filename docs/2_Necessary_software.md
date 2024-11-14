# Necessary Software

In this second section of the user’s guide, you will find all the necessary steps that must be done before starting working in the Giswater environment, from the pre-installation requirements of the software’s configuration, through the creation of new projects real or example), to test the functionalities of Giswater.
## 2.1 Necessary software
To start working with Giswater you must have at least ## 2 programs:
PostgreSQL: The installation process must include the selection pgAdmin component (Data Base Manager) and Postgis application (Spatial Extension)
QGIS: Geoprocessing Software
PostgreSQL can be on our machine or on any server where we have access. QGIS, on the other hand, must always be installed in our machine.
To download all the necessary software is recommended that you visit the Giswater webpage, where you can find the download links for the softwares and the compatible versions with the ultimate release of the Giswater plugin. 

## 2.2 Download and configuration of PostgreSQL

PostgreSQL is an open-source database with enormous potential, which will be used to store all the data with which Giswater works. Thanks to its geospatial extension PostGIS allows an extremely comfortable relation with GIS, especially QGIS. This extension contains over 1000 geospatial functions, which makes it one of the most powerful GIS software available, although PostgreSQL is not a specific GIS program.
We have at your disposal a collection of tutorial videos to help you get started:
TUTORIALS
GISWATER
There are different available versions to download. To work with Giswater a version within 10 and 16 is needed.
In Github you can check the compatibility between PostgreSQL and Giswater versions.
Version compatibility · Giswater/giswater_dbmodel Wiki
GitHub
Step 1) Considering you already have QGIS installed, you must download PostgreSQL
On the installation process make sure to install all its components. PgAdmin will be the user interface for the Data Base (DB) management. It will be used to manage the database and visualize it. PgAdmin also allows the user to modify the tables, views and rules of the database, as well as consult all the information and manage it.
Further, you must create a password for the superuser, which will be necessary to access your pgAdmin for creating and managing a database and also to do a connection to the database from QGIS.
PostgreSQL components
PostgreSQL Password setting (same as used to enter in pgAdmin - DB manager)=
Usual Port Number adopted
PostGis extension installation (select a compatible version)
In the installation process, habilitate the PostGis Extension
PostGis Component.
Once both programs are installed, after opening pgAdmin the first thing that needs to be done is add a new connection
Step ## 2)      Create a Database for your projects on PostgreSQL using pgAdmin interface
DB creation through the DB manager pgAdmin.
The DB name must not contain special characters or uppercase letters.
Once the new connection is created, the first ‘public’ scheme is automatically created in a database. Next, the PostGIS extension must be added, to have all the GIS functionalities available, as well as the pgRouting extension, which adds routing and network analysis functionalities to the database. pgRouting will be essential for some of the Giswater tools such as the cutting polygon and the longitudinal profiles.
By clicking the SQL command button, we can write our first query
CREATE EXTENSION postgis;
CREATE EXTENSION pgrouting;
CREATE EXTENSION tablefunc;
CREATE EXTENSION unaccent;
As of PostGIS version 3, it will also be necessary to add the specific extension to manage raster layers.
CREATE EXTENSION postgis_raster;
After those steps, its time to go back to QGIS and make a DB connection from QGIS to the just created DB using pgAdmin

## 2.3 Configuration of QGIS

When opening QGIS for the first time, a series of parameters must be configured. They are necessary to work with Giswater:
Create a PostGIS connection to the database where the data schema is located
To work comfortably and quickly with raster data, it is recommended to expand the cache memory of QGIS to 1GB and 1 year, through the menu 'Settings/Options/Network'.
Choose open form if a single entity is selected
How to configure a new connection between QGIS and PostGIS?
1. - Click on the icon Add Postgis Layer
2. - Click over New and in the form introduce the connection parameters.
 Connection form to PostGIS from QGIS. It allows to import layers from the database.
3. - Once the parameters are filled in click on Test Connection. If everything is correct the message will appear:
4. - Click OK. At this time, the connection information will be saved with the name on the connection list.
If we want to create new schemas with this connection, the user must be SUPERUSER on PostgreSQL.
To use the Giswater plugin it is necessary to have created a connection to the database that we will use to work. It needs to be created once for each installed QGIS.
Multiple connections to different databases are possible, although in this case it is recommended to work with caution to avoid mixing data between databases.
Once connected we can visualize the tables (with and without geometry) that contain the corresponding database and, if necessary, add them to the project.

## 2.4 Downloading and first steps with Giswater plugin.

In previous versions, Giswater was composed of an application, which acted as a driver for the configuration, creation, and management of the different projects on the database, and a plugin based on QGIS for the exploitation of network elements.
Starting from version 3.## 2, it will only be necessary to install the plugin in QGIS to develop all the before mentioned functions.
In order to download the plugin, the URL of the repository is needed:
The latest realease and repository’s URL can be found on the Giswater website, where is also possible to access the older versions of the plugin.
DOWNLOADS
GISWATER
From the downloads tab it’s also possible to access the information about the product, the benefits of using open-source software, the expert’s community who develop Giswater and get the materials and tutorials to learn how to use it.

### 2.4.1 Installing the plugin in QGIS

To install and connect the Giswater plugin with QGIS, it’s necessary to configure a new repository, which will allow viewing the Giswater plugin in the plugin list. For this we must follow the following steps:
1. - Open QGIS and access plugin repository (Plugins).
2. - Access the tab of Settings and add a new repository.
To add the Giswater plugin to QGIS, look for it in the Plugins tab
3. - Introduce the name and identify the repository and URL.
The repository is added manually, using a URL.
4. - Find and install Giswater plugin from the tab ‘All’.
 We can always see the version of the plugin that we currently have installed and the version available in the repository.
Warning: If we want to update the plugin to the most recent version, it can be done, but this may have implications that we will see later.
The Giswater plugin tool should appear on the Plugins toolbar. If we do not have it activated, we will have to do it through View> Toolbars> Plugins.
If, when installing the plugin for the first time with satisfactory results, the Giswater button in the Plugin toolbar does not automatically appear, we must close QGIS and open it again.
In case of having more than one QGIS project open, the behavior of the plugin may present instabilities, so it is recommended not to use the plugin with more than one QGIS project opened.

### 2.4.2 General project management tool.

This is the tool that a Giswater user should know while starting to work with it. Unlike the other buttons that the plugin incorporates, it is in the general toolbar next to the other buttons of different plugins installed or specific to QGIS.
Most of the functionalities of this tool will only be executed if we open QGIS without any Giswater project (we understand by Giswater project a project that has at least the representation layers of nodes, arcs, connecs of a database schema).
In case of initialization and the first steps with the plugin, we must know how to use this tool to perform all its functionalities:
Generate new working schemas (directly in the database)
Show the existing schemas
Update and edit existing schemas
Provide information about the selected schema
Only when the connection is using a SUPERUSER of PostgreSQL will be possible to create new schemas or update it.
Main form of the general project management tool

### 2.5.1 Creation of an empty schema

Using the general tool of project management, that was just presented in section ## 2.4.## 2, we are going to create a basic template of the working scheme in the database, which can later be opened and edited as a QGIS project. By referring to an empty schema, it does not mean that there is no full data in the tables, but that the data of a specific network are not, however, we will find common and system values that any Giswater work schema must necessarily incorporate.
The first thing we must keep in mind is that this tool, in its first drop-down list called Connection name will show all the PostGIS connections that are created in our QGIS. In section ## 2.3 of this manual, a connection with the name Giswater was created, so this connection appears as available in the tool (Image below). We will then have to consider the connection parameters that we have given in order to know which database the tool will attack and therefore where we are going to generate the new template.
Knowing which database calls the connection, click Create to open the configuration form for the new work scheme.
 Schema creation form. With Empty data selected, we will create an empty schema.
After clicking Accept, the schema will be created, and the program will let us know about its status:
We can also see in the database, through pgAdmin, that the manual_ws schema has appeared with the functions, sequences, tables, triggers, and views that contains a Giswater template for supply networks.

#### 2.5.1.1 Basic configuration of an empty schema

There are many types of tables within all those created in the previous section. There are some that are already filled by default, others that will be filled in as elements of the network are created and there are tables that can be customized by the users, depending on their needs and those of their network.
The basic tables that match the main generic elements of any Giswater project are of great importance and must be considered in order to explain this section. They are the following:
Arc
Node
Connec
Gully (only for UD)
These four tables are empty and will only be filled when our project has geospatial elements of the corresponding type, but they have certain restrictions when filling them and relationships with other tables that must be met.
For any user who wants to customize the types of elements, a consult to a pretended table should be done and modify according to their liking.
cat_feature
This table serves as a catalog for all items of the various types. In any created scheme we will already find values, but we can easily change names, add or delete rows.
Each element that exists in cat_feature must be part of an element type (feature_type), which can be NODE, ARC, CONNEC or GULLY, and in addition to another type within each of the previous ones, specified in the sys_feature_type table (not modifiable by users).
Each user can customize the cat_feature table with specific elements that are necessary for their network, as long as these are related to one of the fields of sys_feature_type (for example, TANK or FOUNTAIN) and with one of the existing feature_type.
In a lower order of hierarchy of tables that determine the existing elements, we find the catalog tables (see section 4.## 2.1.1), which must be filled in by relating each new element, with a name to suit the user, with any of the existing ones in cat_feature.
cat_node
cat_arc
cat_connec
cat_grate (UD)
If in these last catalogs you want to add values for the material columns, it will also be necessary to previously fill in material catalogs:
cat_mat_arc
cat_mat_node
Then there are other interesting tables for adding custom value domains:
man_type_category
man_type_fluid
man_type_function
man_type_location
In these tables we can add specific information about the type of category, fluid, function or location related to the different types of basic elements (arc, node, connec, gully). Each of the tables has the following fields:
id
serial
Numeric auto identification (primary key)
*_type
varchar (50)
Field to put our information that will be used in the arc / node / connec / gully tables
feature_type
varchar (30)
Type of element to which the value is assigned
featurecat_id
varchar (30)
It allows us to detail more in each of the large categories
observ
varchar (150)
To add additional information
*category/fluid/function/location
To give an example of the use of these tables, we could define a domain catalog of custom values for a tank (deposit) in addition to the one that would correspond to it for node.
For information purposes, but it is important to know, these fields are managed by the database using foreign keys to guarantee the consistency and uniqueness of the information. As you can already guess, the foreign key has special characteristics to govern this system of different values depending on the source table. One of the most important characteristics is the duplication of the foreign key.
This means that, to give an example for the node table, and regarding the type of fluid, the double key is managed in such a way that only those values of fluid_type in the man_fluid_type table that meet the condition will be available in the node.fluid_type field. that have the field feature_type = 'NODE'. 

This double foreign key guarantees that the information is consistent at all times, avoiding insertions that do not meet this criteria and propagating changes in the event of renewing or deleting value domains.

### 2.5.2 Creation of a sample schema (sample)

To facilitate the first steps with Giswater and have a complete data model that serves as a reference source, Giswater has incorporated two example schemes, for both urban drainage and water supply networks.
Having a first complete data model, apart from serving as a query source to see how the data is structured within each of the tables, will allow to start with a test environment and practice all the features that the Giswater plugin contains.
In order to create the sample, repeat the previous steps of creating an empty schema, explained in the section ## 2.5.1., but when the time comes to create the schema, you will have to select Example data instead of Empty data.
We will automatically have a Giswater sample project created with all kinds of information and sample data to see its functionality at maximum performance. With the giswater 3.## 2 plugin, the example schema can be given whatever name the user wants, unlike previous versions where the name was necessarily ws_sample and ud_sample.
Create new schema form. By selecting Example data we will create the sample schema

### 2.5. Creation of QGIS projects.

With the general project management tool, apart from creating the schemas within the database, we also can automatically generate projects for QGIS, specifically designed to work with database tables, as well as designed with symbology that allows the project data to be viewed in the most comfortable way possible.
To create these Giswater project templates, we must click on the Create GIS project button in the initial form of the tool.
General project management form. With the Create GIS Project button we obtain a project template in QGIS.
In the small form that will be opened next, we must choose the type of project that we are going to create based on a role. Later in this manual (section 3.5) it will be explained which are the roles that Giswater manages, as well as their characteristics and properties, but for now all we need to know is that the number of layers loaded in the project will be different depending on the role that we choose and, in the same way, the number of functionalities that we can carry out with the plugin will also be modified.
We recommend that, for users who do not use Giswater in a corporate environment, they always choose the admin role to enjoy all the plugin's features.
During the creation of the GIS project, we must also choose a name for the qgs file and a folder where to save it.
Finally, if we want this project to be opened without having to enter the access credentials to the database, we have the possibility to mark Export user password, so that the created file will directly store these credentials and we can open it without having to enter user and password.
By clicking Accept, the file will be created, and we will be ready to open it.
We must bear in mind that, when creating a GIS project:
• For an empty schema we will not see anything inside the QGIS map, and we will have to manually add the data. If what we want is to start drawing our network and enter data from scratch, we will have to follow some specific steps, as there are certain mandatory work rules that will be discussed throughout this manual. In section 6 we will find a brief practical guide on how to digitize a network starting from scratch.
• For an example scheme we will directly have a network with all the data filled in to be able to test the functionalities of the plugin.
• You can also try to import a .inp file from an existing EPA hydraulic  model , to see how it looks in GISWATER, for this we advice you to take a look on  Import inp file debug mode on GitWiki for more info.