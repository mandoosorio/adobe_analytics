# Day 3: Hands on and Management

## Capture Information on an Event
```
s.products = ";" + _satellite.getVar('productName') + ";" + _satellite.getVar('productQty') + ";" + _satellite.getVar('productPrice');
```

In the front end code, the way the satellite will pick up these values is by looking for the digitalData object - getVar("variable") are data elements defined in analytics
Ex:


```
 var digitalData = digitalData || {};
        digitalData = {
            page: {
                pageName:"Order Confirmation Page",
                siteSection:"Checkout Section",
                server:"USA Server"
            },
	    product: {
			productEvent:"Purchase",
			productID:"201233",
			productName:"Tuxedo",
			productTotalRevenue:"2600.00",
			productTotalUnits: "1",
			productTax:"235.00",
			productPostage:"50"
	    	},		
    	};
```

result from the event:
- productName: Tuxedo
- productQty: 0.00 (because productQty does not exist in the digitalData object but 0.00 is the default value given in the analytics data element)
- productPrice: null (no default value given and no productPrice property found in the digitalData object)