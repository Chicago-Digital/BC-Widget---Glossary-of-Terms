# BC-Widget - Glossary-of-Terms
Widget that allows you to output a web app list of terms on your website with the ability to live search for keywords as well as list out all active alphanumeric characters to be able to click to filter.

## Instructions

### Step 1. Upload widget folder to your site 
/_System/Widgets/glossary

----------

### Step 2. Create Glossary Web App

 1. In the admin under the Web Apps menu select Add Web App
 2. Name glossary web app whatever you would like
 3. If you want to have a detail layout for your terms select template or click "Disable Detail Pages"
 4. Click Next to continue to fields
 5. Click Add Field
 6. For field name enter "Alphanumeric First Character" and choose field type "Text (String)" set as mandatory and click save field
 7. That's it! Add your glossary terms now to your web app or add them at the end

----------

### Step 3. Get Web App ID and Web App Search ID (FID)

 1. In the admin under Site Manager select Pages
 2. Click Add Page
 3. Skip to the WYSIWYG editor and the toolbox on the right. Click Web Apps > Web Apps Search Form
 4. Select Glossary Web App and click Insert
 5. When the glossary web app search form has been inserted into the WYSIWYG switch to the code or html view.
 6. Near the top you'll see the form action url. Copy the ID for CCID (also is the web app id) and FID. See below for example

`<form name="catcustomcontentform98191" method="post" onsubmit="return checkWholeForm98191(this)" action="/Default.aspx?CCID=45493&FID=1051923&ExcludeBoolFalse=True&PageID={module_oid}"></form>`

CCID = 45493
FID = 1051923

----------

### Step 4. Initialize Widget


#### Settings (if assigned variable settings are removed widget will set default option)

Option | Type | Default | Description
------ | ---- | ------- | -----------
w_atoz_parent_catalog_id|string|-1| By default set to output all catalogs or update and insert the parent catalog ID to output all sub catalogs of parent catalog.
w_atoz_hide_parents|boolean|true|when setting w_atoz_parent_catalog_id to -1 to display all catalogs setting this option to true will hide parent catalogs from outputting
w_atoz_columns|string|1|outputs A to Z Catalog/Brand list in 4 columns by defaults with responsive media queries. Options include 1-4 columns. Or if you'd like more control you can update the html (/_System/Widgets/atoz-catalog-list/init.liquid) and/or css (/_System/Widgets/atoz-catalog-list/_assets/atoz.css)

#### Place initialization code on page that you would like to output A to Z Catalog/Brand List

```
{% comment -%}<!-- Settings -->{% endcomment -%}
{% assign w_atoz_parent_catalog_id = "-1" -%}
{% assign w_atoz_hide_parents = true -%}  
{% assign w_atoz_columns = "1" -%} 

{%comment-%}<!-- Init Path -->{%endcomment-%}
{% include "/_System/Widgets/atoz-catalog-list/init.liquid" -%} 
```

##### **Example outputting specific catalog sub catalogs:**

```
{% comment -%}<!-- Settings -->{% endcomment -%}
{% assign w_atoz_parent_catalog_id = "123456" -%} 
{% assign w_atoz_columns = "4" -%} 

{%comment-%}<!-- Init Path -->{%endcomment-%}
{% include "/_System/Widgets/atoz-catalog-list/init.liquid" -%} 
```
