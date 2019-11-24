---
layout: post
title:  "Auto Generating code"
#date:   <%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>
date:   '2019-11-18 15:12:11 +0530'
categories: ParaView
---
There are two ways to start scripting in ParaView, one is the hard way of starting from scratch which teaches us the nitty gritty details of ParaView along the way. The other is the faster approach that we follow here of modifying an auto generated python code. This approach is preferred if we only need to make small modifications to the code generated. Lets begin by opening ParaView from the terminal. Its better at this stage to open ParaView without passing any arguments:
{% highlight shell %}
paraview 
{% endhighlight %}

As the GUI window pops up, navigate to the __View tab__ and select the __Start Trace__ option. A window opens up with some options describing the amount of Trace code to be generated. For our purposes, __Trace only changes__ will be sufficient. Click on __Show Incremental Trace__. Now we are all set to let ParaView record our steps as a code. Proceed to the workflow as usual, and all major changes will occasionally be reflected in the trace editor. Once all the actions in the workflow pipeline have been done, delete all the pipeline stages starting from the last one. This generates corresponding lines of delete code in the Trace editor. Save the final Trace file in a python file format (.py). You can now close the ParaView window. We will henceforth work on this file (lets call this file `trace.py`).

Before we move on to editing this file to suit our purpose, we will check the generated python file. There are two ways to check this:
1. Open ParaView. Go to the __Python Shell__ tab and enable it. This opens a __Python Shell__. Click on run scripts in the __Python Shell__ window, navigate to the folder where the data and the Python Trace file is kept, and load it. This runs the entire code from the Trace file. A point to note down, since we have added lines for delete command as well, we will momentariy see the output window before it gets deleted. But if this works, it ensures that the generated script is working.
2. The other way of opening the script is through `pvpython`, a non-GUI ParaView binary which can be found at the same location as the `paraview` binary. To run the file just execute the following code in the command line:
{% highlight shell %}
pvpython trace.py 
{% endhighlight %}
This again will momentarily show the ParaView GUI before the code exits.

### Moving Forward
This tutorial verifies that we have a working auto generated python code, and how to run it. Now lets delve into some modifications to this `trace.py` file to get more out of ParaView.