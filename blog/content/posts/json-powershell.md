+++
date = '2012-07-31'
title = 'Json in Powershell 3.0'
+++

I use Powershell to do a lot of utility coding and exploratory work in testing, I really like having the full features of the .net framework in an interactive environment which encourages me to iterate and poke around. I can instantiate .net objects and then inspect them in an interactive command line to see all their properties and methods. This makes it a terrific testing tool to do exploratory work on systems that have no UI.

I have recently been tasked to look at and use an internal API that is built as a RESTful web service that returns Json objects. In coding around, I discovered that the Powershell that came on my Windows 7 box can easily generate and HTTPWebRequest but has limited support for Json. I could convert the Json to XML and then parse the nodes in XSL or XPath, but that is not so smooth; what I really wanted to take that Json and convert it to a native .net PSobject and then navigate around to discover its properties and methods. So enter Powershell 3.0!!

The latest version of Powershell is in CTP from Microsoft and can be downloaded as part of the Windows Management Framework 3.0

It has a much improved Integrated Scripting Environment (with Intellisense!) and a hot new cmdlet ConvertFrom-Json

The ConvertFrom-Json cmdlet takes a json string and converts it directly into an object which can be referenced in the usual dot notation. It has a complimentary ConvertTo-Json cmdlet which can put things into a json formatted string.

Start by downloading, installing and launching Powershell v3

Let’s take today’s date and make it into Json.

```
Get-Date
Get-Date | ConvertTo-Json
```
```
PS C:\Users\ptaylor1> Get-Date | Select-Object -Property *
Get-Date | Select-Object -Property * | ConvertTo-Json
```
```
DisplayHint : DateTime
DateTime    : Tuesday, July 31, 2012 11:34:30 AM
Date        : 7/31/2012 12:00:00 AM
Day         : 31
DayOfWeek   : Tuesday
DayOfYear   : 213
Hour        : 11
Kind        : Local
Millisecond : 981
Minute      : 34
Month       : 7
Second      : 30
Ticks       : 634793312709814613
TimeOfDay   : 11:34:30.9814613
Year        : 2012
```
```
{
    "DisplayHint":  2,
    "DateTime":  "Tuesday, July 31, 2012 11:34:31 AM",
    "Date":  "\/Date(1343718000000)\/",
    "Day":  31,
    "DayOfWeek":  2,
    "DayOfYear":  213,
    "Hour":  11,
    "Kind":  2,
    "Millisecond":  16,
    "Minute":  34,
    "Month":  7,
    "Second":  31,
    "Ticks":  634793312710164633,
    "TimeOfDay":  {
                      "Ticks":  416710164633,
                      "Days":  0,
                      "Hours":  11,
                      "Milliseconds":  16,
                      "Minutes":  34,
                      "Seconds":  31,
                      "TotalDays":  0.48230343128819442,
                      "TotalHours":  11.575282350916666,
                      "TotalMilliseconds":  41671016.463300005,
                      "TotalMinutes":  694.516941055,
                      "TotalSeconds":  41671.016463299995
                  },
    "Year":  2012
}
```


So you see how it took the native date value and made into Json with names and values. Now let’s take the Json and make it back into an object, we will store it in a variable to keep things clear
```
 $rightNow = Get-Date | Select-Object -Property * | convertTo-Json
 $timeObject = $rightNow | ConvertFrom-Json
 $timeObject.Month
```
```
PS C:\Users\ptaylor1>      $rightNow = Get-Date | Select-Object -Property * | convertTo-Json
     $timeObject = $rightNow | ConvertFrom-Json
     $timeObject.Month
7
```


So we can get PSObjects in and out of Json pretty easily. But to make this really useful, we connect to a HTTP REST JSON service and get back a string that we can transform into a PSObject. Let’s start with connecting to a RESTful web service; twitter is a pretty useful and well understood one.
```
 $url = "http://search.twitter.com/search.json?q=Yummy%20Pho&rpp=5&include_entities=true&result_type=mixed"
 [net.httpWebRequest] $myRequest = [net.webRequest]::create($url)
 $myRequest.Method = "GET"
 [net.httpWebResponse] $myResponse = $myRequest.getResponse()
 $myStreamReader = New-Object IO.StreamReader($myResponse.getResponseStream())
 $myJson = $myStreamReader.ReadToEnd()
 $myTweets = $myJson | ConvertFrom-Json
 $myResponse.Close()
```
Now you have a PSObject which is really a .NET collection of tweets about a delicious Vietnamese soup. Let’s poke around by calling
```
 $myTweets.results

created_at              : Tue, 31 Jul 2012 18:46:24 +0000
entities                : @{hashtags=System.Object[]; urls=System.Object[]; user_mentions=System.Object[]}
from_user               : Kaikai_97
from_user_id            : 267299561
from_user_id_str        : 267299561
from_user_name          : Just me
```
...and so on and so on

I can go further and look at the properties of any tweet in the collection

  $myTweets.results[0].from_user

and get

$myTweets.results[0].from_user
Kaikai_97

So when using and testing our internal APIs I can use Powershell 3 to take a very exploratory and iterative approach while remaining very close to the iron and interfacing with the code in essentially the same manner that our systems will.

*This article was written as part of work I did at the Vivaki Nerve Center, part of the Publicis Groupe. Its original archive can be found at [https://web.archive.org/web/20160711001659/http://www.qathedata.com/blog/2012/07/31/json-in-powershell-3-dot-0/](https://web.archive.org/web/20160711001659/http://www.qathedata.com/blog/2012/07/31/json-in-powershell-3-dot-0/)*
