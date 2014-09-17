scripture-service
=================

JSNode service for retrieving bible scripture in a supported language with a pretty picture.

#Usage
The scripture service depends on StrongLoop.  To install strong loop make sure that you have python 2.7 as it will use it.
See http://strongloop.com/ for more details.

In the server/config.json file, replace "dbpApiKey" with your API key you got from the Digital Bible Platform.

After which in the command prompt simply type in "slc run" to get the service up and running.

##Request Parameters

There are four main parameters when using the scripture service (outside of the strongloop api/explorer).

Parameter  | Type | Subtype | Description | usage | required
------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
id  | integer | path parameter | The id is associated with a specific verse  | [base_url]\[id] | Yes |
l  | string | url parameter | The desired language for the memory verse.  The language must be in the 3 character Digital Bible Platform format. | [base_url]\[id]?l=[language] | Yes |
d | integer | url parameter | A number corresponding to the day of the year, ideally 1 - 366, which will fetch an image associated with that day. | [base_url]\[id]?l=[language]&d=1 | No |
html | boolean | url parameter | A value indicating whether to generate a sharable webpage rather than JSON | [base_url]\[id]?l=[language]&html=true | No |

Note:  The day parameter is not required only because it will use a default image.

## Response

The response will be in the form:

```JSON
{
    scripture: "Scripture verse",
    reference: "Reference",
    image: "image path",
    dbp: {
        fullLink: "http://dbt.io/text/verse?v=2&key=[dbpApiKey]&book_id=Matt&chapter_id=1&verse_start=1&verse_end=2&dam_id=ENGESVN2ET"
    }
}
```

#Notes
* Multiple versions is not supported, though some of the code is there (currently commented out).  Because this is build on the Digital Bible Platform, languages can be associated with versions. As it stands, assign a default version with the language based on the Digital Bible Platform.
* Because of time constraints, html is currently a parameter.  It should really be separated from the response.