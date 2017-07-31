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

### Step 3. Get Web App ID, Web App Search ID (FID) and Alphanumeric First Character Field ID

 1. In the admin under Site Manager select Pages
 2. Click Add Page
 3. Skip to the WYSIWYG editor and the toolbox on the right. Click Web Apps > Web Apps Search Form
 4. Select Glossary Web App and click Insert
 5. When the glossary web app search form has been inserted into the WYSIWYG switch to the code or html view.
 6. Near the top you'll see the form action url. Copy the ID for CCID (also is the web app id) and FID. See below for example
 7. In the inserted web app search form find the input field for custom field you created in step 2. Copy and save custom field ID for next step. See below for example.

`<form name="catcustomcontentform98191" method="post" onsubmit="return checkWholeForm98191(this)" action="/Default.aspx?CCID=45493&FID=1051923&ExcludeBoolFalse=True&PageID={module_oid}"></form>`

Web App ID (CCID) = 45493
Web App Search ID (FID) = 1051923

`<input type="text" maxlength="255" name="CAT_Custom_1" id="CAT_Custom_1" class="cat_textbox" />`

Alphanumeric First Character Field ID = CAT_Custom_1

----------

### Step 4. Initialize Widget


#### Settings (if assigned variable settings are removed widget will set default option)

Option | Type | Description
------ | ---- | ------- | -----------
w_glossary_web_app_id|string| Web App ID for Glossary Web App. Follow step 3 to retrieve this
w_glossary_web_app_search_fid|string|Web App Search ID or FID. Follow step 3 to retrieve this
w_glossary_alphanumeric_field_id|string|Web App "Alphanumeric First Character" field id. Follow step 3 to retrieve this

#### Place initialization code on page that you would like to output A to Z Catalog/Brand List

```
<!--Begin Glossary--> 
        {% comment -%}<!-- Settings -->{% endcomment -%}
        {% assign w_glossary_web_app_id = "45493" -%}
        {% assign w_glossary_web_app_search_fid = "1051923" -%}
        {% assign w_glossary_alphanumeric_field_id = "CAT_Custom_1" -%}
        
        {%comment-%}<!-- Init Path -->{%endcomment-%}
        {% include "/_System/Widgets/glossary/init.liquid" -%}         
        <!--End Glossary--> 
```

