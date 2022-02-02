# Visual data
Projet pour le cours d'Analyse de données et datavisualisation

## Ce panorama liste plusieurs milliers de manifestations et intègre aussi bien les festivals de spectacle vivant ou de cinéma que les salons, rencontres, ##biennales… existant dans le domaine des arts visuels, du livre, du patrimoine, etc

<div class="flourish-embed" data-src="story/1122730"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

## Welcome, le titre un

```Sparql
#Musiciens ou chanteurs qui ont un genre contenant 'rock' et qui ont mort à cause du COVID 19
#defaultView:Graph
SELECT DISTINCT ?human ?humanLabel 
WHERE
{
    VALUES ?professions {wd:Q177220 wd:Q639669} 
    ?human wdt:P31 wd:Q5 .
    ?human wdt:P106 ?professions .
    ?human wdt:P136 ?genre .
    ?human wikibase:statements ?statementcount .
    ?genre rdfs:label ?genreLabel .  
    FILTER CONTAINS(?genreLabel, "rock") .
    SERVICE wikibase:label { bd:serviceParam wikibase:language "en","fr","ru","ge" }
    ?human wdt:P570 ?died.
    filter (?died >= "2020-03-15T00:00:00Z"^^xsd:dateTime && ?died < "2022-01-01T00:00:00Z"^^xsd:dateTime)
    ?human wikibase:sitelinks ?sitelinks.
    service wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
ORDER BY ?humanLabel
```

<iframe style="width: 50vw; height: 30vh; border: none;" src="https://query.wikidata.org/embed.html#%23Musiciens%20ou%20chanteurs%20qui%20ont%20un%20genre%20contenant%20%27rock%27%20et%20qui%20ont%20mort%20%C3%A0%20cause%20du%20COVID%2019%0A%23defaultView%3AGraph%0ASELECT%20DISTINCT%20%3Fhuman%20%3FhumanLabel%20%0AWHERE%0A%7B%0A%20%20%20%20VALUES%20%3Fprofessions%20%7Bwd%3AQ177220%20wd%3AQ639669%7D%20%0A%20%20%20%20%3Fhuman%20wdt%3AP31%20wd%3AQ5%20.%0A%20%20%20%20%3Fhuman%20wdt%3AP106%20%3Fprofessions%20.%0A%20%20%20%20%3Fhuman%20wdt%3AP136%20%3Fgenre%20.%0A%20%20%20%20%3Fhuman%20wikibase%3Astatements%20%3Fstatementcount%20.%0A%20%20%20%20%3Fgenre%20rdfs%3Alabel%20%3FgenreLabel%20.%20%20%0A%20%20%20%20FILTER%20CONTAINS%28%3FgenreLabel%2C%20%22rock%22%29%20.%0A%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22%2C%22fr%22%2C%22ru%22%2C%22ge%22%20%7D%0A%20%20%20%20%3Fhuman%20wdt%3AP570%20%3Fdied.%0A%20%20%20%20filter%20%28%3Fdied%20%3E%3D%20%222020-03-15T00%3A00%3A00Z%22%5E%5Exsd%3AdateTime%20%26%26%20%3Fdied%20%3C%20%222022-01-01T00%3A00%3A00Z%22%5E%5Exsd%3AdateTime%29%0A%20%20%20%20%3Fhuman%20wikibase%3Asitelinks%20%3Fsitelinks.%0A%20%20%20%20service%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0AORDER%20BY%20%3FhumanLabel%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

## Welcome, le titre deux
### Les rock musiciens qui se sont decedé à cause de Covid 19
```Sparql
#Musiciens ou chanteurs qui ont un genre contenant 'rock' et qui ont mort à cause du COVID 19
#defaultView:Tree
SELECT DISTINCT ?human ?humanLabel 
WHERE
{
    VALUES ?professions {wd:Q177220 wd:Q639669} 
    ?human wdt:P31 wd:Q5 .
    ?human wdt:P106 ?professions .
    ?human wdt:P136 ?genre .
    ?human wikibase:statements ?statementcount .
    ?genre rdfs:label ?genreLabel .  
    FILTER CONTAINS(?genreLabel, "rock") .
    SERVICE wikibase:label { bd:serviceParam wikibase:language "en","fr","ru","ge" }
    ?human wdt:P106 wd:Q639669 .    
    ?human wdt:P509 ?cause .       
    ?cause wdt:P279* wd:Q84263196 .
}
ORDER BY ?humanLabel
```
<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23Musiciens%20ou%20chanteurs%20qui%20ont%20un%20genre%20contenant%20%27rock%27%20et%20qui%20ont%20mort%20%C3%A0%20cause%20du%20COVID%2019%0A%23defaultView%3ATree%0ASELECT%20DISTINCT%20%3Fhuman%20%3FhumanLabel%20%0AWHERE%0A%7B%0A%20%20%20%20VALUES%20%3Fprofessions%20%7Bwd%3AQ177220%20wd%3AQ639669%7D%20%0A%20%20%20%20%3Fhuman%20wdt%3AP31%20wd%3AQ5%20.%0A%20%20%20%20%3Fhuman%20wdt%3AP106%20%3Fprofessions%20.%0A%20%20%20%20%3Fhuman%20wdt%3AP136%20%3Fgenre%20.%0A%20%20%20%20%3Fhuman%20wikibase%3Astatements%20%3Fstatementcount%20.%0A%20%20%20%20%3Fgenre%20rdfs%3Alabel%20%3FgenreLabel%20.%20%20%0A%20%20%20%20FILTER%20CONTAINS%28%3FgenreLabel%2C%20%22rock%22%29%20.%0A%20%20%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%22%2C%22fr%22%2C%22ru%22%2C%22ge%22%20%7D%0A%20%20%20%20%3Fhuman%20wdt%3AP106%20wd%3AQ639669%20.%20%20%20%20%0A%20%20%20%20%3Fhuman%20wdt%3AP509%20%3Fcause%20.%20%20%20%20%20%20%20%0A%20%20%20%20%3Fcause%20wdt%3AP279%2a%20wd%3AQ84263196%20.%0A%7D%0AORDER%20BY%20%3FhumanLabel%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>


