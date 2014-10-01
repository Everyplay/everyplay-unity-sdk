Welcome to Everyplay. To get started, make sure you have an account registered, and that you have a unique client ID
for your game. You can get these along with the latest integration instructions at https://developers.everyplay.com/

You can always download the latest SDK upgrades directly from https://github.com/everyplay/everyplay-unity-sdk
or from the Unity Asset Store: https://www.assetstore.unity3d.com/en/#!/content/16005

Looking for iOS version? See https://github.com/everyplay/everyplay-ios-sdk
Looking for Android version? See https://github.com/everyplay/everyplay-android-sdk

Everyplay SDK is licensed under the Apache License, Version 2.0 (http://www.apache.org/licenses/LICENSE-2.0.html) with restrictions. Please see Everyplay Terms of Service at https://everyplay.com/developer-terms-of-service for more information.

Everyplay SDK/Unity - Release Notes
===================================

Unity core and platform specific changes (if any) are separated

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
