# How it works?
- First when you open the page iframe source is set to a custom page called instance launcher. It will send a request to instance manager , instance manager either creates a new instance or starts one of reserved ones (starting is faster than creating new one) and waits until its online then it will return its address to instance launcher.

- Instance launcher then awits until page is fully functional then it will change iframe source to that page (Iframe source changes from Instance Launcher to pixel streaming page so job of instance launcher is done here).

- In the pixel streaming page system will send heartbeats to Instance Manager to notify that instance is still being used . when last heart beat reaches a max time server will turn off (or terminate based of config ) that instance.
