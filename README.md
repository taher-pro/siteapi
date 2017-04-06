# Site API Module

## Features

1. As an administrative user of a Drupal 8 site you can set up a site wide API key.

2. As Anonymous/Authenticated user you can access `page` content in JSON format on your site if you have the following :

   - Site API Key
   - Node ID of the content.
   
## How to use Site API Module?

1. Enable the module via drush `drush en -y siteapi`,
2. Login in as a administrator,
3. Goto `/admin/config/system/site-information`
4. Enter the Site API key for Eg : `FOOBAR12345` and Save the Form.
5. Make sure you have  `page` type content on your site.
6. Go to the link of the format `http(s)://<sitename>/page_json/<SITEAPIKEY>/<NODE_ID>`
   
   1. `<SITEAPIKEY>` key which you entered and saved in step 4,
   2. `<NODE_ID>` - The Unique node id of the content you want to Access. Note : The content should be of type `Page`
   
   Eg : `http://localhost/page_json/FOOBAR12345/17`

## Expected JSON Output

1. Correct API Key, Node ID of a `Page` content.

`{
  "Node ID": "1",
  "title": "Sample Test Page",
  "Contents": [
    {
          "value": "<p> Sample Body. Lorem ipsum </p>"
      "summary": "",
      "format": "basic_html"
    }
  ],
  "Node Type": "page",
  "Node Access": "Granted"
}`

2. Incorrect API key . 
`[
  "Access Denied",
  "Reason : API Key Invalid"
]`

3. Non-numeric NODE_ID.
`[
  "Access Denied",
  "Reason : Invalid Node ID. Please enter numeric Node ID value only"
]
`

4. NODE_ID of a Node which does not exist or not of type `page`.
`[
  "Access Denied",
  "Reason : Node does not exist or not of type page"
]`

### References

- [Drupal 8 Form API](https://www.drupal.org/docs/8/api/form-api/introduction-to-form-api)
- [Drupal 8 Configuration API](https://www.drupal.org/docs/8/api/configuration-api/configuration-api-overview)
- [Drupal 8 JsonResponse](https://api.drupal.org/api/drupal/vendor%21symfony%21http-foundation%21JsonResponse.php/class/JsonResponse/8.2.x)
- [Drupal 8 entityTypeManager](https://api.drupal.org/api/drupal/core%21lib%21Drupal.php/function/Drupal%3A%3AentityTypeManager/8.2.x)

Overall Coding Time - 2 Hours

Coffee Intake - 1 Mug :)
