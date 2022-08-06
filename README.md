SwiftDefaultApps
========

This Preference pane is chiefly intended to be a modern replacement for the amazing RCDefaultApp developed way back when by Carl Lindberg, which stopped working in 10.12 due to deprecation of ObjC Garbage collection.
Additionally, I guess it was a good way to teach myself Swift.

Feel free to contribute, comment or report issues at https://github.com/Lord-Kamina/SwiftDefaultApps.

## Installing & Uninstalling
	
	Download latest release from https://github.com/Lord-Kamina/SwiftDefaultApps/releases
	To install, double click on the .prefpane, and you will be prompted to install it.
	To uninstall, simply Ctrl+Click on the Prefpane icon and remove it, or move the .prefpane file to the Trash.
	
## Installting with brew

run: 

```bash
brew install swiftdefaultappsprefpane
``

then use Spotlight to open the `SwiftDefaultApps.prefpane`. It will open the system preferences and you find the app on the bottom of the icons.

## Usage Notes

This Preference pane will let you view and change default application associations for basically any URI Scheme and/or filetype in macOS.
The user-interface should be pretty self-explanatory; but, there are some things that might require an explanation:
	
- Selecting any URI Scheme or File type (always represented by a UTI), will give you a list of all valid applications for each LaunchServices role. This data is generated by LaunchServices itself.
  - There's two additional options: 
    - One of them is **"Do Nothing"**, what this does is register the item to be handled by a dummy application which basically does nothing. Its only function is being able to open any URI Scheme or UTI whatsoever, printing a line to the console (specifying whatever it was that launched it) and immediately quitting. By default this application should be located in the `Resources` folder inside the prefpane bundle; SwiftDefaultApps will, however, also look for it in the directory it is itself located in (for the CLI version) and every `Applications`folder in the computer.
    - The second is **"Other..."**, which obviously will allow you to select an application not in the list; with a caveat. In recent versions of macOS, the LaunchServices have become quite a bit smarter under the hood than they used to be. In practice, what this means is that although you can choose *any* application to handle anything, only valid associations will be preserved, as the LaunchServices is permanently looking for invalid or stale associations and removing them.
  - One final note: In the URI Schemes tab, you have the option of adding a custom URI Scheme (Removing them on demand is neither possible nor necessary, due to the same thing explained above). This options is provided for completeness' sake; you should virtually never need to use it, since Launch Services should be able to properly detect any valid URL Handlers. As a further cautionary note: If you add a custom URI Scheme when it is not needed, you may not be able to remove it except by uninstalling and reinstalling SwiftDefaultApps. Why? Because new schemes are by default associated to *"Do Nothing", which means Launch Services will always find a valid handler as long as SwiftDefaultApps is installed.

### How to Find Out File UTI

Run in your terminal the following command (replace my_song.mp3 by your file):

`mdls -name kMDItemContentType -name kMDItemContentTypeTree -name kMDItemKind my_song.mp3`

## Acknowledgments & Attributions

- Using jakeheis' SwiftCLI 2.0 as a base for the CLI version located inside the bundle. (https://github.com/jakeheis/SwiftCLI)
- Using AMTourky's DRYView canned views system (https://github.com/AMTourky/CocoaBindingDryView-ReusableViews/)
- Using ZamzamKit's SynchronizedArray (https://github.com/ZamzamInc/ZamzamKit)
- Icon made using the following resources:
	- Brush, Ruler and Pencil designed by Freepik. (http://www.freepik.com/free-vector/background-of-back-to-school_769298.htm)
	- Magnifying glass frame designed by Balintseby / Freepik (http://www.freepik.com/free-vector/realistic-magnifying-glass_789215.htm)
	- Magnifying glass crystal designed by Freepik (http://www.freepik.com/free-vector/crystal-frames-collection_724172.htm)
	- Gears designed by Freepik (http://www.freepik.com/free-vector/gray-background-of-gear_956712.htm)

## Current Version
    - Version: 2.0.1
    - Date: 2019-07-26

## Known Issues
- 

## TO DO
- Localizations

# Release Notes

## [2.0.1] - 2019-07-26
  + ### Fixed
  	+ CLI: Crash when displaying the results for setHandler with shortcuts such as internet, browser, email, etc.

## [2.0.0] - 2019-06-12
  + ### Added
    + Signed prefpane, CLI and Dummy apps.
    + Both the prefpane and the CLI version will now automatically try to locate ThisAppDoesNothing.app if it does not appear registered with launch services.
  + ### Changed
    + SwiftCLI is now built and linked as a static library instead of a framework.
    + Updated to Swift 5
    + The content array is now populated by overriding `didSelect()` instead of relying on an arbitrary sleep timer.
    + Changed the CLI app's name from lsreg to swda.
    + Messages in both the CLI and Preference Pane are now a bit more verbose.
    + Under the hood, folded most of the app's feedback to the user into a single `displayAlert()` function.
  + ### Fixed
  	+ Updated the Swift Package Manager manifest to version 5.
  	+ Updated the SynchronizedArray code and corrected the attribution; Before, I had inadvertently credited an unrelated project with the same name.
  	+ Various small optimizations, fixes and text corrections.

## [1.1.3] - 2018-11-15
  + ### Fixed
  	+ Bug causing crash on related to force-unwrapping bundleIdentifier.

## [1.1.2] - 2018-10-07
  + ### Changed
  	+ Migrated to Swift 4.2
  	+ Force Static linking of standard library, which should fix issues running on Mojave.

## [1.1.1] - 2018-04-15
  + ### Changed
  	+ Small changes for Swift 4.1.

## [1.1.0] - 2017-09-27
  + ### Changed
  	+ Migrated code to Swift 4.
  + ### Fixed
  	+ Fixed an unwrapped Optional when changing associations in the "Applications" tab.
  	+ Fixed CLI tool.
  	+ Some other cleanups.

## [1.0.0] - 2017-05-01
  + ### Added
    + Initial release!
  + ### Changed
  + ### Fixed
  
  
