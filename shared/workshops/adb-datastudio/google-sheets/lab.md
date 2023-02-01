Workshop Request
================

+-------------------+-------------------------------------------------+
| Workshop Title    | Query and Analyze data in Autonomous Database   |
|                   | from Google Sheets                              |
+===================+=================================================+
| Short Description | Learn how to setup and use Google Sheets add-in |
|                   | to run native SQL and query Analytic Views on   |
|                   | ADW                                             |
+-------------------+-------------------------------------------------+
| Long Description  | The Autonomous database built-in Data Studio    |
|                   | application allows users to connect and query a |
|                   | schema from Google Sheets. This offering is an  |
|                   | Add-in that is available on the Database        |
|                   | Actions page. With this capability, you can     |
|                   | easily query and analyze data in an Autonomous  |
|                   | Database with a client tool of your choice. The |
|                   | add-in provides a simple way to access and      |
|                   | share data from the Autonomous Database, either |
|                   | accessing tables and views directly from SQL,   |
|                   | or using Analytic Views, which provide a        |
|                   | pre-defined reporting model over relational     |
|                   | data..                                          |
+-------------------+-------------------------------------------------+
| Stakeholder       | Data Analyst, Data Scientist, Data Engineer     |
+-------------------+-------------------------------------------------+
| Abstract          | > **Workshop Elevator Pitch/Messaging**: Access |
|                   | > data from autonomous database on google       |
|                   | > sheets for data export and analysis.          |
|                   | >                                               |
|                   | > **Workshop Description**: Learn how to set up |
|                   | > and use the google sheets add-in and run      |
|                   | > native SQL queries or use a wizard to analyze |
|                   | > data from Analytic Views.                     |
|                   | >                                               |
|                   | > **Why is this workshop needed?** This         |
|                   | > workshop augments the documentation and       |
|                   | > provides a visual step-by-step guide to set   |
|                   | > up the google sheets add-in and showcase the  |
|                   | > features of the add-in                        |
|                   | >                                               |
|                   | > **What products/technologies are used?**      |
|                   | > Autonomous Database (Shared), Data Studio,    |
|                   | > Analytic Views, Google sheets(add-in)         |
|                   | >                                               |
|                   | > **Is there a primary Oracle                   |
|                   | > product/technology being showcased? If so,    |
|                   | > what is it?** Autonomous Database add-in for  |
|                   | > Google Sheets                                 |
+-------------------+-------------------------------------------------+
| Workshop Outline  | Lab 1: Create an Oracle Autonomous Database     |
|                   |                                                 |
|                   | Lab 2: Create a User                            |
|                   |                                                 |
|                   | Lab 3: Setup Analytic view                      |
|                   |                                                 |
|                   | Lab 4: Download and setup add-in for google     |
|                   | sheets                                          |
|                   |                                                 |
|                   | Lab 5: Setup OAuth client on ADB and connect to |
|                   | ADB                                             |
|                   |                                                 |
|                   | Lab 6: Use Native SQL wizard                    |
|                   |                                                 |
|                   | Lab 7: Query AV using the Query Wizard          |
|                   |                                                 |
|                   | Lab 8: Additional capabilities of the add-in    |
+-------------------+-------------------------------------------------+

Introduction
============

About This Workshop
-------------------

This workshop provides a detailed guide on setting up the add-in for
Google Sheets to run both native SQL and a wizard to analyze data using
Analytic Views.

Native SQL allows you to query tables and other objects using SELECT
statements that you write.

An Analytic View is a type of view in the Oracle Database that allows
you to perform complex queries and calculations on data stored in one or
more tables. These views provide a higher level of abstraction over the
underlying data, allowing users to access and analyze the data in a more
meaningful way. They are typically used in Business Intelligence and
Data Warehousing applications, and can be based on a single table or
multiple tables joined together.

About the Add-in
----------------

This add-in is available as a downloadable zip file that users can set
up in their personal or business Google accounts for Google Sheets. The
Add-in provides the ability to connect to Autonomous Database without
having to install any client wallets or drivers. It uses ORDS to query
the database and OAuth to authenticate users to their schema.

Objectives
----------

In this workshop, you will learn the following:

-   How to set up the client as an add-in on Google sheets

-   How to create an OAuth client on the Autonomous Database

-   How to run native SQL queries on tables in your schema

-   How to use the wizard to analyze data over Analytic Views defined in
    your schema

About the Data
==============

The data set used in this Live Lab is a variation of the MovieStream
data set used by many other Autonomous Database labs. MovieStream is a
fictitious video streaming service. The version of the data set used by
this lab is presented in a form that is easy to analyze. It supports the
analysis of sales data by time, geography, genre used when searching for
movies, and other attributes.

Lab 1: Create and Oracle Autonomous Database 
============================================

Task 1-n: Use block.

Lab 2: Create a User
====================

Task 1-n: Use block. QTEAM user.

Lab 3: Setup Analytic view
==========================

We set up an Analytic View in the autonomous database in this lab. We
create a fact table and a dimension table on which an Analytic View is
developed to analyze the movie sales data. To create the required schema
components, run the following script by opening a SQL worksheet.

Follow the steps outlined below to execute the script:

Task 1:

1.  

The script does the following:

1.  Creates customer dimension and movie sales fact tables.

2.  Loads the data into these tables from an object store location.

3.  Creates an Analytic View for analyzing movie sales data, with:

    a.  Attribute Dimensions

    b.  Hierarchies

    c.  Calculated Measures

This allows us to analyze the movie sales data across various dimensions
and using calculated metrics.

The following tables are created:

1.  CUSTOMER_DIM -- this table has details about customers, and acts as
    the source for the following dimensions and hierarchies -- Age
    Group, Customer Segment, Education, Geography (a hierarchy of
    Continent, Country, State and City), Income Level and Marital
    Status.

2.  MOVIE_SALES_FACT -- this table has sales details for movies for each
    customer, and acts as the source for the following dimensions and
    hierarchies -- Day of Week, Device, Discount Type, Search Genre, and
    Time (a hierarchy of Year, Quarter, Month and Day). It is also used
    to generate the simple measures SALES, QUANTITY, and
    DISCOUNT_PERCENT, as well as the following derived measures:
    SALES_60_DAY_MOVING_AVERAGE, SALES_GEOG_SHARE_OF_PARENT,
    SALES_SHR_DISCOUNT_TYPE, SALES_CHANGE_PRIOR_PERIOD,
    SALES_PCT_CHANGE_PP, SALES_CHANGE_YEAR_AGO,
    SALES_PCT_CHANGE_YEAR_AGO and SALES_SHR_SEARCH_GENRE.

Lab 4: Download and set up add-in for Google Sheets
===================================================

To connect to the Autonomous Database from Google Sheets, you need to
download and set up the Add-in.

Follow the steps outlined below:

1.  Download the Google Sheets Add-in on the Database Actions page from
    the link available in the right-hand navigation pane. Scroll down if
    required.

![1-Getting Started](media/image1.png){width="2.37in"
height="6.322601706036745in"}

2.  Follow the instructions to install the required scripts and set up
    access on Google Sheets.

Lab 5: Set up an OAuth client and connect to the Autonomous Database
====================================================================

Before you can connect to an Autonomous Database from Google Sheets, you
need to set up an OAuth client. OAuth is an open-standard protocol that
provides better performance and security used by ORDS. Follow the steps
as outlined below:

1.  Navigate to the OAuth URL of your instance (after the schema name in
    the URL append - /oauth) e.g.,

2.  On the landing page, click on Clients.

> ![Graphical user interface, text, application, email, Teams
> Description automatically generated](media/image2.png){width="4.77in"
> height="1.5634995625546806in"}

3.  Click on New Client

> ![Graphical user interface, application Description automatically
> generated with medium confidence](media/image3.png){width="5.4in"
> height="1.5403827646544181in"}

4.  Provide the following details:

    a.  **Name:** Name of the client.

    b.  **Description:** Description of the purpose of the client.

    c.  **Response Type:** CODE

    d.  **Allowed Origins:** you can leave this blank for the workshop.

    e.  **Support URI:** https://script.google.com/

    f.  **Logo:** Select an image from your local system to insert a
        logo for your new client.

    g.  **Flow:** AUTH_CODE

    h.  **Redirect URI:** This is the URL for the google sheet when you
        deploy the app script. This can be obtained after the downloaded
        scripts are deployed in google sheets.

        i.  On the app scripts page of google sheets, click the deploy
            button and manage deployments

> ![Graphical user interface, text, application, chat or text message
> Description automatically generated](media/image4.png){width="1.3in"
> height="1.1721292650918635in"}

ii. Copy the Web app URL from the deployment details

> ![Graphical user interface, text, application, email Description
> automatically generated](media/image5.png){width="3.2in"
> height="2.527856517935258in"}

i.  **Support Email:** Enter support\@oracle.com

j.  **Required Privileges:** Choose default -- RESTful Service Editing

> ![](media/image6.png){width="3.4in" height="2.2935465879265093in"}

5.  Once the client is created, you can view it:

> ![Graphical user interface, application Description automatically
> generated](media/image7.png){width="4.9in"
> height="1.4631944444444445in"}

6.  Click on the edit icon to get the client id and client secret.

> ![Graphical user interface, application Description automatically
> generated](media/image8.png){width="3.353018372703412in"
> height="3.044225721784777in"}

7.  To register the client application (Google Sheets) from the Add-in,
    you will need the following information:

    a.  ADB URL:

    b.  Client Id

    c.  Client secret

8.  Now you are ready to connect to the Autonomous database from your
    Google Sheet.

    a.  On the top navigation page, you will see a new tab -- "Ask
        Oracle."

    b.  Click Register

> ![](media/image9.png){width="3.573490813648294in"
> height="0.7502045056867892in"}

c.  A pane opens on the right side to enter the details. Enter the
    details as captured in the previous step and click Authorize.

> ![](media/image10.png){width="1.463254593175853in"
> height="2.060300743657043in"}

d.  Now you are ready to connect to your schema in the autonomous
    database. Click on the Ask Oracle tab to view the options:

> ![Graphical user interface, application, table Description
> automatically
> generated](media/image11.png){width="2.384514435695538in"
> height="1.5508081802274716in"}

e.  Click on Native Sql; this should open a new browser window to log
    into your ADB schema and provide your schema credentials to Sign in.

> ![Graphical user interface, application Description automatically
> generated](media/image12.png){width="4.849446631671041in"
> height="1.06418416447944in"}

f.  In the following screen, click Approve to grant access to the Google
    Sheets client to connect to the Autonomous Database.

> ![Graphical user interface, text, application, email Description
> automatically
> generated](media/image13.png){width="3.7073490813648293in"
> height="1.9229899387576552in"}

g.  If you see the below screen, you can proceed further in the lab as
    you are connected to your schema.

> ![Graphical user interface, text, application, email Description
> automatically
> generated](media/image14.png){width="2.8648293963254594in"
> height="1.15082895888014in"}

h.  Go to the Google Sheets tab on your browser to continue with the
    lab.

Lab 6: Use Native SQL wizard
============================

In this lab, you will use the Native SQL wizard of the Add-in. This
allows users to run SQL queries on the schema you are connected to.

This can also be used to export data from the Autonomous Database.

We have two tables that were loaded from cloud object storage. Let's run
some direct SQL on the CUSTOMER_DIM table to find out what different
marketing segments we have for customers.

1.  Launch the Native SQL wizard by choosing the Native Sql option under
    the Ask Oracle ribbon item.

> ![Graphical user interface, application, table Description
> automatically generated](media/image15.png){width="2.2in"
> height="1.3621489501312336in"}

2.  This launches the Native Sql panel on the right side. Paste the
    following SQL in the Write a Query box:

> select distinct customer_segment, customer_segment_short_name from
> customer_dim;
>
> ![](media/image16.png){width="1.2in" height="2.432001312335958in"}

3.  Click Run.

4.  Since we chose the table option, a new sheet with the resulting data
    is created along with some metadata about the execution.

> ![](media/image17.png){width="3.7in" height="1.9432906824146983in"}

5.  Let's run another query to fetch sales information for each customer
    segment. This would mean joining the customer_dim table with fact
    data.

6.  Paste the following query in the Write a Query box.

> select b.customer_segment, b.customer_segment_short_name, sum(a.sales)
> as total_sales, sum(a.quantity) as total_qty
>
> from movie_sales_fact a
>
> join customer_dim b
>
> on a.cust_id = b.customer_id
>
> group by b.customer_segment, b.customer_segment_short_name
>
> order by 3 desc;

7.  You can create a new sheet, click the + icon under the select
    worksheet section, provide the following name -- Sales by Segment,
    and click the Check icon.

> ![](media/image18.png){width="2.3in" height="4.225583989501312in"}

8.  Click Run

> ![](media/image19.png){width="1.6in" height="1.4525546806649168in"}

9.  A new sheet is created with the resulting data.

> ![](media/image20.png){width="5.165354330708661in"
> height="2.369109798775153in"}

This shows how easy it is for you to run SQL queries and fetch the data
in Google Sheets for further analysis!

As we see, anyone who can write SQL queries can quickly get the data
from an Autonomous Database for analysis on a tool they choose. However,
the Autonomous Database also allows you to model flat tabular data into
dimensional models, and use these models directly in your tool of
choice.

Lab 7: Query an Analytic View using the Query Wizard
====================================================

Bug raised for filter issues - **29-Jan-2023 - **Raised a new bug with
issues in
filtering **- [35024965](https://bug.oraclecorp.com/pls/bug/webbug_edit.edit_info_top?rptno=35024965) - **Ashish** - Parth** to
follow up on this. Filters should be done on ATTR.

In this lab, we will run through a wizard that allows you easily to
query data stored in the Autonomous Database using an Analytic View. As
part of the setup for this lab, we created an Analytic View of the movie
sales data including several hierarchies, measures, and calculated
measures. Let's analyze the movie sales data with the query wizard.

1.  On the top navigation pane, select the "Ask Oracle" tab

2.  Select Query Wizard

> ![](media/image21.png){width="2.173228346456693in"
> height="1.4255872703412074in"}

3.  This opens a pane on the right side of the Google Sheets window.
    This panel allows you to query an Analytic View defined in the
    Autonomous Database without having to write SQL queries. It has 3
    parts:

    a.  Analytic View -- Select an Analytic View defined in the database
        and select measures, hierarchies, and levels from the Analytic
        View.

    b.  Filter -- Filter the data using any of the dimensions, such as
        Year, City or Customer Segment. You can also create custom
        measures.

    c.  Query Result -- Provides a quick summary of the selections done
        in the previous sections. It allows you to choose from options
        like creating a native Google Sheets pivot table from the
        fetched data from the database, display options, and use an
        existing sheet for results or create a new sheet.

> ![](media/image22.png){width="2.5in" height="5.740744750656168in"}

4.  Click on Select an Analytic View and select the MOVIE_SALES_FACT_AV
    that we created in the script earlier.

> ![](media/image23.png){width="1.8in" height="1.2178444881889763in"}

5.  Under the Edit Query section make the following selections

    a.  Select Measures -- SALES, SALES_CHANGE_YEAR_AGO and
        SALES_PCT_CHANGE_YEAR_AGO

    b.  Select Hierarchies --

    c.  Select Levels -- YEAR and CUSTOMER_SEGMENT

> ![](media/image24.png){width="2.1in" height="4.373036964129484in"}

6.  Click Next.

7.  We will create a calculated measure. We have the Discount Percentage
    and Sales Amount, so we can easily calculate the Discount Amount.

8.  Click on Add/Edit Calculations and create a new calculation with the
    following:

    a.  Name -- Disc Amount

    b.  SQL for your Calculation (for the List Price) --
        SALES/(1-DISCOUNT_PERCENT)

> ![Graphical user interface, text, application Description
> automatically generated](media/image25.png){width="1.9in"
> height="2.8429669728783904in"}

9.  Click Add Calculation

10. You should see a new calculated measure as shown below. Click Next

> ![](media/image26.png){width="1.75in" height="3.761194225721785in"}

11. On the next screen, you can see a summary of selections in the
    previous steps. Make the following selections on this screen:

    a.  Display properties: Choose Table, keep the Column Per Level and
        Remove Empty Columns options unchecked.

    b.  Under Select Worksheet, click the + icon to add a new sheet.
        Give the name as "Sales and Disc by Year and Seg" and click the
        check icon to create a new sheet for the result

> ![Graphical user interface, application Description automatically
> generated](media/image27.png){width="2.2in"
> height="3.4240627734033247in"}

12. Click Submit

13. You should see the following results:

> ![](media/image28.png){width="5.6in" height="4.6373534558180225in"}

14. We can use this result to create native Google Sheets objects for
    further analysis. In the next step, we will rerun the same query and
    create a pivot table for analysis. On the right panel, under display
    properties, make the following changes:

    a.  Select the Pivot option

    b.  For the Select Worksheet, click the + icon to create a new sheet
        with the name -- Discount Analysis and click the check icon to
        save it.

> ![](media/image29.png){width="1.72in" height="2.669851268591426in"}

15. Click Submit.

16. A new sheet with a pivot table is created. As shown below:

> ![](media/image30.png){width="4.5in" height="2.071634951881015in"}

17. You can now click the Edit button to use the native Google Sheets
    pivot capabilities to explore the data further. Note: the data for
    this pivot table is available in a hidden dummy sheet which is the
    result set from the query that was run on the AV. In this example,
    the hidden sheet name is -- dummy11922. You can view this sheet by
    unhiding it from the View menu.

> ![](media/image31.png){width="5.5in" height="2.785844269466317in"}

As you can see the Google Sheets add-in can be used to easily extract
data from the Autonomous Database for analysis using familiar tools.

Lab 8: Additional capabilities of the add-in
============================================

...
