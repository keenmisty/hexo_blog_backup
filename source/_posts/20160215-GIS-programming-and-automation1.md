---
title: GIS中Python的使用<1>
date: 2016-02-15 13:02:00
tags:
- ArcGIS
- Python
- Learning
permalink: GISPython-learn
---

# GIS Modeling与Python介绍
---

**ArcGIS中提供了两种写Python的方式：**

- ModelBuilder
- IDLE

ModelBuilder的使用很简单，可以先拿来做模型的结构设计。
但是一些复杂的处理则需要写Python Script来实现。

因此：

**Using Python window in ArcGIS：**


```python
import arcpy
arcpy.Buffer_analysis("us_cities", "us_cities_buffered", "15 miles", "", "", "ALL")

```

注意：所有需要调用ArcGIS的Tools的脚本，都需要`import arcpy`

比如打印feature的空间参考：

```python
# Opens a feature class from a geodatabase and prints the spatial reference
 
import arcpy
  
featureClass = "C:/Data/USA/USA.gdb/StateBoundaries"
   
# Describe the feature class and get its spatial reference   
desc = arcpy.Describe(featureClass)
spatialRef = desc.spatialReference
    
# Print the spatial reference name
print spatialRef.Name
```

参考: Python Scripting for ArcGIS by Paul A. Zandbergen

