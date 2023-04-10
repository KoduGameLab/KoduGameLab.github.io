---
title: New Kodu Release 1.6.18.0
subtitle: New Update!
layout: post
published: true
show_sidebar: true
author: "scoy"
---

## New Kodu Release 1.6.18.0

Mostly internal bug fixes.  
- Kodu was having trouble importing worlds with multiple levels.  The terrain files were getting duplicated and cross linked between the levels.  This should be better now.
- Some Vietnamese uses would not get all the language options.  I'm still not sure what was causing this problem but I've made some changes that I hope will help.
- The "Avoid" tile would occasionally cause a crash.  This is now protected against. 