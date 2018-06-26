# Usage

## Pre-requirement
Head to **Edit** > **Everyplay Settings** and enable platform(s) you wish to record on.

## Initializing
Either enable '**Early Initializer**' setting in **Edit** > **Everyplay Settings** or call **Everyplay.Initialize();** when you wish to initialize Everyplay.

## Recording
* Call **Everyplay.StartRecording();** to start recording.
* Call **Everyplay.StopRecording();** to stop recording.
* Call **Everyplay.PauseRecording();** to pause recording.
* Call **Everyplay.ResumeRecording();** to resume recording after pause.
---
* Call **Everyplay.IsRecording()** to check whether recording is active.
* Call **Everyplay.IsPaused()** to check whether recording is currently paused.
* Call **Everyplay.IsSupported()** to check whether Everyplay is supported on device.
* Call **Everyplay.IsRecordingSupported()** to check whether Everyplay recording is supported on device.
* Call **Everyplay.IsReadyForRecording()** to check whether device is ready to start a new recording.

## Additional functionality
* Call **Everyplay.TakeThumbnail();** to take a thumbnail of the recording. This will cause Everyplay.ThumbnailTextureReady(Texture2D, bool) to fire after the thumbnail has been prepared. You must set a target texture for the thumbnail using Everyplay.SetThumbnailTargetTexture(Texture2D) before using this.
* Call **Everyplay.SetThumbnailTargetTexture(Texture2D);** to set a target texture for the thumbnail. Once a thumbnail is taken, it will be applied to this target texture.
* Call **Everyplay.SetMotionFactor(int)** to affect the quality of the recording. The function clamps the value given between 1 and 4. Default quality is 2. Higher value produces better quality video at cost of file size.
* Call **Everyplay.SetTargetFPS(int)** to affect the frame rate the video is being captured. Higher capture frame rate produces smoother video at cost of file size.
* Call **Everyplay.SetLowMemoryDevice(bool)** to lower the memory cost of the plugin. This will increase CPU usage slightly.
* Call **Everyplay.SetAudioResamplerQuality(int)** to set the audio resampler to compatibility mode. The function clamps the value given between 0 and 1. Default setting is 0. Set this to 1 if you hear snapping, popping or crackling in your recorded video. This function affects only the Android platform.
* Call **Everyplay.SetMaxRecordingMinutesLength(int)** to set maximum length for a recording. The length is counted from the end of the recording. If you set this to 1 and record for 2 minutes, the recording will contain the LAST 1 minute. 
* Call **Everyplay.SetMaxRecordingSecondsLength(int)** to set maximum length for a recording. The length is counted from the end of the recording. If you set this to 15 and record for 30 seconds, the recording will contain the LAST 15 seconds.

## Accessing video
* Call **Everyplay.PlayLastRecording();** to play back last recording and allow user to trim it.
* Call **Everyplay.ShowSharingModal();** to share the video using the device's share modal.
* Call **Everyplay.GetFilepath();** to get the path to the video file. This will cause Everyplay.FileReady(string) to fire after the video has been prepared. 

## Events
* **Everyplay.WasClosed** - This event will fire when the Everyplay video player has been closed.
* **Everyplay.ReadyForRecording(bool)** - This event tells whether the device is currently ready to start a recording session. This event will fire multiple times during the lifetime of the app.
    * If the parameter is true, the device is ready to start a recording. Otherwise it is not.
* **Everyplay.RecordingStarted()** - This event will fire when a recording has been started.
* **Everyplay.RecordingStopped()** - This event will fire when a recording has been stopped.
* **Everyplay.FileReady(string)** - This event will fire when Everyplay.GetFilepath() has been called and the video has successfully been prepared.
    * The parameter contains the path to the recorded file.
* **Everyplay.ThumbnailTextureReady(Texture2D, bool)** - This will fire when Everyplay.TakeThumbnail() has been called and the thumbnail has successfully been prepared.
    * The Texture2D parameter contains the thumbnail as a Texture2D.
    * The bool parameter indicates whether the thumbnail was taken in portrait orientation. If the parameter is true, the thumbnail was taken in portrait orientation, otherwise it was taken in landscape orientation.

## Examples
### Starting recording
    if(Everyplay.IsReadyForRecording())
    {
        Everyplay.StartRecording();
    }
### Stopping recording
    if(Everyplay.IsRecording())
    {
        Everyplay.StopRecording();
    }
### Subscribing to events with sample handlers
    void OnEnable()
    {
        Everyplay.WasClosed += Everyplay_WasClosed;
        Everyplay.ReadyForRecording += Everyplay_ReadyForRecording;
        Everyplay.RecordingStarted += Everyplay_RecordingStarted;
        Everyplay.RecordingStopped += Everyplay_RecordingStopped;
        Everyplay.FileReady += Everyplay_FileReady;
        Everyplay.ThumbnailTextureReady += Everyplay_ThumbnailTextureReady;
    }

    void OnDisable()
    {
        Everyplay.WasClosed -= Everyplay_WasClosed;
        Everyplay.ReadyForRecording -= Everyplay_ReadyForRecording;
        Everyplay.RecordingStarted -= Everyplay_RecordingStarted;
        Everyplay.RecordingStopped -= Everyplay_RecordingStopped;
        Everyplay.FileReady -= Everyplay_FileReady;
        Everyplay.ThumbnailTextureReady -= Everyplay_ThumbnailTextureReady;
    }

    void Everyplay_WasClosed()
    {
        Debug.Log("Everyplay modal was closed!");
    }
    
    void Everyplay_ReadyForRecording(bool isReady)
    {
        Debug.Log("Everyplay ready for recording: " + isReady);
    }
    
    void Everyplay_RecordingStarted()
    {
        Debug.Log("Everyplay recording started!");
    }
    
    void Everyplay_RecordingStopped()
    {
        Debug.Log("Everyplay recording stopped!");
    }
    
    void Everyplay_FileReady(string filePath)
    {
        Debug.Log("Everyplay recorded file: " + filePath);
    }
    
    void Everyplay_ThumbnailTextureReady(Texture2D thumbTex, bool isPortrait)
    {
        Debug.Log("Everyplay Texture w:"+thumbTex.width+" h:"+thumbTex.height+" portrait:"+isPortrait);
    }
