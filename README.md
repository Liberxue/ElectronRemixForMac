## Init

* `https://github.com/Liberxue/ElectronRemixForMac.git && cd electron-applescript`
* `yarn`
* `yarn add applescript`
* `yarn start`

## 备注
1.考虑一下重复点击。点击过快～～
2.多语言请自定义applescripts/sound
3 仅采用appscript支持Mac-->

## demo

## applescript
```applescript
tell application "System Preferences"
	reveal anchor "output" of pane "com.apple.preference.sound"
end tell
tell application "System Events"
	tell application process "System Preferences"
		repeat until exists tab group 1 of window 1
		end repeat
		tell table 1 of scroll area 1 of tab group 1 of window 1
			set target to "Soundflower (2ch)"
			set alternative to value of text field 1 of row 1
			set retry to 1
			set interval to 1
			if value of text field 1 of (row 1 whose selected is true) is target then
				set target to alternative
			end if
			repeat with counter from 0 to retry
				try
					select (row 1 whose value of text field 1 is target)
					exit repeat
				end try
				if counter < retry then
					delay (interval)
				end if
			end repeat
		end tell
	end tell
end tell
tell application "System Preferences" to quit
```
