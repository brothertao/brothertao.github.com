---
layout: post
category : all
tags : []
---
{% include JB/setup %}

The Tracking HTTP API
===================

The Tracking HTTP API
用来跟踪页面访问、时间、独立用户，请求 http://athena.pinganfang.com/nf/track/

Supported Query Parameters

Note: all parameters values that are strings (such as 'url', 'action_name', etc.) must be URL encoded.
注意：所有的参数都是字符串类型,(url、action_name这种要encode)

Required parameters

idsite
 (required) — 暂时没有什么意义
rec
 (required) — 暂时没有意义,例如： &rec=1
url
 (required) — 跟踪的页面

Recommended parameters

action_name
 (recommended) —	方便人眼 
_id
 (recommended) — 和cookie中的tuid类似
rand
 (recommended) — 绕过代理缓存
apiv
 (recommended) — api version

Optional User info (We recommend that these parameters be used if the information is available and relevant to your use case.)

urlref
 — The full HTTP Referrer URL. This value is used to determine how someone got to your website (ie, through a website, search engine or campaign).
_cvar
 — Visit scope custom variables. This is a JSON encoded string of the custom variable array (see below for an example value).
_idvc
 — The current count of visits for this visitor. To set this value correctly, it would be required to store the value for each visitor in your application (using sessions or persisting in a database). Then you would manually increment the counts by one on each new visit or "session", depending on how you choose to define a visit. This value is used to populate the report Visitors > Engagement > Visits by visit number.
_viewts
 — The UNIX timestamp of this visitor's previous visit. This parameter is used to populate the report Visitors > Engagement > Visits by days since last visit.
_idts
 — The UNIX timestamp of this visitor's first visit. This could be set to the date where the user first started using your software/app, or when he/she created an account. This parameter is used to populate the Goals > Days to Conversion report.
_rcn
 — The Campaign name (see Tracking Campaigns). Used to populate the Referrers > Campaigns report. Note: this parameter will only be used for the first pageview of a visit.
_rck
 — The Campaign Keyword (see Tracking Campaigns). Used to populate the Referrers > Campaigns report (clicking on a campaign loads all keywords for this campaign). Note: this parameter will only be used for the first pageview of a visit.
res
 — The resolution of the device the visitor is using, eg 1280x1024.
h
 — 用户端当前时间  小时
m
 — minute
s
 — The current second (local time).
plugins used by the visitor can be specified by setting the following parameters to 1: 
fla
 (Flash), 
java
 (Java), 
dir
 (Director), 
qt
 (Quicktime), 
realp
 (Real Player), 
pdf
(PDF), 
wma
 (Windows Media), 
gears
 (Gears), 
ag
 (Silverlight).

ua
 — An override value for the User-Agent HTTP header field. The user agent is used to detect the operating system and browser used.

lang
 — An override value for the Accept-Language HTTP header field. This value is used to detect the visitor's country if GeoIP is not enabled.
Optional Action info (measure Page view, Outlink, Download, Site search)

cvar
 — Page scope custom variables. This is a JSON encoded string of the custom variable array (see below for an example value).
link
 — An external URL the user has opened. Used for tracking outlink clicks. We recommend to also set the url parameter to this same value.
download
 — URL of a file the user has downloaded. Used for tracking downloads. We recommend to also set the url parameter to this same value.
search
 — The Site Search keyword. When specified, the request will not be tracked as a normal pageview but will instead be tracked as a Site Search request.
search_cat
 — when search is specified, you can optionally specify a search category with this parameter.
search_count
 — when search is specified, we also recommend to set the search_count to the number of search results displayed on the results page. When keywords are tracked with &search_count=0 they will appear in the "No Result Search Keyword" report.
idgoal
 — If specified, the tracking request will trigger a conversion for the goal of the website being tracked with this ID.
revenue
 — A monetary value that was generated as revenue by this goal conversion. Only used if idgoal is specified in the request.
gt_ms
 — The amount of time it took the server to generate this action, in milliseconds. This value is used to process the Page speed report Avg. generation time column in the Page URL and Page Title reports, as well as a site wide running average of the speed of your server. Note: when using the Javascript tracker this value is set to the ime for server to generate response + the time for client to download response.
cs
 — The charset of the page being tracked. Specify the charset if the data you send to Piwik is encoded in a different character set than the default 
utf-8
.

电子商务类的参数

e_c
 — The event category. Must not be empty. (eg. Videos, Music, Games...)
e_a
 — The event action. Must not be empty. (eg. Play, Pause, Duration, Add Playlist, Downloaded, Clicked...)
e_n
 — The event name. (eg. a Movie name, or Song name, or File name...)
e_v
 — The event value. Must be a float or integer value (numeric), not a string.
Ecommerce info

Use the following values to record a cart and/or an ecommerce order. You must also set 
&idgoal=0
 in the request.

ec_id
 — The unique string identifier for the ecommerce order
revenue
 — The grand total for the ecommerce order
ec_st
 — The sub total of the order (excludes shipping)
ec_tx
 — Tax Amount of the order
ec_sh
 — Shipping cost of the Order
ec_dt
 — Discount offered
ec_items
 — Items in the Ecommerce order. This is a JSON encoded array of items. Each item is an array with the following info in this order: item sku, item name, item category, item price, item quantity.


特殊的API
Special parameters

The following parameters require that you set 
&token_auth=
 to the token_auth value of the Super User or a user with admin access to the website visits are being tracked for.

token_auth
 — 32 character authorization key used to authenticate the API request.
cip
 — Override value for the visitor IP (both IPv4 and IPv6 notations supported).
cdt
 — Override for the datetime of the request (normally the current time is used). This can be used to record visits and page views in the past. The expected format is: 
2011-04-05 00:11:42
 (remember to URL encode the value!). The datetime must be sent in UTC timezone. Note: if you record data in the past, you will need to force Piwik to re-process reports for the past dates.
cid
 — defines the visitor ID for this request. You must set this value to exactly a 16 character hexadecimal string (containing only characters 01234567890abcdefABCDEF). When specified, the Visitor ID will be "enforced". This means that if there is no recent visit with this visitor ID, a new one will be created. If a visit is found in the last 30 minutes with your specified Visitor Id, then the new action will be recorded to this existing visit.
new_visit
 — If set to 1, will force a new visit to be created for this action. This feature is also available in Javascript.
country
 — An override value for the country. Should be set to the two letter country code of the visitor (lowercase), eg fr, de, us.
region
 — An override value for the region. Should be set to the two letter region code as defined by MaxMind's GeoIP databases. See here for a list of them for every country (the region codes are located in the second column, to the left of the region name and to the right of the country code).
city
 — An override value for the city. The name of the city the visitor is located in, eg, Tokyo.
lat
 — An override value for the visitor's latitude, eg 22.456.
long
 — An override value for the visitor's longitude, eg 22.456.
Tracking Bots

By default Piwik does not track bots. If you use the Tracking HTTP API directly, you may be interested in tracking bot requests. To enable Bot Tracking in Piwik, set the parameter &bots=1 in your requests to piwik.php.

Example Tracking Request

Here is an example of a real tracking request used by the Piwik Mobile app when anonymously tracking Mobile App usage:

http://piwik-server/piwik.php?_cvar={"1":["OS","iphone 5.0"],"2":["Piwik Mobile Version","1.6.2"],"3":["Locale","en::en"],"4":["Num Accounts","2"]}&action_name=View settings&url=http://mobileapp.piwik.org/window/settings &idsite=8876&rand=351459&h=18&m=13&s=3 &rec=1&apiv=1&cookie= &urlref=http://iphone.mobileapp.piwik.org&_id=af344a398df83874 &_idvc=19&res=320Ã—480&
Note: for clarity, parameter values are not URL encoded in this example.

Explanation: this URL has custom variables for the OS, Piwik version, number of accounts created. It tracks an event named View settings with a fake URL, records the screen resolution and also includes a custom unique ID generated to ensure all requests for the same Mobile App user will be recorded for the same visit in Piwik.

Bulk Tracking
Some applications such as the Piwik log importer, have to track many visits, sometimes tens, hundreds, thousands or even more all at once. Tracking these requests with one HTTP request per visit or action can result in enormous delays due to the amount of time it takes to send an HTTP request, Using the bulk tracking feature, however, these requests can be sent all at once making the application far more efficient.

To send a bulk tracking request, an HTTP POST must be made with a JSON object to the Piwik tracking endpoint. The object must contain the following properties:

requests
 — an array of individual tracking requests. Each tracking request should be the query string you'd send if you were going to track that action individually.
token_auth
 — (optional) token_auth which is found in the API page. Specify this only needed if you use any of the parameters that require 
token_auth
Example Requests

This is an example of the payload of a bulk tracking request:

{
   "requests": [
      "?idsite=1&url=http://example.org&action_name=Test bulk log Pageview&rec=1",
      "?idsite=1&url=http://example.net/test.htm&action_name=Another bul k page view&rec=1"
   ],
   "token_auth": "33dc3f2536d3025974cccb4b4d2d98f4"
}
Here is the command to send this request to Piwik using curl (without the 
token_auth
 which is optional in this case):

curl -i -X POST -d '{"requests":["?idsite=1&url=http://example.org&action_name=Test bulk log Pageview&rec=1","?idsite=1&url=http://example.net/test.htm&action_name=Another bulk page view&rec=1"]}' http://piwik.example.com/piwik.php
This will track two actions using only one HTTP request to Piwik.








