## Apple Scripts
  * [Delay Execution](#apple-scripts_delay-execution)
  * [Login Script](#apple-scripts_login-script)
  * [Chrome Kisok](#apple-scripts_chrome-kiosk-with-keyboard)
  * [Hide Mouse Cursorcerer](#apple-scripts_cursorcerer-hide-mouse)
  * [Kill App](#apple-scripts_kill-app)
  * [Open App](#apple-scripts_open-app)



### Delay Execution
```applescript
do shell script "/bin/sleep #{AMOUNT_IN_SECONDS}"
```
### Login Script
```applescript
tell application "Terminal"
	activate
	do script "$HOME/login.sh"
end tell
```
### Launch
```applescript
tell application "#{ABSOLUTE_PATH_TO_APP}" to launch
```
### Chrome Kiosk (with Keyboard)
```applescript
do shell script "open '/Applications/Google Chrome.app' #{URL}"
tell application "Google Chrome" to activate

tell application "System Events"
	keystroke "f" using {command down, control down}
end tell
```
### Cursorcerer (hide mouse)
Make sure [Cursorcerer](http://doomlaser.com/cursorcerer-hide-your-cursor-at-will/) is installed.
```applescript
tell application "System Preferences"
	activate
	set current pane to pane "Cursorcerer"
end tell
```
### Kill App
```applescript
do shell script "ps -ef | grep #{APPNAME} | grep -v grep | awk '{print $2}' | xargs kill"
```
### Open App
```applescript
do shell script "open '#{ABSOLUTE_PATH_TO_APP}'"
```

### Close All Windows
(Example Close Terminal after Power Out)
```applescript
tell application "Terminal"
  activate
end tell

do shell script "/bin/sleep 3"

tell application "Terminal"
  close every window
end tell

do shell script "/bin/sleep 3"

tell application "Terminal"
  activate
  do script "$HOME/login.sh"
end tell
```