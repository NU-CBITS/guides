# Development - iOS

## Updating Xcode command line tools

These instructions are accurate as of OS X Yosemite (10.10.X).

Ensure Xcode is already installed

```
$ xcode-select -p
/Applications/Xcode.app/Contents/Developer
```

Confirm that the command line tools, including `gcc` are installed

```
$ gcc
clang: error: no input files
```

If you don't see the above output, you will be prompted to install the required
packages.

Once installation is complete

```
$ gcc --version
Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/usr/include/c++/4.2.1
Apple LLVM version 6.0 (clang-600.0.57) (based on LLVM 3.5svn)
Target: x86_64-apple-darwin14.1.0
Thread model: posix
```

## Configuring a simulator

The full documentation from Apple can be [found here](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/iOS_Simulator_Guide/).

Start Xcode by locating the application icon and double clicking it. Open the
simulator under **Xcode** > **Open Developer Tool** > **iOS Simulator**. This
will run the currently configured device and OS version. To change the device,
go to **Hardware** > **Device** and select the desired target device.

To change the target OS, you may need to download additional simulators. To do
this, go to **Hardware** > **Device** > **Manage Devices...**. Click the `+` at
the bottom left of the window, open the selector next to "iOS Version:", then
select "Download more simulators...".

## Debugging web views with the Safari Web Inspector

With your simulator or connected device running the application and open to a
web view, open Safari on your computer. Go to **Safari** > **Preferences...** >
**Advanced**, and ensure "Show Develop menu in menu bar" is checked. Then go to
**Develop** > **iOS Simulator** and select the page. You should see the Web
Inspector.
