title: 获取机场实时气象报告方法
date: 2016-04-18 14:45:00
tags:
- python
- Learning
permalink: get-airport-weather
---

最近坐飞机的时候总是遇到下雨，延误的很凄惨。坐在候机厅里问当班空姐吧，其实她们也不知道。
于是乎还是发挥咱半吊子的气象专业特长，找找看有没有什么办法获取机场气象站的实时报告。

# 手机端app：
手机端的天气app看起来挺多的，但是提供每十五分钟电文的少之又少。
航旅纵横或是飞常准虽然有这功能吧，但要么需要业内认证，要么需要花钱搞专业版。
找来找去，发现Flight Meteo这个app是可以提供各个机场的METAR和TAF的。
![FlightMeteo](/img/312667456527139479.jpg "Flight Meteo")

# 电脑端：

用电脑的话那就办法多多了，各种网站一堆一堆的。
然而没有那么多流量的时候，我还是更喜欢用脚本或者命令来获取。

这里安利两个办法，一个是`weather-util`，一个是`python-metar`。

`python-metar`可以从[pyhton-metar](https://github.com/timetric/python-metar)下载到。
各位如果要结合python做批量获取，就在这个基础上改改改就好啦。

而如果像我一样只是在候机的时候查所在机场的气象报文，那么`weather-util`更合适。
它的安装很简单，直接`sudo apt-get install weather-util`就可以安装好。
而使用嘛，安装好之后一句命令即可：

`weather <code>`

其中，`<code>`是机场的ICAO代码，比如说广州就是ZGGG，北京就是ZBAA。

在[这里](http://www.feeyo.com/airport_code.asp)可以查询全球机场的四字码。

weather-util查到的结果就像这样：

```shell
admin@ubuntu:~$ weather ZGGG
Searching via station...
[caching result Guangzhou, China]
Current conditions at Guangzhou, China (ZGGG) 23-10N 113-20E 42M
Last updated Apr 18, 2016 - 07:00 AM EDT / 2016.04.18 1100 UTC
Temperature: 77 F (25 C)
Relative Humidity: 65%
Wind: Calm
Sky conditions: mostly cloudy
```
如果需要看METAR电文的话，可以`weather -v <code>`，
那么输出的结果会变为：
```shell
admin@ubuntu:~$ weather -v ZGGG
Searching via station...
[caching result Guangzhou, China]
Guangzhou, China (ZGGG) 23-10N 113-20E 42M
Apr 18, 2016 - 07:00 AM EDT / 2016.04.18 1100 UTC
Wind: Calm:0
Visibility: greater than 7 mile(s):0
Sky conditions: mostly cloudy
Temperature: 77 F (25 C)
Dew Point: 64 F (18 C)
Relative Humidity: 65%
Pressure (altimeter): 29.94 in. Hg (1014 hPa)
ob: ZGGG 181100Z 00000MPS 9999 BKN060 25/18 Q1014 NOSIG
cycle: 11
```
其中，ob这一行就是。

可以看到现在广州白云机场的能见度很好，也没有下雨。
那飞机很快就可以起飞咯，再也不去骚扰坐台的空姐了^_^

