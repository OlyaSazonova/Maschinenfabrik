# Maschinenfabrik

## Task conditions

- User is able to enter a key. After clicking the button the value will be shown regarding to the key from JSON.

- Create an angular project based on typescript

- Create a nodejs project with nestJS

- Implement within the frontend an output, input textfield and button

- Create a usefull restendpoint

- Mock the JSON and create a service which finds nested values by a certain key

- If the user tries to find a value from a key which doesnt exist, the application should display: "key isnt available"

- Implement usefull unit tests for the service

- Provide application with a docker-compose setup

- Application should start without any further actions after “docker-compose –f docker-compose.yml up”

 

 

JSON:
```json
{
  "web-app":{
    "servlet":[
      {
        "servlet-name":"cofaxCDS",
        "servlet-class":"org.cofax.cds.CDSServlet",
        "init-param":{
          "configGlossary:installationAt":"Philadelphia, PA",
          "configGlossary:adminEmail":"ksm@pobox.com",
          "configGlossary:poweredBy":"Cofax",
          "configGlossary:poweredByIcon":"/images/cofax.gif",
          "configGlossary:staticPath":"/content/static",
          "templateProcessorClass":"org.cofax.WysiwygTemplate",
          "templateLoaderClass":"org.cofax.FilesTemplateLoader",
          "templatePath":"templates",
          "templateOverridePath":"",
          "defaultListTemplate":"listTemplate.htm",
          "defaultFileTemplate":"articleTemplate.htm",
          "useJSP":false,
          "jspListTemplate":"listTemplate.jsp",
          "jspFileTemplate":"articleTemplate.jsp",
          "cachePackageTagsTrack":200,
          "cachePackageTagsStore":200,
          "cachePackageTagsRefresh":60,
          "cacheTemplatesTrack":100,
          "cacheTemplatesStore":50,
          "cacheTemplatesRefresh":15,
          "cachePagesTrack":200,
          "cachePagesStore":100,
          "cachePagesRefresh":10,
          "cachePagesDirtyRead":10,
          "searchEngineListTemplate":"forSearchEnginesList.htm",
          "searchEngineFileTemplate":"forSearchEngines.htm",
          "searchEngineRobotsDb":"WEB-INF/robots.db",
          "useDataStore":true,
          "dataStoreClass":"org.cofax.SqlDataStore",
          "redirectionClass":"org.cofax.SqlRedirection",
          "dataStoreName":"cofax",
          "dataStoreDriver":"com.microsoft.jdbc.sqlserver.SQLServerDriver",
          "dataStoreUrl":"jdbc:microsoft:sqlserver://LOCALHOST:1433;DatabaseName=goon",
          "dataStoreUser":"sa",
          "dataStorePassword":"dataStoreTestQuery",
          "dataStoreTestQuery":"SET NOCOUNT ON;select test='test';",
          "dataStoreLogFile":"/usr/local/tomcat/logs/datastore.log",
          "dataStoreInitConns":10,
          "dataStoreMaxConns":100,
          "dataStoreConnUsageLimit":100,
          "dataStoreLogLevel":"debug",
          "maxUrlLength":500
        }
      },
      {
        "servlet-name":"cofaxEmail",
        "servlet-class":"org.cofax.cds.EmailServlet",
        "init-param":{
          "mailHost":"mail1",
          "mailHostOverride":"mail2"
        }
      },
      {
        "servlet-name":"cofaxAdmin",
        "servlet-class":"org.cofax.cds.AdminServlet"
      },
      {
        "servlet-name":"fileServlet",
        "servlet-class":"org.cofax.cds.FileServlet"
      },
      {
        "servlet-name":"cofaxTools",
        "servlet-class":"org.cofax.cms.CofaxToolsServlet",
        "init-param":{
          "templatePath":"toolstemplates/",
          "log":1,
          "logLocation":"/usr/local/tomcat/logs/CofaxTools.log",
          "logMaxSize":"",
          "dataLog":1,
          "dataLogLocation":"/usr/local/tomcat/logs/dataLog.log",
          "dataLogMaxSize":"",
          "removePageCache":"/content/admin/remove?cache=pages&id=",
          "removeTemplateCache":"/content/admin/remove?cache=templates&id=",
          "fileTransferFolder":"/usr/local/tomcat/webapps/content/fileTransferFolder",
          "lookInContext":1,
          "adminGroupID":4,
          "betaServer":true
        }
      }
    ],
    "servlet-mapping":{
      "cofaxCDS":"/",
      "cofaxEmail":"/cofaxutil/aemail/*",
      "cofaxAdmin":"/admin/*",
      "fileServlet":"/static/*",
      "cofaxTools":"/tools/*"
    },
    "taglib":{
      "taglib-uri":"cofax.tld",
      "taglib-location":"/WEB-INF/tlds/cofax.tld"
    }
  }
}
```

## Solution

On the main page there is an input field where you can enter any key presented and JSON format above. The result will represent all values found on the key. If there is no such key in JSON, we will get the value 'Key isn't available'. The key search is locked when the data is sent. To check it out, go to Dev Tools -> Network -> Throttling -> Presets (Slow 3G). The code is covered with unit tests. It is possible to run the application in the Docker container, navigate to the application folder, write the command docker-compose up in command line.