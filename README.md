Welcome to Everyplay. To get started, make sure you have an account registered, and that you have a unique client ID
for your game. You can get these along with the latest integration instructions at https://developers.everyplay.com/

You can always download the latest SDK upgrades directly from https://github.com/everyplay/everyplay-unity-sdk
or from the Unity Asset Store: https://www.assetstore.unity3d.com/en/#!/content/16005

Looking for iOS version? See https://github.com/everyplay/everyplay-ios-sdk
<br />
Looking for Android version? See https://github.com/everyplay/everyplay-android-sdk

Everyplay SDK is licensed under the Apache License, Version 2.0 (http://www.apache.org/licenses/LICENSE-2.0.html) with restrictions. Please see Everyplay Terms of Service at https://everyplay.com/developer-terms-of-service for more information.

Everyplay SDK/Unity - Release Notes
===================================

Unity core and platform specific changes (if any) are separated

## Unity 1980-1400 - June 29th 2015

- Now allows 60fps recordings on iOS and Android

  To change the target framerate from the default 30fps,
  call Everyplay.SetTargetFPS()

- Improved frame synchronization and framerate handling

- Removed Everyplay.SetThumbnailWidth method

- Removed ThumbnailReadyAtFilePathDelegate

### iOS v1.9.8 - Jun 29th 2015 (build 1980)

- Now allows 60fps recordings on iOS 8+ devices with
  A7 CPU or later (devices with 64bit capability)

  To change the target framerate from the default 30fps, call
  [[Everyplay sharedInstance] capture].targetFPS

- Metal: CPU performance and snapshotRenderbuffer improvements

- Live FaceCam: When the internal preview box is hidden and
  a target texture is in use, the video content is no longer
  encoded to a separate file and doesn't show separately in
  the video player

- Removed thumbnailWidth property from EveryplayCapture

- Removed file based everyplayThumbnailReadyAt(FilePath|URL): delegates

### Android v1.4.0 - June 29th 2015 (build 1400)

- Now allows 60fps recordings on Android 4.4+ devices

  To change the target framerate from the default 30fps,
  call Everyplay.setTargetFPS()

- Improved frame synchronization and framerate handling

- Fixed an audio issue with FMOD Studio that
  could have resulted to a silent recording

- Removed setThumbnailWidth method from Everyplay class

- Removed onEveryplayThumbnailReadyAtFilePath from IEveryplayListener

- Fixed an issue with PowerVR GPUs and continuous recording feature:
  If recording over 5 minutes while using setMaxRecordingMinutesLength,
  the device could freeze, fixed

## Unity 1970-1350 - June 2nd 2015

- Android: Now supports Android M preview and adds
  a failsafe mode to protect from repeating crashes

- More Qualcomm Adreno 420 GPU fixes

### Android v1.3.5 - June 2nd 2015 (build 1350)

- New feature: Failsafe mode. If there's a crash during early
  initialization of Everyplay, the recording support will be
  disabled when the application is launched the next time

  Since the bug might be OS/driver related, the need for Failsafe
  mode is re-evaluated each time the SDK or OS has been upgraded
  or the application is removed

- Now supports Android M preview and fixes a crash against it.
  Older SDKs are disabled from recording against Android M

- More Qualcomm Adreno 420 crash fixes for some devices, like
  Samsung Galaxy Note 4

## Unity 1970-1340 - May 26th 2015

- iOS Metal: Graphics performance and memory usage optimizations,
  also fixed a small memory leak that happened on every frame
  even while not recording

- iOS Metal: Now supports HUD-less recording support through
  Everyplay.snapshotRenderbuffer();

- Removed use of IDFA / AdSupport.framework dependency

### iOS v1.9.7 - May 26th 2015 (build 1970)

- Metal: Graphics performance and memory usage optimizations

- Metal: Fixed a small memory leak that happened on every frame
  even while not recording

- Metal: Now supports HUD-less recording feature through
  [[[Everyplay sharedInstance] capture] snapshotRenderbuffer];

- Removed IDFA related code (AdSupport.framework), now uses IFV

- Removed EveryplaySoundEngine, OpenAL and AVFoundation implementations.
  Now uses Apple's high performance implementations when available

- Removed legacy OpenGL graphics integration API's from EveryplayCapture

- Removed support for file based thumbnails. If you use thumbnails,
  switch to texture based implementation

- Removed [Everyplay initWithDelegate:andAddRootViewControllerForView:]
  It was a helper for older world iOS apps that didn't implement
  UIViewController. Today, it's safe to assume that your code has them

- Increased the default video bitrate quality a bit

- Fixed a potential audio encoder memory leak while recording

### Android v1.3.4 - May 26th 2015 (build 1340)

- More video quality improvements for some devices

- Workaround a driver issue with Qualcomm Adreno 420's that
  caused a crash in some situations

- Fix graphics issue with Samsung Galaxy S5

- Removed support for file based thumbnails. If you use thumbnails,
  switch to texture based implementation

- Improved error handling on some situations where the video files
  could end up invalid, potentially causing a crash

## Unity 1961-1332 - Apr 29th 2015

- Fixed HUD-less recording to work against multithreaded
  rendering on Unity 4.6+ and against Unity 5 in general

- Video quality improvements on Android

### iOS v1.9.6 - Apr 28th 2015 (build 1961)

- Metal: Fixed Facecam session handling when reseting
  session to audio only (1961)

### Android v1.3.3 - Apr 29th 2015 (build 1332)

- Video quality improvement: On some devices and video codecs,
  the first second of the recording showed up as bit rotten,
  garbled output, fixed

- Fixed a graphics width vs stride regression from 1.3.0 SDK that
  could show up against the new graphics backend on some devices
  and driver versions, like Nexus 7 running Android 4.4

- On some rare devices, querying video codec info could cause
  application load times to slow down by 10 seconds, fixed

- Improved Everyplay.snapshotRenderbuffer() aka
  HUD-less recording feature

- Fix graphics issue with Samsung Galaxy S4 (PowerVR variant)

## Unity 1960-1320 - Apr 16th 2015

- Fixed a iOS build regression with IL2CPP

- Improved iOS/Xcode integration, allows building Unity-iPhone Tests

### iOS v1.9.6 - Apr 16th 2015 (build 1960)

- Improved graphics support against Unity 5.x

- Metal: Fixed thumbnail texture being flipped

- Metal: Fixed to support dynamic screen resolution changes

- Fixed a regression against AVAudioPlayer initWithData: support

- Fixed a compatibility issue with InMobi SDK

### Android v1.3.2 - Apr 16th 2015 (build 1320)

- Improved graphics support against Unity 5.x

- Multiple stability fixes against ImgTec PowerVR GPU

- Improve OpenGL ES1 support checking

- Prefetching data could cause an exception, fixed

- Fixed a rare login exception on Android 4.0.x

- Minor audio handling improvements

## Unity 1950-1310 - Mar 24th 2015

- Major Android graphics performance and stability improvements

- Improved Unity 5 integration support with iOS/Xcode

### Android v1.3.1 - Mar 24th 2015 (build 1310)

- Fixed a regression with setMaxRecordingMinutesLength from not
  working against the new graphics backend on Android 4.3+

- Improved potential memory usage and buffer refcount
  issues for some GPU drivers

- Fixed potential exceptions for general login, sharing
  and Facebook related code

- Fixed video player view from not loading on Android 4.0.x

- Fixed exception with the photo picker

- AndroidManifest.xml tweak to allow Android TV support

## Unity 1950-1300 - Mar 10th 2015

- Major Android graphics performance and stability improvements

### Android v1.3.0 - Mar 10th 2015 (build 1300)

- All-new graphics processing backend for Android 4.3+, improving
  framerate and stability a lot on many devices

- Greatly improved support for Nvidia GPUs (Tegra 3, Tegra 4, Tegra K1)

- Important AndroidManifest.xml changes to improve overall stability
  and reduce memory usage. If you're maintaining the manifest manually
  in your project, please merge the latest changes

- Fixes to potential crashes while using the login activity

- Fixed Javascript binding issues against some Android 4.4.x
  releases that prevented Everyplay Social views from working

- Fix potential performance issues when used against OpenGL ES3

- On some Android versions, changing to another Activity and returning
  could have prevented starting of a new recording from working, fixed

- Fixed a GPU driver caused ADB log flood issue; seen on some devices
  while recording

- Improved image quality on apps with 32-bit color graphics

- Multiple Nexus 10 specific issues fixed

- Now supports Nvidia Shield Portable, Nvidia Shield Tablet
  and Nexus 9 devices

## Unity 1950-1240 - Feb 20th 2015

- Regression fix; importing Everyplay package update cleared
  existing clientId and secret settings

- iOS 8 Metal improvements: Now supports Live FaceCam preview box and using
  target textures for facecam/thumbnails

- Due to above, few delegates/API calls are now obsoleted and replaced with
  a generic, less code requiring Texture2D variants that work against
  GLES/Metal backends

- Code cleanups and C# API usage updates for Unity 5

- Improved Android FAT support

### iOS v1.9.5 - Feb 20th 2015 (build 1950)

- iOS 8 Metal improvements: Now supports Live FaceCam preview box,
  thumbnail files/textures and using MTLPixelFormatRGBA8Unorm_sRGB

- Now supports OpenAL audio streaming through alSourceQueueBuffers

- Fix a conditition between showing modal share dialog and video editor
  that could lead to everyplayHidden delegate not properly called, potentially
  leading to game not being resumed as expected

- Fixed an issue with Cocos2d's scaled graphics on iPhone 6 Plus that prevented
  the recording from starting properly

- Facebook: Remove use of deprecated publish_stream permission

- Lighter UI theme

### Android v1.2.4 - Feb 20th 2015 (build 1240)

- More Android 5 Lollipop and Android Simulator fixes;
  null pointer exceptions, activity handling changes

- Fixed an issue with 64bit Android 5 devices that prevented
  looking up package name properly

- Querying device specific settings now wait until
  Everyplay.initEveryplay is called

- Facebook: Remove use of deprecated publish_stream permission

- Lighter UI theme

## Unity 1940-1230 - Jan 14th 2015

- Important Android 5 Lollipop fixes, potential graphics
  performance fixes

### iOS v1.9.4 - Jan 14th 2015 (build 1940)

- Improved Facebook integration by asking server-side
  configuration status

- Improved AVFoundation/AVAudioPlayer usage against
  small sound effects

### Android v1.2.3 - Jan 14th 2015 (build 1230)

- Fix a null pointer exception that could cause a crash on some
  Android 5 Lollipop devices

- Fix a graphics performance issue with glDiscardFramebufferEXT
  that could affect some Android versions/drivers shipped

- Fix a CORS issue with Android 5 WebResourceResponse

- Improved Facebook integration by asking server-side
  configuration status

## Unity 1930-1220 - Dec 16th 2014

- 1921-1210 release broke modal share dialog from appearing
  on iOS, fixed

### iOS v1.9.3 - Dec 16th 2014 (build 1930)

- Fixed an issue with modal share dialog not appearing
  on some viewController configurations

### Android v1.2.2 - Dec 16th 2014 (build 1220)

- Fixed a rare ClassNotFoundException with Parcel unable to find
  com.everyplay.Everyplay.communication.EveryplayResultReceiver

## Unity 1921-1210 - Dec 10th 2014

- Fixes iOS compatibility against Unity 4.6.1

### iOS v1.9.2 - Dec 10th 2014 (build 1921)

- [Everyplay initWithDelegate:] improvements

- [Everyplay sharedInstance].everyplayDelegate is now a weak pointer

- Minor UI and theming improvements

### Android v1.2.1 - Dec 10th 2014 (build 1210)

- App specific cached files now get removed upon
  application uninstallation

- Improved caching

- Minor UI and theming improvements

## Unity 1910-1200 - Nov 28th 2014

- Fix forward compatibility with future Unity releases,
  including an issue with iOS trampoline changes that
  could prevent Everyplay UI from showing up

### iOS v1.9.1 - Nov 28th 2014 (build 1910)

- Network access and caching optimizations

- Video seek bar and video ending event fixes for
  the new video player

- [Everyplay sharedInstance].parentViewController is now a weak pointer

- Improved UI orientation handling

### Android v1.2 - Nov 28th 2014 (build 1200)

- Generic optimizations against new Everyplay community

- New navigation top bar design to give more space while browsing

- Network access and caching optimizations

- Internal changes for UI theming support

- 3rdparty java code is relocated to another package namespace
  to avoid conflicts

- Performance updates to media merging and trimming

- Everyplay.setMaxRecordingMinutesLength didn't trim the
  resulting video, fixed

- Fixed potential crash issue with camera photo picker

- Upload performance improvements

- Everyplay.initEveryplay now retains IEveryplayListener

- Try-catch blocks for rare exceptions added

## Unity 1901-1160 - Nov 10th 2014

- Now supports iOS 8 Metal graphics for Unity 5 beta

- EveryplayThumbnailPool fixes

### iOS v1.9.0 - Nov 10th 2014 (build 1901)

- First iOS 8 Metal graphics support, no support for Live FaceCam
  preview box or thumbnail files/textures yet

- Video editor / player core and UI rewritten

- Everyplay.bundle graphics update, using fewer files and less space

- Internal changes for UI theming support

- Landscape support enabled by default for all iPhone views

- New navigation top bar design to give more space while browsing

- Improved memory handling

- Improved analytics

- Fixed thumbnail texture handling on iOS 8

- Improved FaceCam audio and video support and removed deprecated API
  usage warnings while running on iOS 7+

### Android v1.1.6 - Nov 10th 2014 (build 1160)

- Changes to activity handling in code and on AndroidManifest.xml
  to fix GPU driver issues and potential crashes

- Improved AAC encoded sound quality

- Improved Facebook behaviour for the future

## Unity 1840-1150 - Oct 9th 2014

### iOS v1.8.4 - Oct 9th 2014 (build 1840)

- Improved avatar photo picker and camera orientation handling

- Improved stereo support for AVFoundation / OpenAL

- OpenAL: Within game code, setting a negative value through
  alSourcef(x, AL_GAIN, volume) could cause iOS 8 mediaserverd to hang
  and cause multiple side effects until the device is rebooted, fixed

- everyplayFaceCamRecordingPermission delegate improvements

### Android v1.1.5 - Oct 9th 2014 (build 1150)

- Fixed Facebook sharing to work against Facebook API 2.0
  and later

## Unity 1830-1140 - Oct 1st 2014

- Forward compatibility with future Unity releases,
  including 5.0 betas

- Removed legacy code from iOS plugin

### iOS v1.8.3 - Oct 1st 2014 (build 1830)

- Now supports iOS 8 SDK / Xcode6 GM

- Fixed recording support against apps supporting the new
  native resolutions of iPhone 6 and iPhone 6 Plus on iOS 8

- Fixed video player / editor UI to support new iPhone 6 resolutions

- Fixed potential video player seek crash on iOS 8

- iOS 8 fixes for changed Javascript behaviour, fixes social
  network connections

- FaceCam now asks video user permission on iOS 8

- Workaround [UIView layoutSubViews] behaviour on iOS 8:

  Depending on game engine used and how the view handling is implemented,
  transitioning between views may trigger layoutSubViews and during the
  process, re-create OpenGL buffers. In some cases, calling EAGLContext
  renderbufferStorage:fromDrawable fails and may result to frozen graphics

  This behaviour is mostly seen on some custom engines and cocos2d

- Setting [Everyplay sharedInstance].capture property to nil
  could reset certain default settings to unwanted state, such
  as lowering target video framerate from the default, fixed

### Android v1.1.4 - Oct 1st 2014 (build 1140)

- Video resolution handling improvements

## Unity 1820-1130 - Sep 12th 2014

- Now respects "Symlink Unity Libraries" iOS platform setting for
  Everyplay.framework

### iOS v1.8.2 - Sep 12th 2014 (build 1820)

- iOS 8 view initialization fixes

- CPU optimizations for games with hard 60fps requirement

- AVFoundation: AVAudioPlayer now supports initWithData: method

- AVFoundation/OpenAL: Backgrounding application during initial splash screen
  could break audio state handling, fixed

## Unity 1810-1130 - Aug 27th 2014

- Now supports creating iOS/Xcode project on Windows

### iOS v1.8.1 - Aug 27th 2014 (build 1810)

- Major audio internals rework for future features, optimized for iOS 7

  As a result, there's less audio interruptions and potential issues that
  could cause losing audio output, recorded audio to be silent or go out
  of sync, mediaserverd crashing and causing wide load of generic issues

- Now supports AudioQueue recording against linear PCM
  and compressed formats (such as AAC)

- The audio core is now more sample rate agnostic, but 44.1 kHz is still
  considered the optimal one

- OpenAL: Improved source/buffer instance refcounting and thread-safety

- OpenAL: Loading audio samples with alBufferData now prefers the
  original sample rate specified and using less memory

- OpenAL: Loading certain audio samples caused audio clicks, fixed

- AVFoundation: AVAudioPlayer now supports duration and numberOfChannels
  properties

- AVFoundation: Improved audio streaming playback

- Fixed rare race condition in graphics recording that could have
  caused dropped video frames or not adding new frames to video

- Video editor now adds FaceCam recording UI buttons only after
  iOS user permission check

### Android v1.1.3 - Aug 27th 2014 (build 1130)

- Some devices and applications had image quality issues/artifacts
  before video encoding step, fixed

- Starting recording with HUD-less enabled could have caused frame
  glitch once while starting, fixed

- Fix network retry handling in Everyplay splash screen

- Analytics improvements

## Unity 1801-1120 - June 17th 2014

- Fixed iOS build error against Unity 4.5.1

- Fixed a potential exception error with Xcode project editor

- Updated WWW constructor parameters for Unity 4.5+

### Android v1.1.2 - June 17th 2014 (build 1120)

- Fixed recording from not working if changing MSAA anti-aliasing
  state during runtime

- Fixed a potential Qualcomm specific issue with rendering
  modal share dialog borders

- Improved upload handling

- Improved videoplayer thread safety

### Android v1.1.1 - May 20th 2014 (build 1110)

- Workaround for ImgTec PowerVR GPU driver behaviour that
  could cause entire device to freeze after initialization

- Fix videoplayer seeking from causing a crash on some
  devices with faulty drivers

- Fix for potential video encoding thread hanging on some
  devices like Samsung Galaxy S3

- Improved sending onEveryplayRecordingStarted listener events

- Add onEveryplayAccountDidChange listener event

## Unity 1801-1100 - May 20th 2014

- Improved Facebook integration, this requires the use of "Facebook for Unity" asset
  available from the Asset Store

- Lots of internal plugin changes and file location changes for better Unity integration,
  the migration should be seamless without removing previous assets

- New prefables integration. Instead of dragging a prefab to your first scene
  you may use the Edit / Everyplay Settings menu to enable Everyplay and to
  set your game credentials. This also allows you to temporarily disable
  Everyplay without removing the package

- Double check that clientId, secret and redirectURI settings have merged into
  the new Edit / Everyplay Settings menu after upgrading

- Calling Everyplay through the SharedInstance is now deprecated. You may still
  use the old way, but the recommended way is to call Everyplay.methodName

- Added checkboxes to new Everyplay settings menu for enabling Everyplay per
  platform (iOS/Android)

- Old test button functionality in Everyplay.prefab has been moved to
  Plugins/Everyplay/Helpers/EveryplayTest.prefab. A new simplified one can
  be enabled through Edit / Everyplay Settings menu

### iOS v1.8.0 - May 14th 2014 (build 1801)

- Everyplay now uses Accounts.framework and Facebook SDK for improved,
  seamless Twitter and Facebook login support. If none are linked into
  the project, the old login conventions apply

- The new improved Facebook login shares via Everyplay Facebook application,
  not through your existing Facebook application credentials. For immediate
  use, you might need to send your iOS bundle information or Android key
  hash to get started, please contact support@everyplay.com. We're currently
  working on making this step automated without extra work required on
  developers behalf

- All around stability and internal handling changes to the
  video recording core

- Further GPU optimizations against the new graphics integration, especially
  with older devices like iPhone 4S, iPad 2 and iPad 3

- Fixed a regression on using the latest Unity package and the new
  graphics integration that resulted to broken graphics in certain
  non-target native resolution use cases (Screen.SetResolution)

- Fixed a rare exception related to:
  '[AVAssetWriterInput initWithMediaType:outputSettings:sourceFormatHint:]
  AVVideoSettings dictionary must specify a positive width'

- Improved video orientation detection

- Fixed EveryplayCapture setLowMemoryDevice property behaviour in
  some rare cases

### Android v1.1 - May 14th 2014 (build 1100)

- Everyplay now uses Facebook SDK for improved, seamless Facebook login support.
  If not linked into the project, the old login convention applies

- The new improved Facebook login shares via Everyplay Facebook application,
  not through your existing Facebook application credentials. For immediate
  use, you might need to send your iOS bundle information or Android key
  hash to get started, please contact support@everyplay.com. We're currently
  working on making this step automated without extra work required on
  developers behalf

- Generic graphics optimizations and improvements to graphics
  related resource allocating and releasing, which could have
  led to invalid graphics state in earlier releases

- Improved recording state handling, orientation changing while
  recording etc

- Worked around OpenGL performance issue that could happen on some devices
  after returning from Everyplay videoplayer activity that's triggered by
  playLastRecording method

- Fixed a rare exception crash thrown by MediaCodec.dequeueInputBuffer

- Improved movie merging behaviour and exception handling

- Don't show 'Launch game' button when the game is already active one

- Improved onEveryplayReadyForRecording(int enabled) listener events
  to return false for more cases where the recording isn't going to
  be supported
