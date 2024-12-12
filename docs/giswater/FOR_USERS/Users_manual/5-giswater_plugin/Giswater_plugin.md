<script>
    var style = document.createElement('style');
    style.innerHTML = `
        .wy-nav-content {
            width: 100% !important;
            max-width: 100% !important;
            margin: 0 auto !important;
        }
    `;
    document.head.appendChild(style);
</script>

# 5. Giswater Plugin

## 5.1 Plugin tools

One of the biggest and most notable improvements of the 3rd version of Giswater, comparing to previous versions, can be found in the plugin tools. Not only have new capabilities been added, but existing tools have been enhanced one by one.

The Giswater plugin is the part of the software with which the user should become more familiar since most of the actions that he wants to carry out can be done using the tools available in the plugin. In one way or another, everything you want to do on your network can be done using the plugin and the buttons it incorporates.

Giswater currently has up to **38 tools** available, divided into different toolbars that must be associated with the six roles that exist in Giswater. In addition to these management tools within the projects, starting from the version 3.1.105, a button has been incorporated that includes the functionalities of creating, modifying, and updating schemes.

Button apart from the plugin toolbars:

![figure 1](images2/figure1_toolbar.png)

Next, the functionality and objective of each of the tools will be detailed, apart from the general project management tool that was already explained in section **2.4.2** of this manual.

## 5.2 Toolbars

### 5.2.1 Basics

This group of consulting tools is related to the basic role of Giswater. They are tools that allow to select and consult the data, but still without the capacity to modify it. Even so, its use is especially important, since the fact of selecting one or another parameter, for example, the states of the elements, will modify the behavior of other tools.

5.2.1.1 Info
![figure 2](images2/figure2_info.png)

The Giswater info button allows you to make an 'info' on the different elements of the supply and sanitation networks.

As a result of using this button, the info will return the custom form of the selected element. In addition, it is not necessary to have the active layer of QGIS that contains the element that we want to select.

This button will only work with the following layers of the ToC:

* v_edit_node
* v_edit_arc
* v_edit_connec
* v_edit_gully
* v_edit_om_visit
* v_edit_dimensions

**Those elements have** also an associated form, designed one by one according to their specific attributes fields. When using this tool, a form of the element will appear in your window, and you will be able to have access to more detailed information, distributed in different **tabs** according to their category. In general, forms are similar. The example of the image below represents the different parts of a form of a Node Element (manhole) of a UD project.

| ![Figure 3](images2/figure3_manhole.png) |
|:------------------------------------------------------------------:|
| *Attribute form of a Manhole type element. Most of the element forms are very similar to this one, which serves as an example to see the distribution of the different attributes and tabs.*|

**Forms of the elements**

* **Data**: information related to the element's own attributes. In the tables located in the annex of the manual, you can check the fields that each element has, which should be shown in this tab of the form. It is also distributed in different sections.
    * Main data: basic information common among most elements, such as start dates, codes, soil, elevations, and depths, etc.
    * Additional data: additional information of the element. It contains the address data and optionally added information.

![figure 4](images2/figure4_connections.png)

* **Relations**: shows a table of other elements that are linked only to this element. They are usually not connected to the network, as the main element must be large enough to contain its related elements. The relations, depending on the type of project and the type of element, can be:

![figure 5](images2/figure5_relations.png)

* **Element**: in this tab other elements are shown, not connected to the network, which are linked to the element that we are visualizing. From the form itself, you can link, unlink, and add elements of this type.
* **Hydrometer** (***only for connec type elements, WS schemas***): relates connections with hydrometers and can show their values, besides connecting or disconnecting them. 
* **Document**: this tab shows the documents related to the element which is being visualized. Documents can be linked, unlinked, and added from the form itself, as well as categorized by date and document type. 
* **O&M**: the events related to the element we are viewing are shown. Each event is part of a visit, which can be consulted using a button within the form. You can also add visits, view photos and documents related to the events. 
* **Scada** (***only for node type elements***): related to the values that come from the SCADA system for the element we are viewing.
* **Cost** (***only for node and arc type elements***): allows to calculate the cost of the element which is being visualized. For node-type elements, only two parameters come into play (price per unit or price per meter of depth). For arc elements, there are many more variables that are necessary when calculating the price and they are all specified in this last section of the form.

!!! info "If you want to make info from any other layer, you will have to use the usual QGIS info."

**5.2.1.2 Selector**
![figure 6](images2/figure6_selector.png)

The selector tool groups in a single button the different filters that can be applied to the visualization of the network.

Allows you to filter by:

* Explotation
* Network state (OBSOLETE, IN SERVICE, PLANNED)
* Customer state (hydrometer tables)
* Existing planning sectors
* Hydraulic Sectors (to send them or not to the generation of the hydraulic model)

Its use is quite simple; You just have to go to the desired tab and select the values that we want to see or stop seeing. Automatically in our canvas we will see how entities appear or disappear depending on the filters applied.

| ![Figure 7](images2/figure7_map.png) |
|:------------------------------------------------------------------:|
| *Tool form, which can be opened in the middle of the screen or dockerized on the right side of the screen (as in the example). In the different tabs we can operate with the filters.*|

**5.2.1.3 Searcher**

![Figure 8](images2/figure8_search.png)

The Giswater search engine allows to search and select elements of the network or the address. There are five different tabs within the search engine, each with different search parameters.

We will see tab by tab the use of the searcher:

![Figure 9](images2/figure9_tab.png)

* **Network** *(network elements)*: allows to search for specific elements of the network. First the type of element must be selected, and then write what we want to search for, either the id or an element type. In the drop-down all the available ones will be filtered showing their id and catalog. Selecting one of the filters will zoom to the element, which will be centered in the middle of the interface. It works with the project system layers, which is a reason to always have them loaded in the project.

![Figure 10](images2/figure10_network.png)

* **Hydrometer**: it allows to search for hydrometers, which must always be related to connecs. In the first drop-down list the exploitation we want must be selected. Then, it is possible to search among all the hydrometers of that exploitation. The *hydrometer_customer_code*, *connec_customer_code* and hydrometer *state* will be displayed. When selecting a record, the tool will automatically open the hydrometer form and will zoom in to the corresponding connec. All the parameters that are used in this browser tab are customizable by the user in the *config_param_system* table.

![Figure 11](images2/figure11_address.png)

* **Address**: the third tab of the searcher is related to the street map, loaded in the last group of Giswater layers. It allows to search for municipalities, streets, or specific portal numbers. To use it, the fields of the *ext_municipality*, *ext_streetaxis* and *ext_address* tables must be correctly filled out. First you will have to choose a municipality in the *Municipality* drop-down. You can then choose a street in the *Street* drop-down. Selecting a street will zoom to its extension. Finally, with the street selected, you can choose a street number from the *Number* drop-down. Clicking on a specific number will zoom to the specific element, centering it on the screen.

![Figure 12](images2/figure12_workcat.png)

* **WorkCat** *(work records)*: it allows to filter the elements of type *node*, *arc*, *connec*, *gully* and *element* according to the work record to which they belong. In the drop-down list, the user can choose a record and after clicking on it, a form containing two tabs will automatically open. The first contains the elements that have the work record selected as the start record. In the second, those who have it will be displayed as a withdrawal file. By clicking on any row of the tables we can open the specific form of the element. In the lower part of each table a summary of the table is added, showing the total of elements of the same type, as well as the total length of the arcs that are part of the selected work record.

In addition, in this window it is possible to export the information presented in the tables into csv file. To do this you only have to set the save path and click in the *Export to csv* button.

On the map, we will draw a polygon that indicates the limits of all the elements of the network related to the selected work record, to which we will zoom. When closing the form, this polygon disappears.

| ![Figure 13](images2/figure13_polygon.png) |
|:------------------------------------------------------------------:|
| *Work record searcher form. It allows to eexportingxport the information to csv.*|

![Figure 14](images2/figure14_psector.png)

* **Psector**: The last tab of the searcher allows to search for the different planification sectors generated in the project. The use is quite simple: you just have to choose the name of the psector that we want to find in the drop-down tool. When you click, the form associated with the corresponding psector will automatically open, where we will have the possibility to edit the information, see the linked elements, add prices or documents, etc. The searcher also zooms to the geometry of the specific psector.

### 5.2.2 Operations and management

This group of tools is designed to perform or simulate actions on the actual network of water supply or urban drainage. Some of them will be used directly from the location of the element in the field, to report information on its status at the same time, others from the office, but always focused on the actual use of the elements.

This O&M toolbar is the only one of the plugin where there are big differences between WS and UD projects. There are some tools that are only for water supply and others that are exclusive for urban drainage. As usual, a clear distinction will be made when detailing the operations.

However, there are several common tools in this toolbar, such as those related to the management of visits and events. The visits to elements are made by a worker in the field, who can add the information directly to the tables specially designed for this function through a mobile device.

**5.2.2.1 Minimum Cut Polygon**

![Figure 15](images2/figure15_polygon.png)

The mincut polygon functionality is surely one of the most important that a drinking water network manager needs to operate for its daily functioning. In this section it will be explained how the internal work logic of the database is developed.

The mincut polygon propagates flows from the elements that supply water to the network and then proposes the valves that should be closed in case of wanting to leave a specific point without water supply.

First, there are several **previous aspects** about the data that are strictly necessary for the tool to work correctly:

1. *Pgrouting* library is used for this process.
2. All *arc* and *node* elements must have *state* and *state_type* fields filled. The state type must be one that is operational. This can be seen in the *value_state_type* table in the *is_operative field*, which must be TRUE. In case of FALSE, the element will not enter the cutting polygon process.
3. The network traceability is made from the node_1 and node_2 of the elements type arc, that is why the network must have topology.
4. The identifiers (*id*) of arcs and nodes must be *integer*.
5. The table *man_valve* must have filled in the values *closed* and *broken* fields, which by default will be *FALSE*.
6. The cutting polygon works in the context of the exploitations system defined by the user in the table *config_graph_inlet*. This table must define exactly which are the nodes that provide water to the system (usually source or tank) and to which exploitation they belong.
7. The type of valves that participate in the cutting polygon must be configured. This can be done from the table *config_graph_valve* or through the *plugin*. Usually, they are only the shutoff valves.
8. For mincut there are three different types of states (not to be confused with the states of the elements of the network). These are defined in the table *om_typevalue* and are:

| typevalue     | id  | idval       |
|---------------|-----|-------------|
| mincut_state  | 0   | Planified   |
| mincut_state  | 1   | In Progress |
| mincut_state  | 2   | Finished    |
| mincut_state  | 3   | Canceled    |
| mincut_state  | 4   | On planning |

Once all the mentioned aspects are controlled the tool can be used. Clicking on the button opens the *mincut* form, where, in the first place we should pay attention to the top toolbar. Here it is possible to distinguish the *mincut* types and the configuration of the tool. In the configuration the types of valves that enter process can be selected.

| ![Figure 16](images2/figure16_hydrometer.png) |
|:------------------------------------------------------------------:|
| *Toolbar of the mincut form. From here it is possible to select the type of polygon that will be performed.*|

As showed in the image above, there are three types of mincut polygon. The one with the most developed functionality is number 1, which proposes the valves to be closed to leave a specific location without water supply.

How to use the three types of mincut:

* ***Network mincut– Class*** **1**

To make a mincut polygon of type 1 the form must be filled (image below) with the different parameters:

* Work order: work record (optional).
* Street map: situation of the point that won’t have water (formed by the fields municipality, postal code, street and number).
* Type: may be demo, real or test, depending on whether the water cut is going to take place or is just a test to see which would be the results.
* Cause: Accidental or planned.
* Start and end date: in this case they are to make a forecast.
* User: name of the user assigned to this process.
* Description: to add additional information in text format for the specific case.

Now the state of the cutting polygon will be planned, but, as we will see, the state is automatically modified depending on the process. At this moment it is time to click the button that will allow to choose the point of the network where the water will be cut.

With the cursor we must be placed over the desired point, which can be either an arc or a node. By clicking, the cutting polygon will be automatically made, which should show the valves that will have to be closed and all the elements that will be affected (sections, nodes, and connections).

| ![Figure 17](images2/figure17_mincut.png) |
|:------------------------------------------------------------------:|
| *Form of the cutting polygon, the same for the three types of polygon. This has different functions and fields that will be activated or not depending on the state of the polygon*|

To offer this information mincut has different tables where the results are stored depending on the type of element:

![Figure 18](images2/figure18_mincut.png)

| ![Figure 19](images2/figure19_map.png) |
|:------------------------------------------------------------------:|
| *View of the map with the cutting polygon made. The symbology clearly shows the valves to be closed, as well as the affected sections, nodes and connecs.*|

All these tables store the information of the element and the identifier of the cutting polygon and allow to clearly visualize on the map the affectation of the process, as shown in the above image.

At this moment, the second button of the mincut toolbar is activated, which will allow, optionally, to choose a valve that for whatever reason will not be able to be closed. By clicking on the button, we choose the valve, and the results of the process will be recalculated considering the modification.

With the completed polygon and knowing that all the marked valves can be effectively closed, it is time for the second tab of the form (Exec). By clicking on *Start*, the rest of the fields will be activated, the start date and time will be set, and the process status will change to *In Progress*. We can add an additional description during the process and other fields such as distance from the building or depth.

If it is a *mincut* test usually the duration will be noticeably short, as we only want to see the affectation; on the other hand, if the *mincut* is real, we can click *OK* and leave the process in this state until, when the time comes, by clicking *End* to finish and change the state to *Finished*. By clicking *End* opens another small form to specify, if necessary, the location and dates of the process. By clicking *OK* in this last form, this cutting polygon will be permanently closed and stored without the possibility of editing it again.

| ![Figure 20](images2/figure20_settings.png) |
|:------------------------------------------------------------------:|
| *Form fields that are only activated when the polygon has started.*|

* ***Connec mincut – Class 2***
To perform a type 2 mincut, in the same way as in 1, the form must be filled in with the location, dates and *mincut* details. Then, click in the button to start the process:

At this moment, a small form is opened that will allow to select the connections to which the water supply will be cut (Image below).

| ![Figure 21](images2/figure21_mincut.png) |
|:------------------------------------------------------------------:|
| *Form to choose the connecs that will be affected by the mincut.*|

To select them we have two options:

![Figure 22](images2/figure22_plus.png)

The button (-) allows to unselect the connections.

Once selected, we click *OK* and these will be stored as connections to be cut for the *mincut* that we have in process and they will be able to be visualized in the map through the *Mincut result conne*c layer.

In the same way as for the *Network mincut*, at this moment the state may be modified. It can be left as planned, it can be started and left as in progress or finished.

Although this type of mincut polygon does not provide as much information as type 1, it is also important when planning network operations in cases where valves do not have to be closed, but the connecs will be.

* ***Hydrometer mincut – Class 3***

This last type of cutting polygon is similar to the previous one, but with an added level of detail. In this case, the hydrometers that are going to be closed are identified. It is useful for cases in which not all the hydrometers of a connection must be closed.

The flow of use is the same as in the previous case, but in this case the selection form has two filters: one for connections and another for the hydrometers that this one contains.

Since the hydrometers do not have geometry, it will not be possible to visualize the results on the map, but they will be stored in the *Mincut result hydrometer* table.

**5.2.2.2 Mincut manager**

![Figure 23](images2/figure23_manager.png)

The mincut polygon manager complements the *mincut* tool. The goal of this tool is to store the different cutting polygons made in the project and allow the user to recover and visualize again the data referred to the existing polygons.

When we open the tool, we will be able to see a form with a central table where the polygons made are shown in rows, whatever their status (planned, in process or finished). Each row offers most of the information of the cut polygon: type, dates, street map, cause, start element, etc. The capabilities of the tool are as follows:

* Filter by *id, state, date, and exploitation*
* View the planned mincuts for the next days
* Delete selected *mincut*
* Open selected *mincut*: When opening a cutting polygon, we will be shown its form and, if it is not finished, we can edit the data. At the same time, the mincut results tables will be updated with the data of the selected process and therefore we will be able to see them again on the map.
* *Mincut* selector: Next to the filter by *mincut_id* button there is a button that opens the mincut selector. After clicking, a selector will appear, allowing to see on the screen different cutting polygons at the same time. Consider that by having different polygons in the selector, the tables where the data is stored will also have more information differentiated by the *mincut_id*.

| ![Figure 24](images2/figure24_settings.png) |
|:------------------------------------------------------------------:|
| *Cutting polygon manager form with selector open.*|

**5.2.2.3 Longitudinal profile**

![Figure 25](images2/figure25_profile.png)

The longitudinal profiles are technical representations of a part of the urban water drainage system. This tool automatically creates longitudinal profiles of the area that the user wants. To choose which elements should be represented, the user must select a start node and a final node. The longitudinal profile will represent all the arcs and nodes that are between these two nodes (including themselves). In addition, there is an option of selecting an additional node which, in case the initial and final nodes have two possible routes, will mark the direction by which the profile should be drawn.

By clicking the button that starts the tool, a form like the one in the next image will open. Here the user can, optionally, establish a profile id. With the button in the bar at the top of the form, you can choose by standing on top of one and clicking, and then do the same in the second. Once we have values for these nodes, we will see how the sections located between the nodes appear in the list, which will also be selected on the map. Inside **Parameters** we can establish:

| ![Figure 26](images2/figure26_profile.png) |
|:------------------------------------------------------------------:|
| *Form to make a longitudinal profile. Allows you to select the start and end nodes to then run the profile.*|

* Vnode Min Dist: minimum distance between connections to be represented in the profile. If it is left as empty, all will come out.
* Title: title of the profile.
* Date: date for the profile.

At this time, we will be able to click the *Draw* button to create the desired longitudinal profile. The *Clear profile* button deletes the data we have selected.

The representation is a graphic type with a table of dimensions in the lower part. It shows the following data:

* Elevation and maximum elevation of the node
* Y max of the node
* Material and diameter, slope, and length of arc
* Data from the connections that arrive to the arcs
* Mentioned title and date

This is an especially useful tool to obtain a graphic representation of the network in a quite simple way. It should be remembered that if any of the essential fields for drawing the profile is empty, the tool has customizable default values in the *config_param_system* table. These values are:

* top_elev (node) / sys_elev (node)
* *ymax (node)*
* *geom1 (cat_arc)*
* *z1 / z2 (cat_arc)*
* *cat_geom1(cat_node)*
* *sys_elev1 / sys_elev2 (arc)*
* *y1 / y2 (arc)*
* *slope (arc)*

In addition to drawing new longitudinal profiles, the tool allows to load existing ones. To keep a profile registered it must be saved using the *Save profile* button. All the ones which are saved can be displayed again by clicking *Load profile* through the main form of the tool.

| ![Figure 27](images2/figure27_graph.png) |
|:------------------------------------------------------------------:|
| *Example of longitudinal profile with the information displayed on the different selected nodes and sections. In this case no connections are shown because Vnode Min Dist is set to 50.*|

**5.2.2.4 Upstream**

![Figure 28](images2/figure28_upstream.png)

This tool, specific for sanitation projects, allows the user to select a specific **node** of the network and show all the elements that are upstream of the chosen node. To show these elements, the tool selects all of them (by painting yellow) and it is possible to visualize them both in the graphical interface as well as in the attribute tables (where they are also selected).

| ![Figure 29](images2/figure29_dmap.png) |
|:------------------------------------------------------------------:|
| *Elements located upstream from the selected node. On the image of the right, the error is shown, because of the inverse direction of one of the sections and that’s why it’s not detected as upstream.*|

**5.2.2.5 Downstream**

![Figure 30](images2/figure30_downstream.png)

This is the same process as the previous tool (upstream), but this time selecting elements which are located downstream from the selected node.

To make this selection, the tool searches in the nodes contiguous with the selected its maximum height and in case when it is higher (for upstream) or lower (for downstream) it selects it and continues the search until the end of the network. One of the goals of this tool is to help find errors in the network, since the elements upstream or downstream must have a coherence of heights so that water flows through the conduits. If the *top_elev* field of a node that should be upstream is smaller than its predecessor, the tool will stop, and it will not be selected. This can be understood more easily in the two images above, as on the right the section that should be upstream is not selected, therefore, there might be a problem with the heights. The one from the left it is shown as correctly selected.

**5.2.2.6 Add multiple visit**

![Figure 31](images2/figure31_visit.png)

This tool allows adding a new visit to our network, following a process in which said visit can be linked to one or more elements of the network, adding the events that have occurred during the visit and selecting documents from your computer to be related to the visit. By clicking on it, we are shown a form with four tabs:

In the first one, we can fill in the data of the new visit that we are going to create. Before doing so, it is necessary to have at least one value in the visit catalog (*om_visit_cat*), since each visit must be related to a value in this table. Only visit catalogs with *active=TRUE* will be available in this drop-down. Other data that are added are those related to the start and end dates of the visit, an external code for its management. Finally, it will be possible to establish whether the visit has specific geometry or is an alphanumeric record. With the *Add geom* button, the location of the geometry is assigned on the map (Image below).

| ![Figure 32](images2/figure32_visita.png) |
|:------------------------------------------------------------------:|
| *Visit insertion form. In the first tab the basic data is added.*|

The second tab relates the visit to events (Image below). As has been said, different events can be part of the same visit. These are actions carried out during the visit, such as repairing a crack or cleaning a section of pipe. The first dropdown is populated with the parameter types, which can be configured in the *om_typevalue* table (typevalue=visit_param_type). The second and third dropdowns are configured in the config_visit_parameter table, where each parameter must be related to its parameter type and a feature type (or all through ALL). Then we can insert events and add values to them.

| ![Figure 33](images2/figure33_evento.png) |
|:------------------------------------------------------------------:|
| *Visit insertion form. The second tab relates visit to events.*|

The third tab of the form refers to the relationships with elements of this visit. If we wish to link new elements to the visit we are creating, we can do so with the tools on this tab. It allows you to filter by type of element and add by id or by selecting directly on the map (Image below).

| ![Figure 34](images2/figure34_relac.png) |
|:------------------------------------------------------------------:|
| *Visit insertion form. The third tab establishes the relationships with elements of the network.*|

Finally, in the last tab of the form, visits can be related to documents (Image below). These are external documents in ‘common’ formats such as *pdf, doc* or *csv*. In the text space it is possible to filter existing documents and link them to the visit. In case the user wishes to add a new document at this moment, it is possible to do so by clicking in the third button which appears in the tab.

This performs the same function as the *Add Document* plugin tool, which will be explained later.
The other button allows to open the URL of the selected document.

| ![Figure 35](images2/figure35_documento.png) |
|:------------------------------------------------------------------:|
| *The last tab allows you to link documents with the multiple visit.*|

**5.2.2.7 Visit manager**

![Figure 36](images2/figure36_manager.png)

When opening the *visit manager*, a form with a table containing all the visits made and some of their data is shown. This tool allows to select a visit and open or delete it. The user is also allowed to filter visits by date.

| ![Figure 37](images2/figure37_visit.png) |
|:------------------------------------------------------------------:|
| *Ima Form of the visit manager. Here all the available visits are shown and might be filtered by date.*|

**5.2.2.8 Date selector**

![Figure 38](images2/figure38_date.png)

This tool allows the user to establish the value for the dates of operations and management.

By clicking on it, a small form opens where it is possible to select a start date and a final date, which will be used later for other processes. This information is stored in the *selector_date* table and will be replaced as the user uses this tool and modifies the values. The table allows only one set of date type values for each user, so that the same user can not have several dates available, only the last inserted value.

| ![Figure 38.1](images2/figure38.1_date.png) |
|:------------------------------------------------------------------:|
| *Date selector. The data inserted in this form will be used to set the dates of other processes.*|

The purpose of this tool is to simplify the use of dates of visits. If a user wants to create a view related to operations and management, he can filter the date fields using those in the *selector_date* table, and it will be quite easy to update the values and use them as default dates. It is designed to establish values such as the following month or this week and use them in different scenarios.

To give an example of the usability of the tool, we will see how to generate a customized view that can be updated from the date selector. We create a view that shows us the valves, their geometry, and their construction date:

![Figure 39](images2/figure39_sql.png)

To visualize the results, we must load the view to our QGIS project. This view will be automatically filtered based on the value we put in the date picker. For example, if we select the dates from the beginning of the year 2010 to the present year, the view will only show us the valves with a discharge date (builtdate field) that are between these dates.

To sum up, any table that has date values can be filtered through this tool, thus achieving a quite simple method of representing information according to the needs of the user, who can customize the view.

### 5.2.3 Edition

The toolbar related to editing the network is the largest one. These tools are intended to facilitate the insertion, elimination, or modification of existing data, especially in relation to geospatial elements. This includes basic tools for adding nodes or arcs, moving elements, or connecting them together, as well as another block of tools to establish relationships with documents or additional elements.

**5.2.3.1 Insert node**

![Figure 40](images2/figure40_node.png)

It is a basic tool that allows to add a new node-type element to the network, both for water supply and sanitation projects. To perform the insertion there are two options:

1. Click on the arrow next to the button and select from the list the type of element we want to insert.
2. Use the keyboard shortcut to select the element type to insert. The shortcuts must be previously configured to use this function. To do so, we must fill the *shortcut_key* field of the *cat_feature_cat* table with the keyboard letter we want.

Once we have the type of node selected, we must place the position on the map that the new element will occupy. If we place the element in a place disconnected from the network there is no problem, but if we want to place it on top of an existing section (by *snapping*), we must consider whether it is a node that must break the section or not. This can be controlled from the *cat_feature_node* table, through the *isarcdivide* field. If this field is **FALSE**, the section where it is located will not be broken. In case of *isarcdivide*=**TRUE**, the section will be divided into two parts right at the insertion point. Here the rules of the state topology (**3.7.4**) come into play again: the insert will act in different ways depending on the state of the inserted node and the element on which it is located.

Once we have clicked on the site where we want to place the new node, the form related to it will automatically open. Here we must add the information regarding our new element. There are fields that are mandatory and therefore must always be filled to correctly insert; however, to facilitate quick insertion of elements, some of these fields can be filled in automatically thanks to the Giswater functionality. The exploitation, the dma and the sector of the new element will be captured directly in case the new element tries to be located within the limits of these zone layers.

The rest of the fields must be filled in manually or using some of the default values, which must have been previously configured.

Finally, by clicking OK will finish the edition and the new element will be inserted.

**5.2.3.2 Insert arc**

![Figure 41](images2/figure41_arc.png)

This tool allows to add a new arc to the network. The flow of using it is the same as of the insertion of a node, with the exception that in the case of arcs it must be drawn between two nodes. In case of not doing so, the insertion will be erroneous, since the topological rules says that an arc must have nodes at its ends. To draw an arc the first step is to click on the starting point and then draw different sections in desired direction until clicking again with the right button to finish the arc.

Once in the insertion form of the arc it is important to consider the differences that exist in some fields, since the arcs have specific attributes such as the length or the codes of the nodes. The other mandatory fields have the same usability as in the case of nodes.

| ![Figure 42](images2/figure42_pipe.png) |
|:------------------------------------------------------------------:|
| *General form of an arc-type element, specifically Pipe. Most item forms are similar, with some difference in the data they display.*|

Finally, by clicking the OK button, the edition is saved, and the arc is inserted.

**5.2.3.3 Replace node**

![Figure 43](images2/figure43_replace.png)

The replace node tool aims to change an existing node to a new one. To do this, Giswater changes the status of the node to be replaced to obsolete and places one back on the same site with a status of service. The user can choose the type of node with which he wants to replace the previous one, as well as modify its data.

When the tool button is clicked the cursor changes its appearance and allows to select the node that is about to be replaced. Once clicked on the item, a form opens where we should choose the element's withdrawal record, as well as the withdrawal date. If the work record that we want to add is not created in the cat_work table, we have the possibility of generating one again directly from this tool by clicking the […] button.

In the second part of the form there are the parameters of a node; here the current node type is displayed. At this time, the new node type must be selected together with its specific catalog (a drop-down list that refers to the *cat_node* table). If *Keep elements* checkbox is marked, the elements and documents related to the old node will be saved for the new one.

| ![Figure 44](images2/figure44_node.png) |
|:------------------------------------------------------------------:|
| *Form of replace node tool. In this example a filter is replaced by the air valve.*|

If we want to check the result of this tool, it can be done using the state selector and we will see one node in a state on service (1) and another in an obsolete state (0).

This is an especially useful tool because it facilitates the process of replacing elements in the network, without having to worry about the topology since its position is exactly the same.

**5.2.3.4 Divide arc**

![Figure 45](images2/figure45_divide.png)

This tool allows placing nodes that are disconnected from the network on top of arcs. In this process, the arc will be divided into two parts, which will inherit the data from the old arc, but with new identifiers. It can only be done one by one.

The image below represents an arc that is a part of a network and a disconnected node. If we want to move this node and place it over the arc, so that it becomes a part of the network, this tool must be used.

| ![Figure 46](images2/figure46_graph.png) |
|:------------------------------------------------------------------:|
| *The node 114451 is disconnected from the network. With the tool divide arc we will connect it.*|

We click the tool button and select the node 114451. Then we will have the possibility to draw an imaginary line towards the arc that we want to break and where we are going to place the node.

| ![Figure 47](images2/figure47_network.png) |
|:------------------------------------------------------------------:|
| *The tool allows to move the selected node just above the network section.*|

Finally, in the next image, we see how the node 114451 has been moved towards the arc and this has been divided into two parts, one with id 114536 and the other 114537. The old arc with id 2101 has been removed.

| ![Figure 48](images2/figure48_pipe.png) |
|:------------------------------------------------------------------:|
| *Node already connected to the network.*|

**5.2.3.5 Arc fusion**

![Figure 49](images2/figure49_fusion.png) 

This tool does exactly the opposite of the previous one; It allows to eliminate a node that divides a section and thus join two arcs into one.

One of the requirements of this tool is that the arcs must be of the same type and belong to the same catalog, i.e., the *arccat_id* attribute must be the same to join them. The node can only be related to two arcs so that the tool can correctly develop.

It is important to keep in mind that if the node to eliminate has a *TRUE* value in the undelete field, it will not be possible to eliminate it. To do so this value needs to be changed to *FALSE*.

By knowing this, the flow of the tool is quite simple: with the active tool we must place ourselves on top of the node that we are going to delete and when we click on it, a window will open warning about the elimination of the node. If we accept this, it will be deleted and the two arcs with which it was related will automatically join into one with a new *id*.

**5.2.3.6 Change node type**

![Figure 50](images2/figure50_node.png) 

The change node type tool allows to select an existing node and automatically modify its type and catalog.

To use this tool, click its button and then select the node which will be changed. After selecting, the modification form will open, where the current node type is shown and where it is possible to select the type by which it will be changed. The catalog of nodes will filter according to the selected type of node. By clicking *OK*, the change will be made, without modifying the rest of the element's data.

| ![Figure 51](images2/figure51_junction.png) |
|:------------------------------------------------------------------:|
| *Form of the change node type tool.*|

The usefulness of this tool lies in the fact that it allows modifying the type of node, a parameter that in the forms of the elements is not editable, in a quite simple, convenient, and fast way; without the need even to put into edition the selected node.

The Replace node tool and this one are similar; Replace node deletes the old element and inserts a new one one, with a new identifier. In contrast, this one maintains the identifier and does not cancel any element, it simply modifies its type.

**5.2.3.7 Connect to network**

![Figure 52](images2/figure52_connect.png)

As we already mentioned, the connections are related with the network, specifically to the arcs, through links, which draw a straight line between the connec and the nearest network section, where a virtual union node is located. The tool connect to network automates the process of creating these links and vnodes.

The goal is to connect to the network all connections that do not have a link. The tool allows to insert during one same process as many links as the user wants, which makes it an immensely powerful tool and very easy to use.

By clicking the button to start the tool, the cursor changes its appearance and allows to draw a rectangle, within which we must place the connections that we want to connect to the network.

| ![Figure 53](images2/figure53_connecs.png) |
|:------------------------------------------------------------------:|
| *Only the connecs inside the selection rectangle will be connected.*|

At this moment, the connecs will be painted in yellow (selected ones), but it’s still possible to draw another rectangle to select more connecs if we want, because those that are already selected will not be lost. It is important to know that to deselect connecs we can hold down the shortcut keys of *Shift + Ctrl* and draw a rectangle that will act in the opposite way to the selection. Once we have all the connections selected, by clicking the right button of the mouse, a message appears indicating the number of connections selected. If we click *OK*, links will automatically be drawn from the connections to the network and the virtual nodes will be inserted at the intersection point, just as shown on the next Image.

| ![Figure 54](images2/figure54_connecs.png) |
|:------------------------------------------------------------------:|
| *Connecs already connected to the network through a link.*|

**5.2.3.8 Dimensioning**

![Figure 55](images2/figure55_dimensioning.png)

The purpose of the dimensioning tool is to offer the possibility of calculating distances within the map, either in relation to elements of the network or with elements of the base map. It is also possible to use the tool in spaces of the map where there is no layer.

As has been mentioned in previous sections, the dimensions have a linear geometry layer that is represented on the map through a view (*v_edit_dimensions*). This allows that the values that are being stored can be represented on the map, offering additional information which may be valuable for networks with particularly accurate digitization.

How to use this tool? By clicking the button that activates it, the cursor will change and then we must click on the point where we want to start the dimensioning. Next, we must click on another site, so that a line appears joining the two points. If we want to finish the dimensioning at this point, by clicking the right mouse button will end the dimensioning. In case we want to make a dimension with more than one segment, we can continue drawing lines by clicking with the left button.

Once the line is finished, the form opens, where more data may be introduced.

| ![Figure 56](images2/figure56_dimensioning.png) |
|:------------------------------------------------------------------:|
| *Tool form, where we can enter the distance and depth data, as well as the coordinates where the symbology will be located.*|

If we know the distance of the dimension we are making, we can enter it in the Distance field. If we leave the value blank, the tool will calculate the real distance. If we know the depth at which we want to make the dimensioning, we must fill in the Depth field. Otherwise, we have the option to select a node or connec from the network and use its depth.

The tool offers different symbologies depending on the zoom of the project. In some cases, the dimension data is shown within a circle. With the button,  you can enter the coordinates where we want to place this circle.

In the two following images, we see examples of the different types of dimensioning symbology according to the project's zoom.

| ![Figure 57](images2/figure57_symbology.png) |
|:------------------------------------------------------------------:|
| *Example of circle symbology for dimensioning. At the top of the circle the distance of the dimension is shown; in the lower part the depth. Symbology programmed for small scales.*|

| ![Figure 58](images2/figure58_symbology.png) |
|:------------------------------------------------------------------:|
| *Example of symbology over the line for a dimension (same as in image above). This type of symbology is programmed for large scales.*|

**5.2.3.9 Add document**

![Figure 59](images2/figure59_document.png)

Many times, the elements of the network will be susceptible to having linked information found in documents external to the database and to QGIS. As has already been seen in other sections, this is possible with Giswater since the element forms have a specific tab where documents of all kinds can be added and linked.

This tool aims to link documents with one or more elements of the network, which can be opened and visible directly from the *plugin* and its forms.

By clicking on the tool button automatically opens the form to add a new document (Image below). Here the data of the document must be inserted: id, type, observations, and the link with the path of our computer.

| ![Figure 60](images2/figure60_document.png) |
|:------------------------------------------------------------------:|
| *First tab of the form to link a document to one or more elements of the network. The document information is added here.*|

Next, in the *Relations* tab, we select all the elements with which the new document will be related. Nodes, arcs and connecs must be chosen separately. They can be selected in the usual ways: with the buttons (+) and (-) they are added and deleted in the list of elements, through the *id*, and with the selector on the screen we can create a rectangle to select different elements at the same time.

In the example of the next image, the document is being added in this process, linked to the node with node_id 1019.

| ![Figure 61](images2/figure61_document.png) |
|:------------------------------------------------------------------:|
| *Second tab of the form, where the document is linked to the elements of the network.*|

To verify the correct linkage of the document with the node, the form of the *Junction element* can be opened, where, in the *Document* tab, the linked document with *doc_id* 1 should be present. By double-clicking on the row the document linked will be automatically opened.

| ![Figure 62](images2/figure62_document.png) |
|:------------------------------------------------------------------:|
| *The form of the item to which the document in this example is linked. Here we can check the correct link.*|

This example has been carried out with a single element, but it is just as easy to link a document to one as it is to many elements.

**5.2.3.10 Document manager**

![Figure 63](images2/figure63_manager.png)

The document manager is a tool used to inventory, visualize, filter, and delete all the documents that have been linked to any element of the network.

In the form that opens by clicking on the tool button, we can see a table with all the available documents, which shows the following data:

* Id
* Document type
* Path
* Observations
* Date
* User that added the document

With a double click over the row it is possible to open the specific document.

In the upper part of the form, the documents can be filtered based on their id. Next to the filter we find the button to delete the document that we have selected.

| ![Figure 64](images2/figure64_management.png) |
|:------------------------------------------------------------------:|
| *Document management form. All documents that have been linked to the network elements are displayed here and can be filtered, displayed, or deleted.*|

**5.2.3.11 Add element**

![Figure 65](images2/figure65_element.png)

This tool is reasonably like the *Add document* since they share the same goal of linking something with the elements of the network. The difference in this case is found in the type of object which is to relate; If an external document has been added before, now we are going to link other elements with the network, elements that can complement the information. In section **3.2** it has been defined that they are the elements and we also know that they have their own catalog, therefore, if we want to add a new element, we must relate it to one of those defined in the elements catalog (*cat_element*).

By clicking on the button to start the tool a form to add a new element will open (Image blow). Here the data of the new element must be entered, many of them are selectable in different drop-down lists. We also have the possibility to add the geometry of the element.

Once the data is entered, in the *Relations* tab, the new element must be linked with the other elements of the network (arc, node, connec) we want. To do this we can follow the same steps as the *Add Document* tool.

| ![Figure 66](images2/figure66_element.png) |
|:------------------------------------------------------------------:|
| *Form to add a new element and link it to another topological element.*|

**5.2.3.12 Element manager**

![Figure 67](images2/figure67_element.png)

The element manager, like all the management tools presented before, serves as an inventory of the elements found in the project. It allows to see all these elements and their attributes.

By double clicking on a selected item its specific form opens. In addition, there is an option to filter by the *element_id* field and delete elements with the *Delete* button.

| ![Figure 68](images2/figure68_element.png) |
|:------------------------------------------------------------------:|
| *Linked elements management form. Here you can filter, show, or delete elements.*|

**5.2.3.13 End feature**

![Figure 69](images2/figure69_feature.png)

This tool aims to remove elements from the network, i.e., change its status to obsolete. To do this, the elements must be on service. It is also necessary to consider the topology rules when deleting elements, since it will not be possible to do so if, for example, the selected node is connected to other arcs. The elements to be cancelled will have to be disconnected from the network.

In this case, Giswater permits an exception. The users can disconnect arcs that have associated connec-type elements, so that the arc will be disengaged and the related connecs will lose their link with the arc. This allows to facilitate the editing of the network in cases where it is necessary to cancel an arc and losing the relationship with the connec is not important. To prevent, the program will always show a list of all the elements that will be disconnected before proceeding.

By clicking on the tool button, the form to remove the item will open. First you must fill in some information about the withdrawal, such as the date or the withdrawal file (we can add one again directly). The next step is to relate the loss to one or more elements. In the *Relations* tab we can select the elements that we want to unsubscribe. Once selected and clicking *OK* will carry out the status change.

| ![Figure 70](images2/figure70_feature.png) |
|:------------------------------------------------------------------:|
| *Form of end feature. In the tab Relations it is posible to link one or many elements that will have their state changed to 0.*|

It is important to remember that the ‘ended’ elements will become obsolete, which does not mean that they will be eliminated. These will be equally visible if the obsolete elements are visible in the state selector.

**5.2.3.14 Delete element**

![Figure 71](images2/figure71_delete.png)

This tool aims to allow the user to completely remove an arc, nodes, connec or gully. Many times, the elements of the network have relationships between themselves and with documents or visits.

When a user tries to delete an element using the usual QGIS tools, he may run into problems, since the Giswater functionality does not allow deleting depending on what relationships exist. This tool allows eliminating, even if these relationships exist, **leaving the responsibility of the user that the network may be left with a broken topology**, since the tool allows breaking topology (simply eliminating a node that is as the initial or final node of a section).

By clicking the button, a form opens where we must select the type of element to delete. Next, using the selection tool, we must choose which is the element to eliminate. The tool only allows you to *work one by one*.

With the element selected, we must click the button 'Show element relationships', which will show us all the links that the element has, either with other elements on the network or with visits or documents. This can help us decide if we really want to eliminate it, since we are going to lose all these relationships.

If we are convinced of deleting, to finish the process we must click the button 'Delete selected item'.

![Figure 72](images2/figure72_borrar.png)

**5.2.3.15 Draw a circle**

![Figure 73](images2/figure73_circle.png)

Draw a circle is the first of the two CAD tools that Giswater has. They are grouped within editing role, although they are in a small bar separated from the rest of the editing tools.

The goal of this tool is to draw a circle around a specific point with a radius set by the user. This circle should serve to draw support points when digitizing the network.

To facilitate the use of this tool it is necessary to have configured the snapping of QGIS, since it will only be possible to draw circles using as reference elements configured in the *snapping*.

When clicking the tool button, the cursor will change shape and then we must place it above the position where we want to put the center of the circle. Next, the program will give us the option to establish a radius for the circle; When we enter this value, we must click *Accept* and the circle will automatically be created.

| ![Figure 74](images2/figure74_circle.png) |
|:------------------------------------------------------------------:|
| *Form in which the radius of a circle should be entered.*|

This circle and the rest of the elements that are generated with the tool will be stored in an auxiliary view of the database (*v_edit_cad_auxcircle*). If we consider that the view already contains too many unnecessary elements it is possible to eliminate them by clicking the *Delete previous circles* button and so the view will become empty at the end of the insertion of the new circle.

Knowing the radius of the circle and using its geometry as a reference, thanks to the snapping, we can insert reference points that will help drawing new elements in exact locations.

| ![Figure 75](images2/figure75_circle.png) |
|:------------------------------------------------------------------:|
| *Example of a circle generated with the tool. In the form of the previous image, we introduced the radius of 5 meters that we visualize in this image.*|

**5.2.3.16 Add relative point**

![Figure 76](images2/figure76_point.png)

The second CAD tool of the Giswater plugin is the one that allows inserting a point element at a distance (x, y) relative to another point on the map. The point of support generated should serve as a reference to draw new arcs and nodes of the network.

To add a new relative point using this tool, we must click on the button and then mark two points on the map, either on top of other elements or on empty points. The imaginary line joining these two points will serve as a reference to enter the relative point. Once selected, a form will open where to set the distances.

| ![Figure 77](images2/figure77_point.png) |
|:------------------------------------------------------------------:|
| *Relative distances and the use of the first or second point are entered in the form.*|

The X distance will be the position where the support point will be located respecting the x coordinate of the beginning of the imaginary line. The Y distance will be the position where the support point will be located with respect to the y coordinate of the beginning of the imaginary line. Using the two distances, the element can be located. Both values admit negative numbers, since only then can points be placed in all directions.

If we click *From: Init point* the distances will be taken from the point which was clicked as first

In the case of *End point*, the distances will be relative to the second clicked point by the user.

| ![Figure 78](images2/figure78_point.png) |
|:------------------------------------------------------------------:|
| *Example of a relative point located 5 meters of x distance and 10 meters of y distance from the Junction node type. Here is where the first click was made, the second one was made above, on the horizontal section in order to follow the same direction.*|

All the support points created in a project are stored in an auxiliary view, in the same way as in the other CAD tool. In this case the view is called *v_edit_cad_auxpoint* and itt can be found in the *BASEMAP* group of the ToC.

### 5.2.4 Hydraulic model

The group of tools related to the hydraulic model is the one which will be used by specialized users in the management of hydraulic behaviors in the distribution or sanitation networks. In addition to knowing the use of the four tools that make up the group, the users should also be clear about the data that is necessary for the models to work properly. These data are described in sections **4.2.3** and **4.2.4**. The characteristics and specific operations of the hydraulic model are explained in detail in section **7** of this manual.

**5.2.4.1 Go 2 EPA**

![Figure 79](images2/figure79_epa.png)

*Go 2 EPA* is the group's main tool for exporting the hydraulic model. Its goal is to obtain the results of this model, by filling in the corresponding tables and views, so that they can be automatically visualized in QGIS through a specific symbology.

Before using the tool, it is necessary to enter the mandatory data in the group tables of EPANET (WS) or SWMM (UD), depending on the type of project which we work with. The tool has many similarities between both types, although there are parameters that are only specific for one type or another.

**FIRST PART - SPECIFIC**

![Figure 80](images2/figure80_ws.png)

When opening the tool, the main form opens, which has two buttons, designed to define parameters prior to the process (Image below).

| ![Figure 81](images2/figure81_epa.png) |
|:------------------------------------------------------------------:|
| *Main form of the Go 2 EPA tool, with pre-process options highlighted in red.*|

The first button is the selector of demand scenarios (**7.1.1.2**), which allows selecting a specific demand scenario, previously defined, to act on the exportation of the model. The performance is the same in all tools of 'selector' type, allowing to move different scenarios from one column to another.

The *Options* button, which appears in second place, is where the user can define different variables related to the hydraulic model.

| ![Figure 82](images2/figure82_epa.png) |
|:------------------------------------------------------------------:|
| *Options form of the Go 2 EPA tool. The data and model settings that precede the export are entered here.*|

All these fields are similar to those used by the EPANET program, therefore, the user in charge of this process, by knowing the hydraulic operation, should already know how to fill in or modify the fields or if it is necessary to modify some of the values that are predefined when opening the form.

Without a doubt, the most important widgets that control the export are those marked in red. See chapter 7 - EXPORT - IMPORT OF HYDRAULIC MODEL for more information

![Figure 83](images2/figure83_ud.png)

The tool is considered the same for both WS and UD, but, as already mentioned, the data, processes and results are different. If the project you are working with is sanitation and water drainage, then the tool form will be a little different.

| ![Figure 84](images2/figure84_epa.avif) |
|:------------------------------------------------------------------:|
| *Go2 Epa Options you can define some model parameters for the UD schema*|

In the options buttons prior to the process, instead of the demand scenario selector, we will find the hydrology selector, defined in the *cat_hydrology* table.

| ![Figure 85](images2/figure85_hydrology.png) |
|:------------------------------------------------------------------:|
| *Hydrology selector, which has associated information regarding infiltration.*|

Regarding the *Options*, these are very similar to those of the SWMM program, therefore, knowing these, the form can be filled in correctly.

**SECOND PART - COMMON**

The second part of the export/import process of the hydraulic model is carried out after the first one, i.e., once the database has the hydraulic data and the options of the specific part are correctly configured.

At this time we will focus on the 'File manager' section of the Go2EPA form.

There you must define the name for the corresponding export, as well as establish the paths on your computer where to store the inp and rpt files that will be generated at the end of the process.

**5.2.4.2 Result manager**

![Figure 86](images2/figure86_result.png)

The *Result Manager* tool allows the user to visualize the data of the different results of the import and export processes of the hydraulic model.

The form of the tool shows, for each row, different data of each one of the model's results. As always, filtering based on the *result_id* field is possible, and rows can be eliminated.

| ![Figure 87](images2/figure87_management.png) |
|:------------------------------------------------------------------:|
| *Form of the result manager. Here are shown all the results of the exportation of the hydraulic model. These can be filtered, shown, or deleted.*|

**5.2.4.3 EPA Filter**

![Figure 88](images2/figure88_filter.png)

This tool is used to establish which results of the hydraulic model will be displayed in QGIS at that moment. The data of the chosen result will be the ones that fill in the different views present in the project, so it will be possible to see results of old processes, sectors, or specific scenarios.

One of the highlights of the information management regarding the hydraulic model that Giswater does is the possibility of using data from two different results at the same time; one of main and another that serves to compare and visualize the existing differences.

With this tool it is also possible to select the result with which the main one will be compared, so that the data will appear in the comparison tables. These have the same style as the main results; therefore, it will be possible to play with both groups and compare results.

| ![Figure 89](images2/figure89_selector.png) |
|:------------------------------------------------------------------:|
| *Form of the EPA Filter is simple. In the first drop-down, you can choose the result that will be shown in the QGIS layers intended for this. In the second, you choose with which result it will be compared, so that the data from this second also occupies its side in the QGIS ToC and it is easy to compare both results.*|

The functioning of this tool is remarkably simple: simply select the main result in the first combo box, which will show all available results. In the second combo box, the result that will serve as a comparison is selected. By clicking the *OK* button will update the data and can be used.

### 5.2.5 Masterplan

The planning tools are specially designed for users in charge of issues related to budgets (both at the level of individual elements and of actions with multiple effects) and the management of planned sectors of the network. For the correct functioning of this group of tools, the project and its data must be specially configured and with great accuracy.

As already explained in section **4.2.5**, referring to the tables related to planning, the first step of all is to fill in the price data of the elements. The prices should be inserted in the *Simple Price*, *Compost Price* and *Value Compost Price* tables and these will be linked to the elements present in the results tables of their category:

* *Plan result node*
* *Plan result arc*
* *Plan psector x node cost*
* *Plan psector x arc cost*

If in the planning operations an economic planning should be carried out, it is necessary to fill all the prices of the fields of the tables that are related to it. For more information, see section **4.2.5.**

The different tools that make up the masterplan group are explained below.

**5.2.5.1 New planification sector**

![Figure 90](images2/figure90_sector.png)

This tool aims to allow the user to create a new planning sector and assign the elements with which it will be related, as well as show the cost details of the set of operations that would be necessary to carry out the project.

| ![Figure 91](images2/figure91_psector.png) |
|:------------------------------------------------------------------:|
| *Form to add a new planning sector. In this first tab basic data of the sector are added*|

First, when we open the tool, the *psector* form appears (image above). This form is similar to the one that each specific element of the network has but referring to an entire sector of the map and therefore to several elements.

In the initial tab the basic data of the *psector* must be entered: name, priority, exploitation, and sector to which it belongs, type and other observations.

The moment we click OK, the planning sector will be created. At first it will appear without geometry, but the moment it begins to have relationships with elements, a polygonal and rectangular geometry will automatically be generated around the linked elements.

![Figure 92](images2/figure92_note.png)

To link the network elements to a *psector* there are two ways:

* When inserting a new element with a planned status. It will be causally linked to the planning sector that is selected as default at the time.
* Through the *Relations* tab of the form (Image below) elements that will be part of the *psector* can be selected.

| ![Figure 93](images2/figure93_plan.png) |
|:------------------------------------------------------------------:|
| *The second tab of the form is used to link the planning sector with the elements of the network.*|

In this tab the information of the related elements will appear. It is *important to look* at the *state* and *doable* fields. *State* refers to the state within the *psector*, it is not the state of the element in the network. The elements with state 1 will be displayed and those with state = 0 will not. *Doable* is used to establish whether the element will enter into budget calculations: TRUE will enter, FALSE will not enter. In many cases, the planning sectors need to incorporate existing elements in the network, which should not be used to calculate the price. The goal of this field is to allow such calculations. Those two fields will be filled automatically depending on the *state_type* of the linked element.

The third tab of the form is used to add to the budget of the planning sector the prices of any other parameters that are required to develop the work, apart from the value of the elements of the network. For example, the user can add prices for the transport of waste, excavation or any work that is necessary.

To select any of the prices and link it with the total budget of the planning sector you only need to click on the lower part of the form named ADD PRICES. The available prices are shown in the *price_compost* table. All those that are necessary for this budget can be added from here.

| ![Figure 94](images2/figure94_plan.png) |
|:------------------------------------------------------------------:|
| *The tab Other prices allows to link the costs not related directly with the network elements to the planification sector.*|

The tab *Budget* allows to see a budget summary of the planning sector. Here, the prices of the planned operations are detailed and presented in groups:

* Total value for arcs
* Total value for nodes
* Total value for other parameters
* General expenses (+19%)
* VAT (+21%)
* Others

With the sum of all these groups of prices the **total budget** of the project is generated.

| ![Figure 95](images2/figure95_plan.png) |
|:------------------------------------------------------------------:|
| *The last tab of the form shows the total Budget of the psector. It is possible to create personalized reports with the data of psectors using the Generate rapports.*|
   
In the lower part of the form there is the *Generate rapports* button, which allows to create external files with the information about the *psector* we are working. There are three options to generate reports, each of them individually selectable based on the interest of the user. The file in pdf format that can be generated by the QGIS composer can use templates that the user loaded into the project. Keep in mind that the template must be well configured so that the process could work properly.

The last tab, added in version 3.1 of the *plugin*, allows to link documents to a psector. These can be created again from the existing form or link.

**5.2.5.2 Psector manager**

![Figure 96](images2/figure96_psector.png)

The planning sector manager is a tool that allows to inventory, visualize, filter, and eliminate the existing psectors. In addition, it shows the planning sector which is selected as default now and allows to change it by another one. The default psector is an important parameter, since all the planned elements that are inserted will be linked to it.

In the form, that opens after clicking on the tool button, we can see a table with all the existing sectors and its data.

With a double click on the row it is possible to open the specific psector, where the user can put into practice all the functionalities of the previous tool. Unlike other Giswater management tools, this one serves as the **only way to open the psector forms**, therefore, it will be of remarkable importance when working on planning.

In the upper part of the form there is a filter, see the current default psector, change or delete any of the existing.

| ![Figure 97](images2/figure97_psector.png) |
|:------------------------------------------------------------------:|
| *Form of the psector manager. All existing psectors in the project are displayed here. The tool allows you to filter according to the identifier, update the psector that will be used as default, delete data, or open a specific form, where the user can view the related elements and associated budgets.*|

**5.2.5.3 Network cost manager**

![Figure 98](images2/figure98_network.png)

The network cost manager is a tool that allows to inventory, visualize, filter, and eliminate the different calculated network costs.

In the form that opens after clicking the tool button we can see a table with all the results, which shows the data of each of the results.

With a double click on the row it is possible to open the specific result, where the user will be able to see the related information.

In the upper part of the form, it can be filtered according to the result identifier.

| ![Figure 96](images2/figure96_price.png) |
|:------------------------------------------------------------------:|
| *Form of the network cost manager. All the costs are shown here and can be filtered or opened.*|

### 5.2.6 Utilities

This last group of tools of the Giswater plugin is formed by tools that can be used for different project related tasks. It is a heterogeneous group, with vastly different functionalities focused on general processes, unlike the rest of the toolbars that had much more specific role. Here there are tools that allow control, topology, value management, data import and functionalities focused on basic users to get the most out of Giswater.

We are going to see, one by one, the different tools that make up this bar.

**5.2.6.1 Toolbox**

![Figure 99](images2/figure99_toolbox.png)

The toolbox aims to offer a multitude of functions that may be useful when checking if certain parameters of the project are correct. The different functions offer different answers: some insert data in tables and others represent new geometries within a layer.

The new toolbox has a different form than the previous one, present in the last version of Giswater, since now it can be opened through a side panel, simulating the usual toolboxes in most GIS softwares. Here we can see, grouped by role, the different functions that are available for the user.

By double clicking on one of the functions, its form will open, where:

* **Input layer**: input layer on which the process will be executed.
* **Selection type**: the function can be passed over the entire input layer or only over a previous selection made with the QGIS selection tool.
* **Option parameter**: some functions have configuration parameters so that the process is one or the other.
* **Info**: description about the process functionality.
| ![Figure 100](images2/figure100_info.png) |
|:------------------------------------------------------------------:|
| *Example of a form to use the functions available in the toolbox.*|

With new versions coming out of Giswater, new functions will appear in the toolbox, but so far there are 11, which are the following:

* **Check data form O&M process:** It aims to find errors and inconsistencies in the data before using O&M processes. It will vary depending on the type of project; cutting polygon (ws), longitudinal profile (ud) and visit (ws and ud).
* **Check arcs with same start/end node**: topological control assistant. To review how many arcs have the same node1 and node2.
* **Check arcs without start/end node**: topological control assistant. To review how many arcs don’t have any initial or final nodes.
* **Check connecs duplicated**: topological control assistant. To review how many connecs are duplicated.
* **Check inconsistency on editable data**: It aims to find errors and inconsistent data in the editable data.
* Check node topological consistency: topological control assistant. Helps the user to identifiy nodes with more or less sections that are connected to it, depending on the number of arcs that have been defined in the *num_arcs* column of the *node_type* table.
* **Check nodes duplicated**: topological control assistant. To review how many nodes are duplicated.
* **Check node orphan**: topological control assistant. To review how many nodes are disconnected from the network.
* **Check data according to the EPA rules**: It aims to find errors and inconsistencies in the data before making the first export to EPA model. Checks the model tables of the mandatory data to perform the simulation. It works with all the tables that are necessary to carry out the process of exporting data to a hydraulic model. If there is still no EPA result in the database, this function can be executed directly. Subsequently, it can be eliminated with the results manager tool.
* **Check plan missing / wrong data before prices**: It aims to find errors and inconsistencies before the first budget calculation with Giswater. Checks the price tables and the required data to perform the calculation.
* **Build nodes of arc without start/end node**: Massive construction assistant. Creates as many nodes as necessary to comply with the topology rules. To do so, all the nodes will be inserted using the default user values (catalog, workcat_id, state, type of state and node type (ud)). Before executing the function, it is important to check that all the nodes will be inserted inside one of the zones of the map. If you want the nodes that are necessary not to be entered directly in the node table, to review them first, they can be entered in the anl_node table if we uncheck Direct insert into node table.

Some of these tools are designed to review data after the complete migration process, during which some topological control rules are disabled to facilitate the insertion of elements. It is after the insertion of elements and with active topological rules that these functions can be executed for review.

Beyond this case, some functions should never return data, since the control of errors and inconsistency of Giswater will never allow, for example, that a section has no initial or final node.

**5.2.6.2 Config**

![Figure 101](images2/figure101_config.png)

Configuration assistant for the behavior of the *plugin*. It allows to define different parameters that are used in other tools and processes of the project. It is a tool of enormous importance and that all users should know well, since its use is recurrent and essential for the operation of Giswater.

The form of the tool is divided into five different tabs. The first of them is common. The second, *Featurecat*, will vary depending on whether the project is for water supply or sanitation, since it is based on establishing default values for the insertion of network elements.

However, the operation is the same for all tabs: each parameter has a checkbox next to its value. The user can set the value that he considers appropriate, following the filters that each parameter has. If the checkbox is checked, the value of the parameter will be active and stored in one of the database configurations tables. If the checkbox is not checked, the value of the parameter will not be used anywhere.

Within the tool we will find both default values configurable by the user and system values, which can also be modified or chosen by the user in the way that has been explained in section **3.6**. Many of the values that can be configured with the tool are easily recognizable, however, there are some that are more complex and require a concrete explanation. Some of the most prominent values are explained below:

Other:

* **Keep opened edition**: if it is marked, in case of insertion of a network element, the edition of the layer will remain opened. Otherwise, it will close automatically.
* **Connect connecs to network**: if it is marked, when you insert a connec or gully type element, it will connect directly to the nearest section through a link.
* **Force link & vnode downgrade**: if it is marked, when we change the stauts to obsolete or remove a connec or gully element, the corresponding link and vnode will also be affected.

Topology:

* **State topocontrol**: activate or deactivate the topological control of states.
* **Arc same node init end control**: controls those arcs with start and end ends located at the same node.
* **Arc searchnodes buffer**: manages the tolerance when connecting ends of the arc to the nearest node.
* **Node/connec proximity control**: allows or not the insertion of very close nodes/connecs, using a tolerance value.
* **Double geometry enabled**: allows the automatic insertion of double geometry elements and controls the area that the generated polygon will occupy.
* **Link search buffer:** allows to establish a tolerance to perform a *buffer* relative to a link.
* **Neighbourhood proximity buffer**: allows to establish a tolerance when making a *buffer* that looks for elements considered as neighbors.

System:

* **Scale zoom**: controls the scale at which the elements will be zoomed when the Search tool is used.

| ![Figure 102](images2/figure102_scale.avif) |
|:------------------------------------------------------------------:|
| *Giswater Configuration Tool Form. In the Other tab, different parameters can be configured with a default value and modify some of the characteristics with which the user works.*|

**5.2.6.3 Import CSV**

![Figure 103](images2/figure103_csv.png)

Many times, it will be probable that we have data from our water network that is in table formats, such as *xls* or *csv*. Giswater incorporates this tool in its plugin to offer the possibility of importing directly into the schema tables the data contained in a *csv* file.

To show the functionality of the tool, we will use as an example the possibility of importing a price table, which will be incorporated directly into the *price_compost* table of our schema. To do this, the program has a function specially designed to carry out this process. Every import of csv files must have a specific function.

We are going to see, step by step, how to use the tool to incorporate new simple prices to our database:

1 - We must have a .csv file ready to import. This means that it must meet the requirements of the tool and the Giswater function, otherwise the data will not be incorporated correctly. To know these requirements, we must open the tool and, at the top, select *Import db* prices as *Import type*.

| ![Figure 104](images2/figure104_csv.png) |
|:------------------------------------------------------------------:|
| *The form of the tool explains how the csv file to be imported should be. The general name of the imported prices will be: Test Giswater.*|

![Figure 104.2](images2/figure104.2_csv.png)

2 - We prepare our file based on these requirements.

3 - Within the form, with *Import db prices* selected, we assign a value for *Import label*, which will be the name that the import prices will receive and will be incorporated into the simple price catalog (*Price_cat_simple*). For this example, it will be: **Test Giswater**.

| ![Figure 105](images2/figure105_test.png) |
|:------------------------------------------------------------------:|
| *With the file path added, the table will show a preview of the data.*|

4 - Next, we add the path of the *prices2.csv* file and select the encoding and the delimiter, which can be 'comma' or 'semicolon'. The table below shows us a preview of what the data to be inserted will be like (Image below).

5 - Click the OK button and the import is carried out.

6 - The function is parameterized so that the data from our correctly structured file is incorporated directly into the *price_compost* table, so that the columns of this table coincide with those of the import. As we see in the next image, the data is perfectly added to the table, with all its records and with the price catalog *(pricecat_id)* as **Test Giswater**, which is selected from the *price_cat_simple* table where it has just been incorporated.

| ![Figure 106](images2/figure106_test.avif) |
|:------------------------------------------------------------------:|
| *The data found in the csv file has been incorporated into the price_compost table, so that these prices can be used for other Giswater functionalities.*|

At the end of the tool process, it has been possible to link the information we have in a *.csv* file to specific tables in the database. At this moment, the data found in the *price_compost* table is available to be used in other Giswater tools and processes, for example, when making budget calculations with Masterplan operations.

Apart from linking the price tables, the tool includes other specific functionalities to import *csv* files that refer to:

* **Import addfields**: to link custom fields directly to the *man_addfields_value* table. To do so, the table must have the id of the element, the parameter (referring to the custom field) and the value to assign.
* **Import elements**: useful for linking elements associated with sections, nodes or connecs. A specific table for each type of element will be necessary to do the import; i.e., if we want to link elements to nodes, we will have to make a *csv* table with only node-type elements. The table must contain the id of the topological element, the catalog of the associated element, observations, additional comments, and number of elements. When performing the operation, *the element* and *element_x_* tables will be automatically populated, which link the elements associated with the topological elements (node, arc, connec).
* **Import visit table**: useful to link visits to any type of network element. There are specific functionalities in the *Import type* drop-down list, for each type of element, so the visits can be linked only to nodes, arcs or connecs depending on the selected type and the *csv* file.

**5.2.6.4 Fast print**

![Figure 107](images2/figure107_print.png)

This last utility tool is specifically developed to facilitate the printing of plans and maps. In addition, it also allows adding information directly to some of the fields that contain the corresponding print *composer*.

To use it, there must be at least one composer configured using QGIS tools. Once it is done, the quick print will allow us to draw a map of a specific area with the characteristics of the selected composer.

By opening the tool, we select a *composer* and then choose the scale of the map. Everything that is inside the box that appears on the canvas will be a part of the printed map. We have the possibility to move freely and place the box where we want, so that exactly the part that we want to take is shown on the map.

There is also the possibility of rotating the *canvas* using the tool, to allow even more precision while printing the selected area.

The more advanced users who also master the database, may add other values to this form, by filling in the fields, the information will appear directly on the print, placed in some part of the *composer*.

To do it is necessary:

1 - Add to the *composer* the text elements with the concrete ID. For this example, the fields are:

  * Title, description, author, date

2 - Open the table *config_api_form_fields* in pgAdmin. There are some fields with the *formname=printGeneric*. More of them can be added as showed on the image below:

| ![Figure 108](images2/figure108_print.avif) |
|:------------------------------------------------------------------:|
| *In the table config_api_form_fields the user can add, remove, or modify the values that allow to personalize the fast print tool.*|

3 - The field *column_id* must match the IDs that we have put in the composer. In *label* we will configure the label we will see in the form. In *layout_order* the order within the optional values. The rest of the fields will be like the ones that already come by default in the other rows, apart from *widgetfuncion* where it’s necessary to change *gw_api_setprint* to *gw_api_set_composer*.

4 - We go back to QGIS and open the tool. We select the configurated composer, in this case *comp_giswater*. We place the box in the desired place, moving the map below and using the scale and rotation fields.

5 - We fill in the optional fields with data so that in the end we see something like image below:

| ![Figure 109](images2/figure109_print.avif) |
|:------------------------------------------------------------------:|
| *We see the form that we have configured in the database and the box of the area that we are going to print in the composer. If we fill in the available data, these will be automatically placed in the place previously established in the composer.*|

6 - We click *Print* and select the printer or export to pdf. **Attention**, remember to configure the printing of the page horizontally or vertically depending on how it’s done in the composer.

7 - If the print was saved in pdf it will be already available in the selected folder with the optional values set where they have been configured.
Final result of the print using the configured values and filled in using the fast print tool.

| ![Figure 110](images2/figure110_mapa.png) |
|:------------------------------------------------------------------:|
| *Final result of the print using the configured values and filled in using the fast print tool.*|

**5.2.6.5 Check project**

![Figure 111](images2/figure111_check.png)

This tool aims to offer the user a detailed summary of the health status of their project.

The operation is as simple as clicking the button and this summary will automatically be generated and displayed through a form.

This form includes, in its first part, the information about the versions that the user has, both Giswater plugin and the database, as well as other versions such as QGIS, PostGIS, Postgres and their own operating system.

The second part shows the status of the project, i.e., the work scheme to which the QGIS project is related. Up to 3 information headers can appear here:

* CRITICAL ERRORS: Errors in the data that must be immediately resolved, as they can generate important problems or inconsistencies in the operation of Giswater.
* WARNINGS: Minor inconsistencies that are recommended to be resolved, but that their existence does not significantly affect the operation of the program.
* INFO: All the processes that are controlled and verified with this tool appear here. You can check what they are. Appearing in INFO means that the process has returned an expected result.

| ![Figure 112](images2/figure112_check.png) |
|:------------------------------------------------------------------:|
| *Form resulting from verifying the project, with the information on the versions and the review of the processes with their different headers depending on the status.*|
