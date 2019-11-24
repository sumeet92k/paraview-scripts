---
layout: post
title:  "paraview.simple library"
#date:   <%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>
date:   '2019-11-20 15:12:11 +0530'
categories: ParaView
---
ParaView brings with itself a very powerful library which makes feasible to write vtk commands. The first thing we'll do is take the ParaView data and manipulate it using the script we generated `trace.py`. We'll work on the contour data that we generated that was called `contour1`. Let's gather this data in a useful form in the variable `data`:
{% highlight python %}
from vtk.numpy_interface import dataset_adapter as dsa
rawData = servermanager.Fetch(contour1)
data = dsa.WrapDataObject(rawData)
{% endhighlight %}
First we import the `dsa` library which adds numpy functionality. Here `data` is the dataset that we'll work on. To explore what it contains, we can use
{% highlight python %}
dir(data)
{% endhighlight %}
This gives a list of variables contained in the object `data`. We can check the type of object `data` using python commands like `type(data)` or `dtype(data)`. Suppose we want to get the coordinates of contour1, we can use:
{% highlight python %}
xi = data.Points.Arrays[0][i][0]
yi = data.Points.Arrays[0][i][1]
{% endhighlight %}
To get the values of a field `T` at this index `i`, we can use the following command:
{% highlight python %}
data.PointData['T'][i]
{% endhighlight %}
We can also convert the above `coordinates` array and `T` field array into something that is in numpy's format using:
{% highlight python %}
import numpy as np
coords_npBulk = np.asarray(data.Points.Arrays[0])
T_np = np.asarray(data.PointData['T'].Arrays[0])
{% endhighlight %}
We can plot these numpy arrays using matplotlib, the regular way we do it in python:
{% highlight python %}
import matplotlib.pyplot as plt
plt.plot(coords_npBulk[:,0], T_np, 'o')
plt.savefig('contour_1_' + '.png')
plt.close()
{% endhighlight %}