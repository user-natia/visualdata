# Visual data
Pour le cours d'Analyse de données et datavisualisation

## Welcome, le titre un

```
Sparql
select ?person ?personLabel ?died ?sitelinks where {
  ?person wdt:P31 wd:Q5;
          wdt:P570 ?died.
  filter (?died >= "2019-03-15T00:00:00Z"^^xsd:dateTime && ?died < "2019-05-01T00:00:00Z"^^xsd:dateTime)
  ?person wikibase:sitelinks ?sitelinks.
  service wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}  order by desc(?sitelinks) limit 100
```
