---
published: true
title: Adding default Myanmar Font in Manjaro XFCE
layout: post
---
##Problem
I try to install zawgyi font and other unicode fonts inside *~/.fonts* the system try to pick up only zawgyi font as default font.

##Solution
put this file 
	
	/etc/fonts/conf.d/90-my-mm.conf

The content should be 

```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <match target="pattern">
        <test name="lang" compare="contains">
            <string>my</string>
        </test>
        <test qual="any" name="family">
            <string>sans-serif</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>Noto Sans Myanmar</string>
        </edit>
    </match>

    <match target="pattern">
        <test name="lang" compare="contains">
            <string>my</string>
        </test>
        <test qual="any" name="family">
            <string>serif</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
            <string>Noto Sans Myanmar</string>
        </edit>
    </match>
</fontconfig>

```

I install noto fonts  b4 this because Noto Sans Myanmar font is ok for me.
    
    $sudo pacman -S noto-fonts

If you want to use Yunghkio or other unicode fonts you can replace in the config.