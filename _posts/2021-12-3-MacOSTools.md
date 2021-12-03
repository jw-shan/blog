---
layout: post
title:  "MacOS Tools"
date:   2021-05-21 16:00 
categories: Latex
---

Excellent tools in Mac OS.

### 1. PopClip

#### 自定义插件：

https://github.com/pilotmoon/PopClip-Extensions

https://pilotmoon.com/popclip/extensions/

http://www.saitjr.com/others/popclip-extension.html

插件位置：`~/Library/Application Support/PopClip/Extensions/` 

(自定义插件需要注释掉identifier)





---

### Appendix

### A.1 在pdf expert中添加下划线

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>Actions</key>
	<array>
		<dict>
			<!-- <key>Image File</key>
			<string>hlite.png</string> -->
			<key>Key Combo</key>
			<dict>
				<key>keyChar</key>
				<string>U</string>
				<key>modifiers</key>
				<integer>1310720</integer>
			</dict>
			<key>Required Apps</key>
			<array>
				<string>com.readdle.PDFExpert-Mac</string>
			</array>
			<key>Title</key>
			<string>Underline</string>
		</dict>
	</array>
	<key>Extension Description</key>
	<string>Underline the selected text. Works in Pages, Preview, Evernote, Alternote, Scrivener, DevonThink, Skim, PDFpen and PDF Expert only.</string>
	<!-- <key>Extension Identifier</key>
	<string>com.pilotmoon.popclip.extension.Underline</string> -->
	<key>Extension Name</key>
	<string>Underline</string>
</dict>
</plist>

```

