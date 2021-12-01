---
title: Advanced Configurations
keywords: documentation
last_updated: October 15th, 2020
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

Welcome in the Advanced Configuration. This section of the documentation is specifically designed for proficient and expert users.

##### [Dataset Advanced Configuration](/docs/dataset-advanced-configuration)

```javascript

{
   "when" : "!query.isSorted()",
   "order" : "PRICE" 
},
{
   "when" : "!query.isSortedByMeasure()",
   "order" : "PRICE ASC" 
},
{
   "when" : "!query.isSortedByDimension()",
   "order" : "PLACE DESC" 
},

{
   "when" : "!query.isSortedBy('place')",
   "order" : "PRICE DESC, PLACE ASC" 
}

```

##### [Configure a Channel](/docs/advanced-configuration-other-channels)

Learn how to configure external channels such as Slack, Skype, Messenger, Whatsapp... 

{% include links.html %}

    
