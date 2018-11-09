---
layout: post
title:  "How to Install Command Line Tools only in OS X(Without Xcode)"
date:   2016-02-15
categories: [DevTool]

---
	How to Install Command Line Tools(CML) in OS X  (Without Xcode)?
	

Today when i type git into the terminal,one error jump out said:

> xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun

What's wrong with my rMBP,after i google it,i find out that it is caused by my upgrading OS X into EICaption(v10.11.3).

Okay we got the reason for this problem then we need fix it now:
install the command line tool as it asked
>xcode-select --install
 then we a dialog jump out ,we choose to install the CML only.yes just this trick.

 
 >if you have issues with xcode-select --install command , I kept getting a network problem timeout.

Try download the dmg at developer.apple.com/downloads (Command line tools OS X 10.11) for Xcode 7.1

for more refer [here](http://stackoverflow.com/questions/32893412/command-line-tools-not-working-os-x-el-capitan) and [here](http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/)






