# Visual data
Projet pour le cours d'Analyse de données et datavisualisation
# Est-ce que la programmation des festivals français va-t-être boulversée à cause de la Covid 19?

# Sommaire
1. [Introduction](#introduction)
2. [Partie 1](#paragraph1)
3. [Partie 2](#paragraph2)
4. [Partie 3](#paragraph3)
5. [Conclusion](#conclusion)




## Introduction <a name="introduction"></a>
Malgré le fait que les humains aient compris l’importance de la visualisation des données très tôt, ce n’est qu’à partir des années 2000 que des ordinateurs assez puissants pour traiter un aussi grand volume de données ont été créés. À l'époque actuelle nous produisons des chiffres pour tout: pour les stocks, pour les facturations… Pourtant au fur et à mesure, le volume de données à traiter a augmenté si rapidement qu'il n’est plus possible de s'approprier et d'analyser une grande quantité de données en un simple coup d'œil. Et soyons honnête, le cerveau humain n’est pas fait pour analyser des milliers de lignes de données. Le travail suivant étudiera si la covid 19 a un impact sur la programmation des festivals français de rock. 


## Partie 1 <a name="paragraph1"></a>
Tout d'abord voyons tous les festivals français existants à l'aide de l'outil en ligne datawrapper. Comme données je me suis servie de data fournies par le ministère de la culture publiées en 2018 sur leur site dédié à l'open data. J'ai ensuite nettoyé les données brutes dans OpenRefine (j'ai retiré le colonnes non pertinentes par rapport à ce travail, ainsi que les espaces vides et j'ai aussi supprimé les premières lignes de description qui m'empéchait de bien exploiter les données dans les outils utilisés pour ce travail). 


<iframe title="Festivals" aria-label="Tableau" id="datawrapper-chart-MO6AV" src="https://datawrapper.dwcdn.net/MO6AV/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="2144"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();
</script>


## Partie 2  <a name="paragraph2"></a>
Voici une capture d'écran de l'outil en ligne Palladio qui montre que les festivals ont eu lieu à la fois en France métropolitaine, ainsi que dans les DOM-TOM, dans lequel j'ai utilisé la même data issue du ministère de la culture uaprès l'avoir nettoyée.

![Palladio](https://github.com/user-natia/visualdata/blob/80f1be2c89a3d8ce96bbdf20fa8ece23185e7375/Palladio.png)

   
## Partie 3 <a name="paragraph3"></a>    
### Voici deux requettes Sparql:
### Une qui montre les muciens(rock) et chanteurs(rock) qui se sont decedés depuis le debut de la pandemie mondiale: 
   
```sparql
#Musiciens ou chanteurs qui ont un genre contenant 'rock' et qui se sont décédé depuis le debut de la pandemie
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

### Et la deuxieme qui nous permet a visualiser ceux qui sont mort à cause du COVID19:

```sparql
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

## Conclusion <a name="Conclusion"></a>

