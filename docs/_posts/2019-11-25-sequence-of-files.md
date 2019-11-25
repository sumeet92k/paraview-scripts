---
layout: post
title:  "Time sequence of files"
#date:   <%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>
date:   '2019-11-25 15:12:11 +0530'
categories: ParaView
---
An important use of scripting comes when we have a large number of files (probably at different times) and we would like to run the same script over all the time frames. We had generated a `trace.py` file which works on a single time source. Now we'll modify this file so that it executes on the available data at different times. 
ParaView stores the filenames in an array 