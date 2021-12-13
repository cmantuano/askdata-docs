---
title: Advanced Configuration - Other channels
keywords: documentation
last_updated: October 15th, 2020
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

# SmartUI configuration
## Schema definition
An object can be described by a schema, the schema is used to handle the communication between FE and BE via REST endpoint and also it guides the UI composition.
An example of schema definition is the following:

```json
    {
    	"fields" : [
    	{
	      "code" : "code",
	      "label" : "Entity Code",
	      "type" : "string",
	      "viewType" : "text",
	      "readOnly" : false,
	      "mandatory":true,
          "settings" : {
             "validation" : {
                "regex" : "^[A-Za-z0-9]{3,7}$", 
                "errorMessage" : "The name length should be in the range 3 - 7"
              }
           }
	    },
	    {
	      "code" : "details",
	      "label" : "Details",
	      "type" : "object",
	      "viewType" : "json",
	      "readOnly" : false,
	      "mandatory": true
	    },
	    {
	      "code" : "synonyms",
	      "label" : "Synonyms",
	      "type" : "array",
	      "viewType" : "array",
	      "readOnly" : false
	    },
        {
            "code" : "settings.enableValues", 
            "label" : "Enable Values as default", 
            "type" : "boolean", 
            "readOnly" : false, 
            "defaultValue" : true, 
            "viewType" : "dropdown", 
            "settings" : {
                "items" : {
                    "fixed" : [
                        {
                            "value" : true, 
                            "label" : "Yes"
                        }, 
                        {
                            "value" : false, 
                            "label" : "No"
                        }
                    ]
                }
            }, 
            "tooltip" : "Enable or not the values"
        }]
	}
```
 
###  Schema configuration

| Property      | Description |  Possibile values |
| ------------- | ------------- | ------ |
| code | It denotes the field that will be produced for a POST/PUT call | Any string |
| label | It denotes the label that will be showed in the UI| Any string |
| type | It denotes the the data type that will be produced for a POST/PUT call| string,boolean,array,number,date, object |
| viewType | It denotes the type of component that should be showed in the form view | text, date, textarea, list, array, json, image |
| readOnly | It indicates if the field can be modified/edited in form | true/false, false by default |
| disabled | It indicates if the field is disabled in form | true/false, false by default |
| mandatory | It denotes if the field must be validated in the UI | true/false, by default it is false |
| defaultValue | The default value for the field | it relates to the field type nd viewType|
| placeholder | Text shown on the field before the user start to input data | Any string |
| tooltip | Text shown when hover on the i icon | Any string |
| settings | Some specific settings for a field | See examples below |

### Settings items

Items, used for the dropdown list, can be ```fixed``` or ```rest``` triggered and filled through an event

```json
 "settings" : { 
    "items" : {
       "fixed" : [
          {
             "value" : true, 
             "label" : "Yes"
          }, 
          {
             "value" : false, 
             "label" : "No"
          }
       ]
    }
 }
```

```json
 "settings" : { 
    "items" : {
       "rest" : {
          "triggerEvent" : "loadConnections", 
          "endpoint" : "https://smartbot.askdata.com/connections/types", 
          "method" : "GET", 
          "valueField" : "code", 
          "labelField" : "label"
       }
    }
 }
```

### Settings string validation

```json
 "settings" : {
    "validation" : {
       "regex" : "^[A-Za-z0-9]{3,7}$", 
       "errorMessage" : "The name length should be in the range 3 - 7"
    }
 }
```

### Components

| Component | Description | Special settings |
| --- | --- | --- |
| text | A simple text field | "pattern": a regex the will validate the text in input, "format": "phonenumber" -> on mobile apps the keyboard should show only numbers. Possible values: 'phonenumber', 'email', 'number'| 
| date |  A date time picker, the FE will send the time as an epoch value | |
| textarea |  A multi line text field | pattern: a regex the will validate the text in input |
| dropdown |  A dropdown component | items: The items to be used to populate the dropdown, multi: Indicates if the user can select one or multiple choices (true/false, false by default) |
| array | An array of elements | 
| json | A widget that let the user to input a json document |
| image | A widget that let the user to upload an image |
| stepper | A widget that let the user select an amount via a "+" and "-" button | 'step': 1. It indicates the step that has to be taken for each tap on the plus/minus button |
| slider | A widget that let the user select a value between a fixed range | maxValue and minValue, which set the slider boundaries |
| radio | A radio input | items: The possible choices to select from in the format: {"code":"some_code","description":"Some description"} |
| checkbox | A checkbox input | items: The possible choices to select from in the format: {"code":"some_code","description":"Some description"} , the selected options will result in an array |
| colorpicker | A colorpicker | |


#### Component examples:

* text

 ```json
    {
      "code" : "field_code",
      "label" : "Input your value",
      "type" : "string",
      "viewType" : "text",
      "readOnly" : false ,
      "placeholder": "placeholder",
      "settings":{
      	  "regex":"^[a-zA-Z ]*$",
      	  "format": "phonenumber"
      }
    }
 ```
 
 Produced json output:
 
 ```json
  {
    "field_code": "Some value"
  }
 ```
 

* date

 ```json
    {
      "code" : "time",
      "label" : "Time",
      "type" : "date",
      "viewType" : "date"   
    }
 ``` 
 
 Produced json output:
 
 ```json
 {
 		"time": 123123981212
 }
 ```
 
* textarea

 ```json
	    {
	      "code" : "a_long_text",
	      "label" : "Input you text",
	      "type" : "string",
	      "viewType" : "textarea"
	    }
 ``` 
 Produced json output:
 
 ```json
 {
 		"a_long_text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
 }
 ```
  
* dropdown (fixed items)

 ```json
	    {
	      "code" : "field",
	      "label" : "Select your choice",
	      "type" : "string",
	      "viewType" : "dropdown",
	      "settings":{
	        "multi":true,
	      	 "items": {
	      	 	"fixed" : [
   	      	 	  {"value":"choice_1","label":"Desc 1"},
	      	 	  {"value":"choice_2","label":"Desc 2"}
	      	 	]
	     	 ]
	      }
	    }
 ``` 
 Produced json output:

 ```json
 {
 		"field": "choice_1"
 }
 ```
 
* dropdown (dynamic items)

 ```json
	    {
	      "code" : "field",
	      "label" : "Select your choice",
	      "type" : "string",
	      "viewType" : "dropdown",
	      "settings":{
	      	 "items": {
	      	 	"rest" : {
	      	 		"endpoint": "/getItems",
	      	 		"valueField":"code",
	      	 		"labelField":"name"
	      	 	}
	     	 ]
	      }
	    }
 ``` 
 Produced json output:

 ```json
 {
 		"field": "choice_1"
 }
 ```
 
* dropdown with muiltiple choice (set multiple field in settings as true)
```json
 {
            "code" : "languages", 
            "label" : "Enabled Languages", 
            "type" : "string", 
            "readOnly" : false, 
            "viewType" : "dropdown", 
            "mandatory" : true, 
            "settings" : {
                "multiple" : true, 
                "items" : {
                    "rest" : {
                        "triggerEvent" : "loadLanguages", 
                        "endpoint" : "https://smartbot-dev.askdata.com/languages", 
                        "method" : "GET", 
                        "valueField" : "code", 
                        "labelField" : "label"
                    }
                }
            }
}, 
  ```

* dropdown (items with dependency)

 This dropdown is loaded after another component, {{code}} is the value retrieved from another component

 ```json
	    {
	      "code" : "field",
	      "label" : "Select your choice",
	      "type" : "string",
	      "viewType" : "dropdown",
	      "settings":{
	      	 "items": {
	      	 	"rest" : {
	      	 		"endpoint": "/getItems/{{action}}",
	      	 		"valueField":"code",
	      	 		"labelField":"name"
	      	 	}
	     	 ]
	      }
	    }
 ``` 
 Produced json output:

 ```json
 {
 		"field": "choice_1"
 }
 ```
  
* array

 ```json
	    {
	      "code" : "field",
	      "label" : "Input your values",
	      "type" : "array",
	      "viewType" : "array"
	    }
 ```   
  Produced json output:

 ```json
 {
 		"field": ["input_1","input_2"]
 }
 ```
 
* json

 ```json
	    {
	      "code" : "json_field",
	      "label" : "Input your json",
	      "type" : "object",
	      "viewType" : "json"
	    }
 ```   
  Produced json output:

 ```json
 {
 		"json_field": { "field_1":"value_1","field_2":"value_2"} 
 }
 ```
* image

 ```json
	    TBD
 ```   
  Produced json output:

 ```json
 {
 		TBD 
 }
 ```
* stepper

 ```json
	    {
	    	"code":"value",
	    	"label":"How many items would you like to buy?",
	    	"type":"number",
	    	"viewType":"stepper",
	    	"settings":{
	    	   "step": 0.5,
	    		"minValue":0,
	    		"maxValue":100
	    	}	
	    }
 ```   
  Produced json output:

 ```json
 {
 	"value":"25"
 }
 ``` 
* slider

 ```json
	    {
	    	"code":"value",
	    	"label":"How many items would you like to buy?",
	    	"type":"number",
	    	"viewType":"slider",
	    	"settings":{
	    		"minValue":0,
	    		"maxValue":100
	    	}	
	    }
 ```   
  Produced json output:

 ```json
 {
 	"value":"25"
 }
 ```  
* radio

 ```json
	    {
	    	"code":"value",
	    	"label":"Select your option",
	    	"type":"string",
	    	"viewType":"radio",
	    	"settings":{
	    		"items" : {
                "fixed" : [
                    {
                        "value" : "choice_1", 
                        "label" : "Desc 1"
                    }, 
                    {
                        "value" : "choice_2", 
                        "label" : "Desc 2"
                    }
                ]
            }
	    	}	
	    }
 ```   
  Produced json output:

 ```json
 {
 	"value":"25"
 }
 ```   
 
* checkbox

 ```json
	    {
	    	"code":"values",
	    	"label":"Select your options",
	    	"type":"string",
	    	"viewType":"checkbox",
	    	"settings":{
	    		"items" : {
                "fixed" : [
                    {
                        "value" : "choice_1", 
                        "label" : "Desc 1"
                    }, 
                    {
                        "value" : "choice_2", 
                        "label" : "Desc 2"
                    }
                ]

	    	}	
	    }
 ```   
  Produced json output:

 ```json
 {
 	"values":["option1","option2"]
 }
 ```   
 
 
* colorpicker

 ```json
    {
      "code" : "field_code",
      "label" : "Select a color",
      "type" : "string",
      "viewType" : "colorpicker",
      "readOnly" : false 
    }
 ```
 Produced json output:
 
 ```json
 {
 		"field_code": "#4286f4"
 }
 ```

### Buttons, actions and events

| Component | Description |
| --- | --- |
| Navigation button  | It is used to let the user navigate through the various sections of a formView |

### Navigation buttons 
  * Exit from the form
   ```  "settings":{ "action" : "cancel", "label" : "Annulla" } ```

  * Go one step back in the sections
   ```"settings":{"action" : "prev", "label" : "Annulla"} ```
  * Go one step forward in the sections
   ``` "settings":{ "action" : "next", "label" : "Annulla"} ```
 
 
## FormView Configuration
The formView allows to show / hide schema elements, and also introduce event buttons, properly in a form mode 

```json
    "formView" : {
        "savable" : true,                                
        "dataUrl" : "http://smartbot.askdata.com/getData",  
        "saveUrl" : "http://smartbot.askdata.com/saveData",
        "saveMethod" : "PUT",
        "events" : [
            {
                "type" : "rest", 
                "name" : "produceInsight", 
                "settings" : {
                    "endpoint" : "https://smartbot.askdata.com/insight/{{domain}}/{{dataType}}/{{_object.process}}", 
                    "method" : "POST", 
                    "body" : {

                    }
                }
            }
        ], 
        "onLoad" : {
            "fireEvents" : [
                "loadAgents"
            ]
        }, 
        "sections" : [
            {
                "title" : "Edit settings", 
                "elements" : [
                    {
                        "code" : "label", 
                        "type" : "field",
                        "label" : "My Label" 
                    },
                    {
                        "code" : "produce_insight", 
                        "type" : "action", 
                        "settings" : {
                            "label" : "Produce Insight", 
                            "fireEvent" : "produceInsight"
                        }
                    },
                    {  
                        "code":"confirm",
                        "type":"action",
                        "settings":{  
                           "label":"Conferma",
                           "role": "SUBMIT"
                        }
                     },
                     {  
                        "code":"cancel",
                        "type":"action",
                        "settings":{  
                           "label":"Cancel",
                           "role": "CANCEL"
                        }
                     },
                     {
                        "type" : "action", 
                        "settings" : {
                            "label" : "Synchronization", 
                            "role" : "FORM_VIEW", 
                            "extraData" : {
                                "schemaUrl" : "https://smartbot.askdata.com/schemas/INNAAS/dataset/sample_sync", 
                                "formViewUrl" : "https://smartbot.askdata.com/uiconfiguration/formView/INNAAS/dataset/sample_sync", 
                                "dataUrl" : "https://smartbot.askdata.com/datasets/{{datasetId}}/schedule", 
                                "saveUrl" : "https://smartbot.askdata.com/datasets/{{datasetId}}/schedule", 
                                "enabledUrl" : "https://smartbot.askdata.com/datasets/{{datasetId}}/enabled"
                            }
                        }
                    }
                ]
            }
        ]
    }
```
 
### FormView main fields

| Field | Description |
| --- | --- |
| savable | Will show / hide the Save button; default as true |
| dataUrl | Formerly a GET to collect data |
| saveUrl | Formerly a POST / PUT to save data |
| saveMethod |  Possible values : POST / PUT |
| onLoad |  Object that allows firing events when loading the form |
| sections |  The list of sections for the formView |
| events |  Arrays of defined events |


### Use of placeholders in FormView

Some of the most common placeholders are mapped on FE,  e.g. ```{{domain}}``` or ```{{dataType}}``` ; moreover, it's possible to reference elements of the related schema using 
``` _object.codeOfTheSchemaField: ``` -> e.g. ```{{_object.process}}``` , where the schema has a field with ```"code" : "process"```

   
### FormView Event

```json
    "events" : [
                {
                    "type" : "rest", 
                    "name" : "produceInsight", 
                    "settings" : {
                        "endpoint" : "https://smartbot.askdata.com/insight/{{domain}}/{{dataType}}/{{_object.process}}", 
                        "method" : "POST", 
                        "body" : {
                        }
                    }
                }
            ]
```

| type | Description | Settings |
| --- | --- | --- |
| rest | The kind of event | - | 
| name | The name of the defined event | - |
| settings | The settings map to configure the event |  "endpoint" : "http://smartbot.askdata.com/insight/{{domain}}/{{dataType}}/{{_object.process}}", "method" : "POST", "body" : { } |

### onLoad object

It contains the ```fireEvents``` array of strings listing the actions to execute when loading the formView
    
```json
    "onLoad" : {
        "fireEvents" : [
            "loadAgents"
        ]
    }
```

### FormView Section Elements

| Element type | Description | Settings |
| --- | --- | --- |
| field | A simple element that map a schema field , using the same "code" | | 
| action | Will be represented as a button | "label": the label of the button , "fireEvent": the reference to the event name in the events array| 
| settings | The settings for the action element |  "label":"Cancel"; "role" -> Possible Values are ```CANCEL```, ```CONFIRM```, ```FORM_VIEW```  ; "extraData"|


### FORM_VIEW Action Extradata

| Field | Description |
| --- | --- |
| schemaUrl | The URL of the subsequent schema to use |
| formViewUrl | The URL of the subsequent formView to use | 
| dataUrl | The URL for getting data for the subsequent form |
| saveUrl | The URL for saving data for the subsequent form |
| enabledUrl | The URL for enabling / disabling the current action button |

## TableView Configuration

```json
"tableView" : {
        "onLoad" : {
            "fireEvents" : [
                "loadAgents"
            ]
        }, 
        "filter" : "server", 
        "readOnly" : true, 
        "columns" : [
            {
                "code" : "id",
                "label" : "My Id"
            }, 
            {
                "code" : "type",
                "settings" : {
                    "getLabels" : {
                        "rest" : {
                            "endpoint" : "/agent/types/id", 
                            "valueField" : "code", 
                            "labelField" : "label"
                        }
                    }
                }
            }, 
            {
                "code" : "name"
            }
        ]
    }
```
 
### TableView main fields

| Field | Description |
| --- | --- |
| filter | Specify the filtering side; Possible values: ```server```, ```client```; default is ```client``` |
| onLoad |  Object that allows firing events when loading the form |
| readOnly | Will render the table as readOnly or not; default as false |
| columns |  The list of columns for the tableView |

### onLoad object

It contains the ```fireEvents``` array of strings listing the actions to execute when loading the tableView
    
```json
    "onLoad" : {
        "fireEvents" : [
            "loadAgents"
        ]
    }
```

### Settings getLabels

Labels, used for the dropdown list, used as ```rest```

```json
"settings" : {
   "getLabels" : {
      "rest" : {
         "endpoint" : "/agent/types/id", 
         "valueField" : "code", 
         "labelField" : "label"
         }
    }
}
```
