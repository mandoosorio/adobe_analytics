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

### Internal Search Term Capture
- create data element
- extension: core
- data element type: query string parameter
- force lowercase value true
- clean text true
- storage duration: pageview
- url query string value: q
- allow capitalization differences: true
- create/edit rule
- set variables: eVar -> data element
- set prop: prop -> duplicate from eVar

- we use an evar to store the value and transfer it into a prop because the eVar will let us hold larger strings (100 char) and if they are duplicated to a prop, the prop length restriction doesn't apply

## Campaign Conversion
Campaign Variables
- reports can be named "Customer Aquisition", "Identify Referrer Type (by Country)
- referrer type is link that resulted in page visit
- campaign: set of actions that lead to an event/action
- capture tracking codes
- set tracking code to a specific landing page
- access tracking code in the query string of the url

```
s.campaign = "tracking code"
s.campaign = "radio_spot_xyz"
```

Use of campaign is used to tell us what is the most affective way to attract a user to a page
- from emails, ads, promos, etc
- purpose is to bring more traffic into webiste
- campaigns will tell us how/best way

### Internal vs External Campaigns
Internal
    - drive traffic to one part of your website from another part, or is a "call to action"
    - should be tracked with a custome conversion variable
    - data element for internal campaign will be of type query string parameter with value "intcmp"
External
    - drive traffic from another source completely outside of your website
    - should be tracked with the campaign variable
    - is a default variable that exists, go to rule and set the campaign to query parameter: cid

