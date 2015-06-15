# RaySDK for iOS
The RaySDK allows you to interact with Ray beacons in the wild.

##Prerequisites
RaySDK is compatible with projects for iOS 8 and above

##Installation
1. Drag the **RaySDK.framework** file into your project
2. Under your peoject's target's _General_ settings, make sure **RaySDK.framework** is included under _Embedded Binaries_ as well as _Linked Frameworks and Libraries_
	
##Usage
1. Register your _API Key_ by calling `RSDK.sharedInstanceWithApiKey("YourAPIKey")`
2. Set the SDK delegate `RSDK.sharedInstance.delegate`
3. Set the location service `AuthorizationType` to request. `.Always` or `.WhenInUse`. 
	* If location services has not yet been requested, the SDK will attempt to request for it.
	* Make sure the `NSLocationAlwaysUsageDescription` or `NSLocationWhenInUseUsageDescription` key is present in your plist file.
4. Call `RSDK.sharedInstance.startMonitoring()` to begin monitoring for _Ray_ beacons

###Optional Configurations
**Variable** | **Description**
--- | --- | ---
`beaconRSSITrigger` | The value where a beacon should be registered as "in-range". Default value is -75.
`beaconMinimumThreshold` | The minimum value of the range where the beacon should stay in in-order to be considered "in-range". Value must be less than `beaconMaximumThreshold` and within range of (∞, 0). Default value is -95.
`beaconMaximumThreshold` | The maximum value of the range where the beacon should stay in in-order to be considered "in-range". Value must be greater than `beaconMinimumThreshold` and within range of (∞, 0]. Default value is 0.
`timeToWait` | The time to wait (seconds) before a beacon is registered. Default value is 10 seconds.
`subsequentRangingInterval` | The time to wait (seconds) between identifying identical beacons. Default value is 6 hours.
`enableBackgroundProcessTimeExtension` | If `true`, background process time will be extended while app is in background. Default value is `false`.