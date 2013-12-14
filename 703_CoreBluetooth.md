# Session 703 Core Bluetooth

1. Dropped simulator support, use device!
2. Simplified API to handle centrals and peripherals
3. Database caching in iOS 7 caches characteristic + descriptor & characteristic value
4. iOS 7 increase MTU(Max Transmission Unit) -> faster
	* default MTU = 23 bytes
	* increased MTU = ?? (need to contact peripherals) -> 20% increasement
	* No API change is required
5. Background mode for Bluetooth
	* system will proxy Bluetooth
	* Opt-in: for long term purpose
	* Add State preservation and Restoration
6. Built-in GATT client
	* HID device=?, just like bluetooth classic
	* ANCS service to replace MAP, notification about any event on your phone
		* System is managing the connection
