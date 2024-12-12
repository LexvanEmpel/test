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


# Annex

**Description of Giswater configuration variables**

The configuration and customization possibilities in the Giswater environment are exceptionally large, since it is intended to meet most of the needs of the different users by integrating all the processes in the same code.

Through the tables *config_param_system* (for system configurations, which will affect the entire schema regardless of the user) and *config_param_user* (for configurations per user) many work processes can be customized.

To know the different configuration variables, you can access the **Github Giswater_db_model Wiki**, where this and many other tables of the database are defined and explained. In addition, you can also find a lot of [additional information](https://github.com/Giswater/giswater_dbmodel/wiki/config_param_system) to get started with the project.

This is a database-centric project. The database acts as more than just a database. You are working on a new approach that unites data, user actions, and advanced algorithms. 

As a result, you can find the relationships that act as a standard DB approach, the tables within 'inner logics' that work in an advanced database approach, and many stored procedures that act as 'inner algorithm' on the page **Dbmodel: filling tables and strategies**

[GitHub Dbmodel: filling tables and strategies · Giswater/giswater_dbmodel Wiki](https://github.com/Giswater/giswater_dbmodel/wiki/Dbmodel:-filling-tables-and-strategies){ .md-button .md-button--secondary }