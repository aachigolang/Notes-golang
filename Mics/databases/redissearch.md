asidmanzoorawan
aachi0987



### redissearch


docker run -p 6379:6379 redislabs/redisearch:latest

docker exec -it <docker name> /bin/bash
redis-cli


client lib
go get github.com/RediSearch/redisearch-go/redisearch

FT.CREATE shakespeare SCHEMA line TEXT SORTABLE play TEXT NOSTEM speech NUMERIC SORTABLE speaker TEXT NOSTEM entry TEXT location GEO


FT.ADD shakespeare 57956 1 FIELDS text_entry "Out, damned spot! out, I say!--One: two: why," line "5.1.31" play macbeth speech 15  speaker "LADY MACBETH" location -3.9264,57.5243



https://github.com/RediSearch/redisearch-beer

rsbeer
rsbrewery

ftbeeridx
ftbreweryidx

ftbeeridx
       TextField('name', weight=5.0),
        TextField('brewery'),
        NumericField('breweryid', sortable=True),
        TextField('category'),
        NumericField('categoryid'),
        TextField('style'),
        NumericField('styleid'),
        TextField('description'),
        NumericField('abv', sortable=True),
        NumericField('ibu', sortable=True),
        TagField('favorite')
 

Irish Ale and German Ale beers with ABV greater than 9%:
FT.SEARCH beerIdx "@category:Irish Ale|German Ale @abv:[9 inf]"

All beers with ABV higher than 5% but lower than 6%:
FT.SEARCH beerIdx "@abv:[5 6]"

Breweries in a 10km radius of the coordinates of Chicago, IL USA:
FT.SEARCH breweryIdx "@location:[-87.623177 41.881832 10 km]"

FT.INFO

FT.SEARCH {index} {query} [NOCONTENT] [VERBATIM] [NOSTOPWORDS] [WITHSCORES] [WITHPAYLOADS] [WITHSORTKEYS]
  [FILTER {numeric_field} {min} {max}] ...
  [GEOFILTER {geo_field} {lon} {lat} {radius} m|km|mi|ft]
  [INKEYS {num} {key} ... ]
  [INFIELDS {num} {field} ... ]
  [RETURN {num} {field} ... ]
  [SUMMARIZE [FIELDS {num} {field} ... ] [FRAGS {num}] [LEN {fragsize}] [SEPARATOR {separator}]]
  [HIGHLIGHT [FIELDS {num} {field} ... ] [TAGS {open} {close}]]
  [SLOP {slop}] [INORDER]
  [LANGUAGE {language}]
  [EXPANDER {expander}]
  [SCORER {scorer}] [EXPLAINSCORE]
  [PAYLOAD {payload}]
  [SORTBY {field} [ASC|DESC]]
  [LIMIT offset num]