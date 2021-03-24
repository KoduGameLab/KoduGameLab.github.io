---
title: New Kodu Release 1.5.76.0
subtitle: micro:bit V2 now supported!
image: https://kodugamelab.github.io/images/microbitV2.jpg
layout: post
published: true
show_sidebar: true
author: "scoy"
---

# *1.5.76.0 is delayed until I get the proper certificate for digitally signing the new build.  Should be a week or so.*  

## New for 1.5.76.0

1.5.76.0 is a minor release with just a few bug fixes and changed features.

- Add support for micro:bit V2.  Kodu should now work with V1 or V2 devices.

- Add support for translating individual levels.<br>
    Includes support for localizing:<br>
             - titles<br>
             - descriptions<br>
             - 'say' strings<br>
             - 'hear said' strings<br>
             - tutorial instructions<br>
    Includes Russian for built-in Kodu worlds.<br>
    Right now doing a translation is a tedious process of hand editing the Xml file.  In the future I hope to create a tool to make this easier and less error-prone.
    
- Tweak the movement of Kodu and other bots that use the hover chassis.  This
change is not drastic but does make the bots feels more controllable and less
like they're sliding sideways a lot.

- Fix bot to bot collision response when one bot is user controlled and the other
is not.  Previously the user controlled bot wouldn't budge when collided with.
Now acts as it should.

- Change News Feed on the Main Menu page to stay open all the time.  Previously, 
it would close when not being read which may have hid important announcements.  
When open it would also sometimes "trap" input making it difficult to get back 
to the Main Menu.

- Kodu terrain map files now use the extension .Map instead of .Raw.  The .Raw
extension was being blocked by some anti-virus software.  There should be no
user-noticable effect of this.

- Add further compression to audio and remove opening video to reduce installer size.

- Update EULA, Privacy Statement, and Code of Conduct links to point to web site.