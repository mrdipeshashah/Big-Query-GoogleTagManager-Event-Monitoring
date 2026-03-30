This repository contains Big Query code using Google Analytics raw data tracking the health of events via Google Tag Manager. Tags are critical in the GTM set-up but the common theme with all platforms is the event/trigger which is used by Google Ads, Meta, Google Analytics etc. The focus is on event performance that can be diagnosed by any of the different teams working with the different platforms. 

I have developed a looker studio dashboard (https://lookerstudio.google.com/reporting/b3d4ac15-0583-4b5a-a083-32bdbd41d6ca) that brings the insights to life. 

The steps required:

1. To be able to generate the data to build the dashboard it requires implementing this GTM container > https://github.com/GTMRecipeContainers/Google-Analytics-4-Enhanced-E-commerce it will require configuring the triggers + GA4 event tag that works best for the website
2. Google Analytics is connected to Big Query
3. The 2 Big Query code provided, create and save the views in Big Query
4. Make a copy of the looker studio dashboard and connect it to the saved views

Watch-Outs: 

1. To be able to monitor the performance of Google Analytics tags the most important is the architecture of each tag that is shared in the GitHub GTM link provided above. Each GA-GTM event tag requires adding the following event parameters: tag_name, tag_catgeory and tag_date_creation. These are additional info that will be available in Big Query for each event/tag. To be able to monitor the performance correctly having these event parameters correclty inputted will provide far greater insights
2. The Event Variable Settings shared in the GitHub GTM link provided above should be a default for every GA4 event tag in Google Tag Manager. The Event Variable Settings has the following event parameters: container_id, container_version and timestamp, container_id + container_version are coming from built-in variables where timestamp is coming from a user defined variable which can be found in the GitHub GTM container. These provide addtional rich information in Big Query for each event.tag. Once the Event Variable Settings are set it should not be changed unless addtional event parameters are being added  
3. The one addition the dashboard will need is adding in Health Status in the audit log table + the scorecards under unhealthy tags, Add Field > Add Calculated Field > Label Health Status > Copy the below and change the tag name and requirements


  
