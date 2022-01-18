---
title: Data Card - Technical Model
keywords: documentation
last_updated: December 12th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

Smartfeed - Components
======================

### **Feed message components**

A Smartfeed message is composed of the following components:

```

{

   "stream":"",

   "topics":\[

   \],

   "text":"hi",

   "attachment":{

   },

   "quick\_replies":\[

   \],

   "thread":"",

   "receiver":"",

   "sender":"0ee....",

   "time":153224343222
   
```

The fields that contain the data to be shown are text, quick\_replies, attachment and sender (if message into chat view).

_Stream_

It is a label used to classify the messages. It’s possible to use every label you want excluded the reserved ones, as followed described:

· _main_: is the default, if no stream wasn’t specified during creation of the messages, they’ll take this value;

· _agent_: the default value for all messages that come from and are sent to the agent, in other words, the chat channel;

· _\_feed/{{feedId}}_: is a dynamically resolved feed channel. All messages with this value belonging to the feed with given id {{feedId}};

· _\_user/{{userId}}_: is a dynamic value resolved with the current user id. This classification is used to indicate the “inbox” channel.

  
_Thread_  
Is the id of message root of a discussion. If a user clicks on a card to show the details it’ll have the possibility to send messages to the agent regarding that specific card. All the messages exchanged with the agent after will belong to the same thread so their thread property will be valued with the root message id ([see the api](https://innaas.atlassian.net/wiki/spaces/A/pages/522256400/Comments))

_Topic_

A topic is a label associated with the card; his format is “/type/code” and it comes from the insight generation process. The type and code should be present in an ENTITY to permit to recognize the name of the topic self.  
For a card, it’s possible to give multiple topics. The user can pin a topic by clicking on the “Follow” button when the application shows it on the right side of the header. In this case, the name of the topic will be shown on the Channels menu. Of course, it’s possible to remove the pin by clicking on the topic in the channel and then by selecting the Unfollow button in the header bar.

_Attachment_

The following json is an example of attachment format:

```

 "attachment": {

            "id": "ACEA-best\_kpi",

            "domain": "ACEA",

            "type": null,

            "topics": \[

                "/generale/best"

            \],

            "code": "ACEA-best\_kpi",

            "hat": {

                "icon": "https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons/acea/aceaico.png",

                "name": "Home",

                "sponsored": false,

                "action": "smartfeed://topic/generale/best"

            },

            "header": {

                "icon": "https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons/acea/home\_blank.png",

                "title": "Best KPI",

                "notification": 0,

                "timestamp": 1527756898640,

                "action": "smartfeed://topic/generale/best",

                "action\_label": "Mostra tutte"

            },

            "body": \[

                {

                    "component\_type": "text",

                    "details": {

                        "text": "Il fatturato idrico cumulato ad aprile 2018 è in crescita del 10% rispetto all'anno precedente."

                    }

                },

                {

                    "component\_type": "cta",

                    "details": {

                        "link": "smartfeed://card/ACEA-fatturato\_cumulato\_aprile",

                        "label": "Drill down per aziende"

                    }

                }

            \],

            "footer": {

                "interaction": 0,

                "url": "smartfeed://card/best\_kpi",

                "bookmark": {

                    "count": 3,

                    "bookmarked": true

                }

            }

        }

```

The elements of an attachment are:

**Property name**

**Description**

**Mandatory**

hat

It contains generic info relative to the card like name and sponsored info

false

header

It contains the _title_, _timestamp_ and _action_ info

false

body

It contains an array of components that populate the card

true

footer

It contains the number of interaction with the card, liking information and a sharing URL

false

_id_

the unique id of the message

true

_domain_

the domain which message belong to

true

_type_

type of the message

false

_code_

code of the message (part of ID)

true

_topics_

the topic list of the message

false

### Body components

The body is an array of components. Every component has a component\_type property that qualifies the component self and a detail list. This list is specific for different component\_type but the number and quality of custom details are fixed (except for not mandatory ones)

**text**

It prints a simple text into the card.

{

   "component\_type":"text",

   "details":{

      "text":"There are more than 1031 IT requests with aging greater than 30 days in 2011."

   }

}

**image**

It prints an image addressed by the resource field, alt\_text is used in those cases when the resource field is not available.

example:
```
{

   "component\_type":"image",

   "details":{

      "resource":"https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons/isa/top11offensiveyoung.png",

      "alt\_text":"Top 11 Young - Offensive Index"

   }

}
```

#### cta

It enables a button that prints the label fields. The action is a calling to the URL contained by the link field.

example:

```
{

   "component\_type":"cta",

   "details":{

      "link":"smartfeed://card/ACEA-fatturato\_cumulato\_aprile",

      "label":"Drill down per aziende"

   }

}
```

#### Comparison

It prints two pieces of information (item) at comparison. For each item it's possible to specify the following fields:

**Property name**

**Description**

**Mandatory**

**Possible values**

label

The label that will be printed in top of the item

false

value

The value of the item

true

format

The format of data, useful to presentation issue. If the value is _string_ the value must be printed as is, no transformation

true

string/numeric/currency/time

unit

The measuring unit

only for _currency_ and _time_ format

EUR (tri-letter ISO4217) for _currency_ unit / [Date Format](http://www.unicode.org/reports/tr35/tr35-31/tr35-dates.html#Date_Format_Patterns)

markup

A simple indicator if the value is positive or not. If GOOD the value must be colored green, red in the other case

false

GOOD/BAD

description

The subtitle

false

Code xample:

```

{

   "component\_type":"comparison",

   "details":{

      "item\_a":{

         "label":"Fatturato ad aprile 2018",

         "value":"242,95 Mln €",

         "format":"string",

         "unit":"EUR",

         "markup":"GOOD",

         "description":"10% di incremento"

      },

      "item\_b":{

         "label":"Previsione fatturato 2018",

         "value":"718,88 Mln €",

         "format":"string",

         "unit":"EUR",

         "markup":"BAD",

         "description":"2% sotto l'obiettivo"

      }

   }

}

```

#### Container

It contains items

```
{

   "component\_type":"container",

   "details":{

      "image":"https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons-thumb-down@2x.png",

      "items":\[

         {

            "component\_type":"item",

            "details":{

               "title":"Incasso",

               "text":"Incasso previsto: 50.000,00 € -17.499,09 € al raggiungimento dell’obiettivo"

            }

         }

      \]

   }

}

```

**item**

The component prints a container item but it's possible to use it outside of a container

**Property name**

**Description**

**Mandatory**

icon

Icon print on this left of the line

false

title

The label print after icon

true

description

Description before action

true

action

The measuring unit

Link and URL for an action

Code Example:

```
{

   "component\_type":"item",

   "details":{

      "icon": "https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons/acea/its\_blank.png",

      "title": "NUMERO INCIDENT", 

      "description": "581",

      "action":  {

          "label" : "show", 

          "url" : "smartfeed://topic/its/workorder\_incident"

      }

   }

}

```

** Table**

It prints a table for which it's possible to specify the header columns and the row values. The maximum number of columns is 3, but it possible to use 2 ones.

**Property name**

**Description**

**Widths with 2 or 3 columns**

**Text justification**

columns

Array of string

{4/7, 3/7}, {3/7, 2/7, 2/7}

{left, centered, right}

rows

String matrix

{4/7, 3/7}, {3/7, 2/7, 2/7}

{left, right}

The text will be truncated with ... at the end of the second line.  

Code example:
```
{

   "component\_type":"table",

   "details":{

      "columns":\[

         "Oggetto",

         "Scadenza",

         "Stato"

      \],

      "rows":\[

         \[

            "N° fattura 1233143",

            "22.04.2018",

            "Non pagata +9000"

         \],

         \[

            "Anticipo Iva",

            "30.05.2018",

            "Non pagata -1000"

         \]

      \]

   }

}

```

**Horizontal Chart**

It prints a progress bar that represents the range between \[start, end\]. The value contains the percentage of progression and the bar must be colored until this value.

**Property name**

**Description**

**Type**

**Possible values**

start

the start of the range

Numeric

0

end

the end of the range

Numeric

100

value

the value of the percentage

Numeric

45

Code example:

```
{

   "component\_type":"horizontal\_chart",

   "details":{

      "start":0,

      "end":45,

      "value":100

   }

}

```

** Map**

It prints a map according to the given coordinates.

**Property name**

**Description**

**Mandatory**

center

lat and long of the map center

true

center\_on\_me

if true the map must be center of my current position, false otherwise

true

radius

the number of meters for radius

true

show\_my\_position

if true a pin on my position must be shown

true

points

list of lat and long for the different points to show

true

geo

geoJson coordinates

false

Code example:

```

{

   "component\_type":"map",

   "details":{

      "center":{

         "lat":"41.876471",

         "long":"12.465616"

      },

      "center\_on\_me":false,

      "radius":1000,

      "show\_my\_position":false,

      "points":\[

         {

            "lat":"41.881789",

            "long":"12.467728"

         },

         {

            "lat":"41.876346",

            "long":"12.465314"

         },

         {

            "lat":"41.875301",

            "long":"12.465470"

         }

      \],

      "geojson":{

         "features":\[

            {

               "geometry":{

                  "coordinates":\[

                     12.33845213,

                     45.43490485

                  \],

                  "type":"Point"

               },

               "properties":{

                  "\_\_fillAlpha":0.5,

                  "\_\_fillColor":"#266ff2",

                  "\_\_radius":6.0,

                  "\_\_strokeColor":"#266FF2",

                  "\_\_strokeWidth":2.0,

                  "some property":"value"

               },

               "type":"Feature"

            }

         \]

      }

   }

}

```

**_geoJson_** coordinates follow the geoJson standard format (please see [https://en.wikipedia.org/wiki/GeoJSON](https://en.wikipedia.org/wiki/GeoJSON))

It’s possible to use `Point`, `LineStrig`, `Polygon`,`MultiPoint`, `MultiLineString`, `MultiPolygon` and`GeometryCollection` features.

In the `properties` it’s possible to specify the value of custom property in order to show that in the tooltip when users will tap over the Feature.

Apart from custom properties, there are the styles one as visible into the example, their name are reserved

**Style property name**

**Description**

**Feature Type**

**Mandatory**

\_\_fillAlpha

the alpha factor for color

Point

true

\_\_fillColor

the main color

Point

true

\_\_radius

the size of element

Point

true

\_\_strokeWidth

how big is the border

Point

true

\_\_strokeColor

the color of the border

Point

true

  
**Message Visibility**

In the main view two particular feeds are available:

· Home

· Inbox

In the home, all the messages from the public feed are visualized together with those messages belong to the feed specified into _include_ strategy specified into FeedConfiguration.  
In the inbox all the messages that have been directed to the logged user.  
They are visible because the owner is “agent”. So every feed with ownership of agent will be visible in the bar beside Home and Inbox.

A custom feed could be created by a user during the sharing rule process and by agent, when it connects a dataset. By default a “dataset” feed is public but a “user-defined” feed not, it is visible to the owner when he clicks on his channels.

Meteo and Sport are private channel

![](file:///C:/73be7d58103eee3db24599b5c31d990c)

MYSQL is a public channel

![](file:///C:/56e374c58c1454d94915e428f0ba1c8f)

It is possible to publish a user-defined feed changing the following property inside of feed collection:

"published":true

By setting it to true the related highlight will be shown on the main page of the feed.

_What is visible on the main page of feed?_

The main feed returns all messages belonging to all feed created by the current user (check owner property in the related feed document), all those messages belonging to the feeds marked as published and all messages whose stream is dynamically resolved through the inclusion/exclusion in the configuration of feed stored in the feed collection.

1. get all messages of feeds I created (the owner in feed document contains my user id)

2. get all messages of published feed (the feed of other users as well)

3. get all messages with the stream is in the range of streams dynamically resolved in the feed home

4. if nothing is retrieved all messages with “main” stream will be retrieved

5. zero card is returned if no messages are found using the logic 1..4

Home and Inbox are two special kinds of feed always present by default. They are printed at the top of the main view because their owner is “agent”. So if you want to add a new feed in that bar the owner of this feed should be “agent”.

### **Sharing rule**

…

### **Search**

The search is made possible through multiple instances of the ElasticSearch index.

For every index, there is a Searcher object responsible for searching, suggestions and in some cases the indexing document.

**Index name**

**Description**

**ElasticSearch index name**

**Produce suggestions**

**Component**

Topic

It stores measure only

“feed\_index”

true

Entities

It contains the _title_, _timestamp_ and _action_ info

"state.smartbot.flatentity"

true

ElasticEntityMeasureSearcher

UserQuery

It contains all the queries made by users and it is interrogated to produce the “previous query” in the search item result

"events.smartbot.user\_query"

false

ChainSearcher:{  
ElasticUserQuerySearcher, ElasticDiscoveryQuerySearcher}

_For developers_

`SearchConfiguration` class is responsible for the building the Chain of the searcher used when a search is performed.`ChainSearcher` is a kind of searcher that contains different Searcher and executed.

_Search and Browse special item_

There are two special search result items with subtitle “Search” normally returned as the first result only when the user input is not empty. Clicking on it, it possible ask the given input directly to the agent.

The second is “Browse” of Question catalog that shows the list of Discovey entry in the same view. Note it appears in the first result position if the user hasn’t typed any text. In all the other case (when the results are returned) is returned on the last position.

![](file:///C:/e976a1460fc5e7419688250807285348)

_Search and Browse with no results_

![](file:///C:/95e9d81e467a254ebae03a846a180993)

_Browse in the last position_

_Suggestions_

The horizontal suggestions are suggested from search and they can contain measure and entities as shown in the figure:

![](file:///C:/903901453d120176cdc5e875a0edf016)

**_Measures_** _suggested: total spend on pos, price_

![](file:///C:/e061418eb49d7744868fb692f822d082)

**_Entity_** _suggested: restaurant, residentia-residential_

_Total spend on pos, price, waiters_ are some of the measures suggested automatically.

In particular, the horizontal suggestions come from the `ElasticEntityMeasureSearcher` executing the following logic:

1. if the user input except spaces is empty it returns measures (case 1)

2. if the user input has some tokens it returns a list of entities. If the last token is not empty it will use the _matchPhrasePrefixQuery_ operator (case 2)

3. if the list of entities is empty it tries to return a list of ENTITY using _matchPhrasePrefixQuery_ operator.

Configuration
=============

### **Agent**

Every time an agent is being created a new configuration on feed is created as well. The configuration is present in feedConfiguration Mongo collection. The feedConfiguration document contains the property that customizes the behavior of that feed.

Property configuration

**Name**

**Description**

**Type**

visible

If true, the agent can be accessed to everyone, anonymous included. Otherwise, the connection is possible only with a valid token. This property is automatically set by the system when the permission for anonymous users is being changed on the relative agent (see Kafka ShareAgentStream event streaming).

Boolean

InitCommand

If set, when a user asks the initial (empty) history of messages exchange with the agent, that text contained by this property is sent to the agent and so triggers a chat.

String

forYou

It true, the channel “For you” is enabled, which means that messages will be sent to it. What about its visibility depends on forYouHidden.

Boolean

forYouHidden

It false, the “For you” is enabled is visible In the list of channels seen by users.

Boolean

### **FeedSetting**

Every feed has a configuration stored into feed collection. The following extract contains the inclusion/exclusion logic used to determine if what messages must have to be considered in the feed retrieval. In the example, will be considered all messages that have stream with value: `_feed/BA44E597`, but not `"agent"`.

...

"streams" : {

        "include" : \[

            "\_feed/BA44E597"

        \], 

        "exclude" : \[

            "agent"

        \]

 },

"code" : "test1",

"published": true

...

In particular, that feed is public (cause of `"published": true` property) so its messages will be shown in the main feed.

**Name**

**Description**

**Type**

suggestedFeeds

The list of channel slugs that configurator wants they are suggested on the the home.

Array

suggestedQueries

The list of channel slugs that configurator wants use a source of query suggested into discovery.

Array

InitCommand

If set, when a user asks the initial (empty) history of messages exchange with the agent, that text contained by this property is sent to the agent and so triggers a chat.

String

forYou

It true, the channel “For you” is enabled, which means that messages will be sent to it. What about its visibility depends on forYouHidden.

Boolean

forYouHidden

It false, the “For you” is enabled is visible In the list of channels seen by users.

Boolean

  
**SuggesteFeeds**  
The visibility of suggested feeds follows the check of two parameters:

· user’s authentication (anonymous or logged)

· the presence of suggestion

**Feed visibility in home**

**user logged**

**anonymous**

**no suggestion**

the user’s feeds (public and private)

all public feeds

**suggestion**

suggested feeds before the user’s feeds

public between those suggested

Note: deletes and updates are available only to the owner of Feed
