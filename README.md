## Les Fromages Français

### Présentation du jeu de données

Ce jeu de données réunit la liste de 338 spécialités fromagères françaises.

<iframe src="https://data.opendatasoft.com/explore/embed/dataset/fromagescsv-fromagescsv@public/table/?disjunctive.fromage&static=false&datasetcard=false" width="400" height="300" frameborder="0"></iframe>

### Les fromages selon le type de lait

<iframe src="https://data.opendatasoft.com/chart/embed/?dataChart=eyJ0aW1lc2NhbGUiOiIiLCJxdWVyaWVzIjpbeyJjaGFydHMiOlt7ImFsaWduTW9udGgiOnRydWUsInR5cGUiOiJwaWUiLCJmdW5jIjoiQ09VTlQiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiJyYW5nZS1jdXN0b20iLCJwb3NpdGlvbiI6ImNlbnRlciJ9XSwiY29uZmlnIjp7ImRhdGFzZXQiOiJmcm9tYWdlc2Nzdi1mcm9tYWdlc2NzdkBwdWJsaWMiLCJvcHRpb25zIjp7fX0sInhBeGlzIjoibGFpdCIsIm1heHBvaW50cyI6NTAsInNvcnQiOiIiLCJjYXRlZ29yeUNvbG9ycyI6eyJWYWNoZSI6IiNFODcyNzMiLCJDaFx1MDBFOHZyZSI6IiNFRTlBOUEiLCJCcmViaXMiOiIjRjdBRDg0IiwiVmFjaGVzIjoiI0M3OERCRCJ9LCJzZXJpZXNCcmVha2Rvd24iOiIiLCJzZXJpZXNCcmVha2Rvd25UaW1lc2NhbGUiOiIifV0sImFsaWduTW9udGgiOnRydWUsImRpc3BsYXlMZWdlbmQiOnRydWV9&static=false&datasetcard=false" width="400" height="300" frameborder="0"></iframe>

### Datavisualisation des fromages selon leur région de production


Voici une datavisualisation qui présente les fromages de France selon leur région de production. On remarque que la Savoie est la région qui produit le plus de fromage en France.


<iframe frameborder="0" width="800" height="600" src="https://data.opendatasoft.com/map/embed/liste_des_fromages_francais2/?&static=false&scrollWheelZoom=false"></iframe>

## Requête WikiData

### Les peintures de Monet

```select distinct ?peinture
where {
    ?peinture wdt:P31/wdt:P279* wd:Q3305213 .
    ?peinture wdt:P170 wd:Q296 .
}


### Les peintures de Monet avec les labels (via le service wikibase:label) et les images associées 

SELECT DISTINCT ?peinture ?peintureLabel ?image WHERE {
  ?peinture (wdt:P31/(wdt:P279*)) wd:Q3305213;
    wdt:P170 wd:Q296.
  OPTIONAL { ?peinture wdt:P18 ?image. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr". }
}
### Les peintures de Monet avec en option (via OPTIONAL) les collections/lieux de conservation

select DISTINCT ?peinture ?peintureLabel ?image ?localisation ?localisationLabel
where {
 ?peinture wdt:P170 wd:Q296.
 ?peinture wdt:P18 ?image.
OPTIONAL {?peinture wdt:P195 ?localisation
}  
  
SERVICE wikibase:label {
bd:serviceParam wikibase:language "fr"}
}
```
