---
layout: post
title:  "paraview.simple library"
#date:   <%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>
date:   '2019-11-20 15:12:11 +0530'
categories: ParaView
---
ParaView is packed with a very powerful library which makes it feasible to execute complex vtk commands. The first thing we'll do is take the ParaView data and manipulate it using the script we generated previously `trace.py`. We'll work on the contour data that was produced in the script called `contour1` (this is the default name that ParaView uses for contour). Let's gather this data in a useful form in the variable `data`:
```python
from vtk.numpy_interface import dataset_adapter as dsa
rawData = servermanager.Fetch(contour1)
data = dsa.WrapDataObject(rawData)
```
First we import the `dsa` library which adds numpy functionality. Here `data` is the dataset that we'll work on. To explore what it contains, we can use
```python
dir(data)
```
This gives a list of variables contained in the object `data`. We can check the type of object `data` using python commands like `type(data)` or `dtype(data)`. Suppose we want to get the coordinates of contour1, we can use:
```python
xi = data.Points.Arrays[0][i][0]
yi = data.Points.Arrays[0][i][1]
```
To get the values of a field `T` at this index `i`, we can use the following command:
```python
data.PointData['T'][i]
```
We can also convert the above `coordinates` array and `T` field array into something that is in numpy's format using:
```python
import numpy as np
coords_np = np.asarray(data.Points.Arrays[0])
T_np = np.asarray(data.PointData['T'].Arrays[0])
```
We can plot these numpy arrays using matplotlib, the regular way we do it in python:
```python
import matplotlib.pyplot as plt
plt.plot(coords_np[:,0], T_np, 'o')
plt.savefig('contour_1_' + '.png')
plt.close()
```