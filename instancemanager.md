# Instance Manager

- Instance Manager is a minimal server that reduces costs by turning on servers on demand!

- Requests that you can call on instance manager (in form of ` https://instancemanageraddress/request `)

## /Check
To check if server is online 

## RequestNewInstance 
- Params : ami 

- example : https://server.pixelsteam.com/RequestNewInstance?ami=2jsdoo2ms9

Will create an instance based of AMI provided , will destroy it after being used.


## RequestReserveInstance 

- Params : ami 

- example : https://server.pixelsteam.com/RequestReserveInstance?ami=2jsdoo2ms9

Will start an reserverd instance ,will turn it off after being used. Reserved instances must have `Reserved` tag . Reserved instance are usually twice faster to start but they have monthly cost of storage which is around 30$ for 10 instances (30gb) .use aws calculator to estimate your cost .

## RequestSharedInstance

- Params : ami 

- example : https://server.pixelsteam.com/RequestSharedInstance?ami=2jsdoo2ms9

Will return an online shared instance or will start a reserved instance if didn't found any. Shared instances must have tag `Reserved`. Shared instances must have tag name `MaxUsers` with a value of max users (for example `4` ) .

## HeartBeat

Will notify Instance Manager  that we are using the returned pixel streaming server. its handeled internally in app.js file.

## RequestDebugInstance 

Will return first instance found that is tagged `Debug` . useful for development phase !

## Where to use these functions?

By default these functions are used in InstanceLauncher.js
