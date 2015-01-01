This project is a brutal fork of zxing for android in eclipse. Lots of edits to make the code Java 1.6 compliant. The zxing project uses Java 1.7

It makes a single jar file, which you can nab from the bin directory if that is all you need.

If you want to use the source tree in a library you probably want to subclass com.google.zxing.android.CaptureActivity. 

Quickstart with this lib:
Add to AndroidManifest.xml:
<uses-permission android:name="android.permission.CAMERA"/>

<application
    .
    .
     <activity android:name="com.google.zxing.client.android.CaptureActivity"
           android:screenOrientation="landscape"
           android:configChanges="orientation|keyboardHidden"
           android:theme="@android:style/Theme.NoTitleBar.Fullscreen"
           android:windowSoftInputMode="stateAlwaysHidden">
           <intent-filter>
              <action android:name="android.intent.action.MAIN"/>
              <category android:name="android.intent.category.DEFAULT"/>
           </intent-filter>
           <intent-filter>
              <action android:name="com.google.zxing.client.android.SCAN"/>
              <category android:name="android.intent.category.DEFAULT"/>
            </intent-filter>
    </activity>
    .
    .
</application>
</manifest>

Scan QR codes:
Intent intent = new Intent("com.google.zxing.client.android.SCAN");
intent.putExtra("SCAN_MODE", "QR_CODE_MODE");
startActivityForResult(intent, 0);