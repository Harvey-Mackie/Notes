# Tips
- Fix build failing for unknown reason e.g. nonzero exit
	- Clean build folder
	- Delete derived data folder (can access via settings)
	- Run `pod install --repo-update`
	- Re-run
	- [Reference](https://stackoverflow.com/questions/52387452/command-compileswift-failed-with-a-nonzero-exit-code-in-xcode-10) 


- Fix xcode deny(1) file-write-create
    - Update your Xcode project build option ENABLE_USER_SCRIPT_SANDBOXING to 'No'.
    - Source - https://stackoverflow.com/questions/76590131/error-while-build-ios-app-in-xcode-sandbox-rsync-samba-13105-deny1-file-w
