PathPlug Android SDK (v1.0.0)
====================

###Android Manifest

You need to add these permissions into <strong>AndroidManifest.xml</strong> file.

  	<uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.BLUETOOTH"/>
	<uses-permission android:name="android.permission.BLUETOOTH_ADMIN"/>
		
###Library Import
You need to add <strong>pathplug.jar</strong> file to your libs directory of your project and then import on your projects Main Activiy.

		import com.arkenus.pathplug.*;
		
###PathPlugManager Variable
On your activity you should init your <strong>PathPlugManager</strong> variable like below.

		private PathPlugManager ppm;
		
###OnCreate Function
You need to add init functions of PathPlug to your MainActivity OnCreate function

    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.JELLY_BEAN_MR2)
    {		
	     ppm = PathPlugManager.getInstance(this);
	     ppm.initialize(MainActivity.class,R.drawable.icon,"your_app_key","your_app_secret");
    }

###Required Override Methods
When you add <strong>PathplugListener</strong> to your activity it will ask you to add other required functions. You should add them like below.
  ```java
    @Override
	public void searchState(final int state) {
		//
	}

	@Override
	public void enterRegion(IBeacon ibeacon) {
		//			
	}
	
	@Override
	public void beaconFound(IBeacon ibeacon) {
		ppm.checkPathPlugInteractions();
	}
	
	
	@Override
	public void exitRegion(IBeacon ibeacon) {
		//
	}
	
	@Override
	public void operationError(int status) {
		Log.i("Pathplug", "Bluetooth error: " + status);	
	}	

