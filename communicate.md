## Communicate From UE4 to WebPage
- Sending from UE:  
![](https://docs.pixelsteam.net/Images/uetopage.jpg)
- Receiving in page:
![](https://docs.pixelsteam.net/Images/pagerec.jpg)

## Communicate From Web Page to UE4 

- Sending from page 

Example : inside instanceinterface.js

```
    var Command={
    "SomeField": "SomeEvent",
    "X":width,
    "Y":height
    
    }
    var Frame=   document.getElementById("PixelFrame");
    Frame.contentWindow.postMessage(JSON.stringify(Command), PageURL); 
    
```
- Receiving in UE4
 
 If you have pixelmanager installed you can bind to this event to recive messages from web page. 
 ![](https://docs.pixelsteam.net/Images/pixelinput.jpg)
 
