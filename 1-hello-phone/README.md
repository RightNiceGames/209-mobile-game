# 1 Hello Mobile

In this chapter, we'll learn how to use Unity go get our Game on our phones.

## Modules
Install the Modules for the Platform that you want to build for.
- Open Unity Hub
- Go to Installs
- Select your Install
- Config > Add Modules

## Changing Platform
Change the Target Platform to the Platform you want to build for.
- Unity already open?
  - Open Build Settings
  - Click on the Platform you want to test for
  - Click on Switch Platform
- Unity not open, yet?
  - Open Unity Hub
  - Click on the Project you want to open's Version Number
  - Select the platform you want to switch to

## Build And Run
Make sure your Phone is Connected
- On Android, enable the Developer Mode
- For iOS, you need a Mac to Build&Run
  - Because XCode is required to build
  - and it only exists for MacOS
- Use an Emulator in case you don't have a compatible phone
  - Nox
  - BlueStacks

And hit Build & Run

You might run into a few more issues that need resolving
- like XCode not being installed or needing to be updated
- NDK or Android Studio not being installed or needing to be updated

Try fixing these issues yourself
- Google the Error message you're getting
  - You're definitely not the first person in the internet with this problem
- Or look at tutorials

## Debug

Try Debugging Remotely
- Build&Run
- Attach Rider's Debugger
- Or Unity's Remote Logging Feature

Can you
- See the Logs?
- Pause the execution?
- Hit Breakpoints?