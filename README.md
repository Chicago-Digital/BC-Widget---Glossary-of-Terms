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

#### Dependencies
**jQuery is required for this widget to work. Please make sure your page or template that will be outputting the glossary of terms already has jQuery installed or insert it before your initialization code**

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>


#### Settings (all settings are required for widget to work)

Option | Type | Description
------ | ---- | -----------
w_glossary_web_app_id|string| Web App ID for Glossary Web App. Follow step 3 to retrieve this
w_glossary_web_app_search_fid|string|Web App Search ID or FID. Follow step 3 to retrieve this
w_glossary_alphanumeric_field_id|string|Web App "Alphanumeric First Character" field id. Follow step 3 to retrieve this

#### Place initialization code on page that you would like to output Glossary of Terms

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

### Other considerations or optional settings (advanced)
1. When you upload your widgets folder /_System/Widgets/glossary a new page will be uploaded /_System/Widgets/glossary/_ajax/glossary.htm and this will create a new page on the server. When new pages are uploaded via sftp instead of being added via the admin the page name defaults to the name of "untitled" it is recommended you update this to "Glossary Search". Also, this page will default to not having a template defined. This is okay but for optimal performance it is recommended you create a blank template with "No HEAD elements" checked (under more options when creating a template). Then assign this glossary.htm page to this template so that no BC css or javascript files are injected on to the page.
2. If you want to make any updates to the styling of the glossary of terms the css file can be found at the following path: /_System/Widgets/glossary/_assets/css/glossary.css or you can choose to override the styling in your own css files
3. If you want to make any updates to the list layout of terms you can find the list layout at the following path: /_System/Widgets/glossary/layouts/glossary-list.tpl
