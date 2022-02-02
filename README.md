# Visual data
Pour le cours d'Analyse de données et datavisualisation

## Welcome, le titre un

````Sparql
select ?person ?personLabel ?died ?sitelinks where {
  ?person wdt:P31 wd:Q5;
          wdt:P570 ?died.
  filter (?died >= "2019-03-15T00:00:00Z"^^xsd:dateTime && ?died < "2019-05-01T00:00:00Z"^^xsd:dateTime)
  ?person wikibase:sitelinks ?sitelinks.
  service wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}  order by desc(?sitelinks) limit 100
````

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#select%20%3Fperson%20%3FpersonLabel%20%3Fdied%20%3Fsitelinks%20where%20%7B%0A%20%20%3Fperson%20wdt%3AP31%20wd%3AQ5%3B%0A%20%20%20%20%20%20%20%20%20%20wdt%3AP570%20%3Fdied.%0A%20%20filter%20%28%3Fdied%20%3E%3D%20%222019-03-15T00%3A00%3A00Z%22%5E%5Exsd%3AdateTime%20%26%26%20%3Fdied%20%3C%20%222019-05-01T00%3A00%3A00Z%22%5E%5Exsd%3AdateTime%29%0A%20%20%3Fperson%20wikibase%3Asitelinks%20%3Fsitelinks.%0A%20%20service%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%20%20order%20by%20desc%28%3Fsitelinks%29%20limit%20100" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>
