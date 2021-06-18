---
title: Widget Creation - Example of HTML
keywords: documentation
last_updated: June 17th, 2020
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---


Here you can find a HTML template for creating a new widget. Follow these instructions.


In the head tags of the HTML we're loading the libraries usually required to consume data for the specific widget contained in the Data Card.
You are not required of using any of these libraries but you can use this doc as a reference since you have to follow the integration pattern.

```HTML
<HEAD>

<!-- Beginning Include Header -->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">

<script src="https://cdn.jsdelivr.net/npm/js-cookie@rc/dist/js.cookie.min.js"></script>
<script src="/lib/scripts/utils.js"></script>
<script src="/lib/scripts/env.js"></script>
<script src="/lib/scripts/jquery.min.js"></script>
<link href="/lib/styles/css" rel="stylesheet" type="text/css">
<link rel="stylesheet" type="text/css" href="/lib/styles/style.css">
<script src="https://unpkg.com/mustache@latest"></script>

<script type="text/javascript">
var getUrlParameter = function getUrlParameter(sParam) {
    var sPageURL = window.location.search.substring(1),
        sURLVariables = sPageURL.split('&'),
        sParameterName,
        i;

    for (i = 0; i < sURLVariables.length; i++) {
        sParameterName = sURLVariables[i].split('=');

        if (sParameterName[0] === sParam) {
            return sParameterName[1] === undefined ? true : decodeURIComponent(sParameterName[1]);
        }
    }
};
</script>

  <script>

// Retrieve auth token for URL of from the Cookies
if (getUrlParameter('token') != undefined){
  var token = getUrlParameter('token');
}else{
  var token = Cookies.get('access_token')
}

</script>

<!-- End Include Header -->

<link rel="preconnect" href="https://fonts.gstatic.com"> <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet">
  
```
While at the bottom of the html file between the </body> and the </html> clouse taags:

```HTML
<script type="text/javascript">

// environment_widget = "https://api-dev.askdata.com";
//environment_widget = "https://api.askdata.com"  // prod  da togliere quando porto su...

$.ajax({

url: environment_widget +"/smartinsight/widgets/" + getUrlParameter('widgetId'),
type: "GET",
async: false,
beforeSend: function(xhr){xhr.setRequestHeader('Authorization', 'Bearer ' + getToken() 
 ).setRequestHeader('Content-Type','application/json')},
success: function(data) { 

/// PUT YOUR CODE THAT RENDER THE WIDGET RESULTS


    }
  });
</script>

```

You can copy and extend the previous example [here].

[here]: <https://github.com/AskdataHQ/askdata-charts-components/tree/main/widgets/askdata/_widget_example/index.html>

