# 10. Connection with data from the commercial management system

Giswater is prepared to simulate flow data in water projects (WS) taking data from the commercial management system. It is not an easy task. You will need specific tables similars to the ones on the following list (mandatory on bold):

***hydrometer***
***hydrometer_x_data***
*hydro_cat_catalog*
*hydro_cat_category*
***hydro_val_state***
***hydro_cat_period***
*hydro_cat_priority*

By using a script to connect to the CRM, these tables can be filled, either with real-time data, or with data obtained through a nightly data loading and updating process. 

Usually these tables are stored in an specific schema named *crm*.

Once the tables are filled in, its information **must be connected to Giswater data model** with their corresponding correlation tables:

***ext_rtc_hydrometer***
***ext_rtc_hydrometer_x_data***
***ext_cat_period*****
***rtc_hydrometer***
***rtc_hydrometer_x_connec***

**WORKFLOW OF TABLES AND DATA**

* For each hydrometer, table **ext_rtc_hydrometer** need to be filled using some nightly process. After first load it only updates changes.
* For hydrometer consumptions, the table **ext_rtc_hydrometer_x_data** need to be filled using some nightly process each time you have new data from billing period (in combination with **ext_cat_period**).
* For each hydrometer, the relation with the Giswater hydrometer is: **rtc_hydrometer**.<span style="color: blue;">**hydrometer_id**</span>.::text = **ext_rtc_hydrometer**.<span style="color: blue;">**id**</span>::text
* For each hydrometer, the relation with the Giswater connec is: **ext_rtc_hydromete**r.<span style="color: blue;">**connec_id**</span>::text = **connec.**<span style="color: blue;">**customer_code**</span>::text
* Finally it is mandatory to keep the table **ext_cat_period** updated and be sure that you fill two tables more with giswater ids (hydrometer_id & connec_id)
    * **rtc_hydrometer** with <span style="color: blue;">**hydrometer_id**</span>
    * **rtc_hydrometer_x_connec** with <span style="color: blue;">**hydrometer_id**</span> and <span style="color: blue;">**connec_id**</span>