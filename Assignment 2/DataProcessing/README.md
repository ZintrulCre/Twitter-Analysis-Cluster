1. selecte by location (each of the main capital cities) and time interval (down to the day)

- melbourne

  - curl "http://45.113.232.90/couchdbro/twitter/_design/twitter/_view/summary" -G --data-urlencode 'start_key=["melbourne",2015,1,1]' --data-urlencode 'end_key=["melbourne",2017,5,31]' --data-urlencode 'reduce=false' --data-urlencode 'include_docs=true' --user "readonly:ween7ighai9gahR6" -o /data/twitter-melbourne-20150101-20170531.json

  - curl "http://45.113.232.90/couchdbro/twitter/_design/twitter/_view/summary" -G --data-urlencode 'start_key=["melbourne",2017,6,1]' --data-urlencode 'end_key=["melbourne",2017,12,31]' --data-urlencode 'reduce=false' --data-urlencode 'include_docs=true' --user "readonly:ween7ighai9gahR6" -o /data/twitter-melbourne-20170601-20171231.json
  - curl "http://45.113.232.90/couchdbro/twitter/_design/twitter/_view/summary" -G --data-urlencode 'start_key=["melbourne",2018,1,1]' --data-urlencode 'end_key=["melbourne",2018,12,31]' --data-urlencode 'reduce=false' --data-urlencode 'include_docs=true' --user "readonly:ween7ighai9gahR6" -o /data/twitter-melbourne-20180101-20181231.json


2. aggregate tweets by city, the "summary" view can be used

curl -XGET "http://45.113.232.90/couchdbro/twitter/_design/twitter/_view/summary" -G --data-urlencode 'reduce=true' --data-urlencode 'include_docs=false' --data-urlencode 'group_level=1' --user "readonly:ween7ighai9gahR6" 

3. extracts GeoJSON limited to an area around Melbourne CBD ("r1r0" to "r1r1" geohash): 

curl -XGET "http://45.113.232.90/couchdbro/twitter/_design/twitter/_list/geojson/geoindex?reduce=false" -G --data-urlencode 'start_key=["r1r0",null,null,null]' --data-urlencode 'end_key=["r1r1",{},{},{}]' --user "readonly:ween7ighai9gahR6" 

