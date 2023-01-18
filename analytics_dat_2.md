# Day 2: Hands-On

### Rules
- naming convention: 06-02 All Pages Rule (90) : the (90) will rank the rule so that it executes after all the numbers before it
- Page Bottom event type triggers when you are about to leave the page

### Data Element Viewer Browser Script
https://jimalytics.com/implementation/data-element-viewer-for-adobe-launch/

``` javascript:(function(){if('undefined'!=typeof _satellite)if(void 0!==_satellite._container){var dataElementValue,dataElementNames=[],dataElementObject={},cleanElementObject={};function checkDataElements(){for(var e in _satellite._container.dataElements)dataElementValue=_satellite.getVar(e),dataElementNames.push(e),''===dataElementValue&&(dataElementValue=' '),dataElementObject[e]=dataElementValue,''!==_satellite.getVar(e)&&_satellite.getVar(e)!==_satellite._container.dataElements[e].defaultValue&&(cleanElementObject[e]=dataElementValue);return{everything:dataElementObject,clean:cleanElementObject}}function displayDataElements(e,t){console.group('RAW Data Elements - Data Element Viewer by Jimalytics - https://jimalytics.com'),console.table(e),console.groupEnd(),console.group('CLEAN Data Elements - Data Element Viewer by Jimalytics - https://jimalytics.com'),console.table(t),console.groupEnd()}function returnData(){var e=checkDataElements();displayDataElements(e.everything,e.clean)}returnData(),window._satellite=window._satellite||{},window._satellite._monitors=window._satellite._monitors||[],window._satellite._monitors.push({ruleTriggered:function(e){returnData()}})}else console.log('Adobe Launch is not present.');else console.log('Adobe Launch is not present.');})(); ```
- right click bookmark section and add a page, paste this script in url field

## Introduction to Custom Traffic Variables
- s.props behave the same as a predefined traffic variable (pageName, channel, server info)
- s.props used for pathing
- can be used for holding values for internal search terms, scope of search, number of search results, etc
- grouping: s.prop22 = Home > Category > Subcategory > Product || useful to keep track of the journey
- in conversion variables config settings, enable "Path Reports"
### Traffic Variable Code in Action
``` 1. First View
s.pageName = "Home Page"
s.channel = "Home Page"
s.prop20 = "Gold"

2. Second View
s.pageName = "Electronics"
s.channel = "Electronics"
s.prop20 = "Gold"

3. Third View
s.pageName = "Electronics: Sony TV"
s.channel = "Electronics"
s.prop20 = "Gold"

4. Fourth View
s.pageName = "Men: Activewear"
s.channel = "Men"
s.prop20 = "Gold" 
```
