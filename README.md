#H1 IDX Broker Polygon saved link API PUT
------

Creation of a polygon saved link requires latitude and longitude points.

These can be created in an IDX Broker account and pulled via an API GET call for savedlinks.

In the url string that contains the lat and long points do not include the plus signs as this appears to cause an encoding issue.

There is a limit to the amount of characters allowed. The max length that is allowed is 512 for the pgon parameter. The more complicated the polygon the longer the urls string will be. Adding additional filers will make this string even longer. Should you reach the limit a URL can handle the savedlink may not function correctly. Simpler shapes are best. Complex shapes should be efficient in the amount of points used.

When saved links are called the query string is returned with plus signs which will probably get encoded as %2b and commas that will likely be encoded as %252C. Sending this plus sign encoding in a PUT call will not work. Nor will sending a plus sign like +. Instead use an empty space. The commas do not appear to make a difference and are accepted either way.

Example that doesn't work:
`"queryString":"pgon=44.0811730583207%2B-123.09107780456544%252C44.07143046636492%2B-123.11905860900879%252C44.04774558163617%2B-123.1032657623291%252C44.0811730583207%2B-123.09107780456544&radius=&layerType=polygon&clat=42.25291778330197&clng=-88.35754394&zoom=13&idxID=a001&pt=1"`

Example that will work:
"queryString":"pgon=44.0811730583207 -123.09107780456544%252C44.07143046636492 -123.11905860900879%252C44.04774558163617 -123.1032657623291%252C44.0811730583207 -123.09107780456544&radius=&layerType=polygon&clat=42.25291778330197&clng=-88.35754394&zoom=13&idxID=a001&pt=1"





Standard Disclaimer: This code is not official IDX Broker code. It does use their API, but in NO WAY is it supported by IDX Broker. DO NOT contact IDX Broker for any support of this code.
