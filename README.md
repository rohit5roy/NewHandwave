# NewHandwave

All Credit for the C files Goes to the original Kritts/Handwave Repo

I have made a big update in improving the methodology used in this library (it is a library now and not a project).
The sensing of motion is now more accurate (opposed to swiping up and it picks up left/right more easily)
I have added convenience methods for initializing and checking permissions > Android M

Usage on a seperate project:

1. Download the library to your computer

2. Open the project you want to add this to

3. File -> New -> Import Module

4. Check Both -> OK -> Wait for the libraries to index

5. Right Click your app module -> Open Module Settings

6. Click the dependencies tab 

7. Click the + icon and select the module option

8. Add Both the openCV module and the NewHandwave module

9. The library is now usable in your project (See below for instructions)



Manifest:

      <uses-permission android:name="android.permission.CAMERA" />


Activity/Fragment usage:

1. 
            YourActivity implements CameraGestureSensor.Listener

2. 
                  @Override
                protected void onCreate(Bundle savedInstanceState) {
                    super.onCreate(savedInstanceState);
                    setContentView(R.layout.activity_main);
                    if (PermissionUtility.checkCameraPermission(this)) {
                        LocalOpenCV loader = new LocalOpenCV(MainActivity.this, MainActivity.this);
                    }
                }

3. 
                    @Override
                      public void onResume() {
                          super.onResume();
                          if (PermissionUtility.checkCameraPermission(this)) {
                              LocalOpenCV loader = new LocalOpenCV(MainActivity.this, MainActivity.this);
                          }
                      }

4. Customize the following to correspond to the actions the sensor picks up:

              @Override
                public void onGestureUp(CameraGestureSensor caller, long gestureLength) {
                    Log.i(TAG, "Up");
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            Toast.makeText(MainActivity.this, "Hand Motion Up", Toast.LENGTH_SHORT).show();
                        }
                    });
                }

                @Override
                public void onGestureDown(CameraGestureSensor caller, long gestureLength) {
                    Log.i(TAG, "Down");
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            Toast.makeText(MainActivity.this, "Hand Motion Down", Toast.LENGTH_SHORT).show();
                        }
                    });

                }

                @Override
                public void onGestureLeft(CameraGestureSensor caller, long gestureLength) {
                    Log.i(TAG, "Left");
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            Toast.makeText(MainActivity.this, "Hand Motion Left", Toast.LENGTH_SHORT).show();
                        }
                    });
                }

                @Override
                public void onGestureRight(CameraGestureSensor caller, long gestureLength) {
                    Log.i(TAG, "RIght");
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            Toast.makeText(MainActivity.this, "Hand Motion Right", Toast.LENGTH_SHORT).show();
                        }
                    });
                }
                
 Enjoy!


<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
