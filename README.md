# Unity-Text-To-Speech-Android

This plugin is unity TTS(Text to speach) plugin for android platform


Implementation 

In Unity add tts.jar and AndroidManifest.xml to your assest folder. Then create a new c# script and add following codes. That's it. Make sure 
Before run the program add scipt to the scence.

    private AndroidJavaObject tts = null;
    private AndroidJavaObject activityContext = null;
    
     using (AndroidJavaClass activityClass = new AndroidJavaClass("com.unity3d.player.UnityPlayer"))
            {
                activityContext = activityClass.GetStatic<AndroidJavaObject>("currentActivity");
         
            }

            using (AndroidJavaClass pluginClass = new AndroidJavaClass("com.example.ttsunity.MainClass"))
            { 
                tts = pluginClass.CallStatic<AndroidJavaObject>("instance");

                tts.Call("setContext", activityContext);
                activityContext.Call("runOnUiThread", new AndroidJavaRunnable(() =>
                {
                   

                    String speak = "Hi How are you";

                    String aa = tts.Call<String>("getText", speak);
               



                }));
    
     }
