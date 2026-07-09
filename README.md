[![GloBI Review by Elton](../../actions/workflows/review.yml/badge.svg)](../../actions/workflows/review.yml) [![GloBI](https://api.globalbioticinteractions.org/interaction.svg?accordingTo=globi:globalbioticinteractions/european-vertebrate-flower-visitation&refutes=true&refutes=false)](https://globalbioticinteractions.org/?accordingTo=globi:globalbioticinteractions/european-vertebrate-flower-visitation)

Configuration to help Global Biotic Interactions (GloBI, https://globalbioticinteractions.org) index: 

Anneliese Magrath, Nick Balfour, Maria Clara Castellanos. 2026. Vertebrate Flower Visitation in Europe. Personal Communication.

# Example Record

An example of a visitation record in this dataset is provided below: 

```json
{
  "http://www.w3.org/ns/prov#wasDerivedFrom": "line:xlsx:hash://md5/a145956849e70f1eeae954ee4b4f8f07!/All%20data!/L2",
  "http://purl.org/dc/elements/1.1/format": "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
  "Pollinator Group": "Bird",
  "Polinator ": "Serinus canarius",
  "Plant": "Aeonium arboreum",
  "Visitation Rate (visits per hour per plant)": "",
  "Mean Nectar Volume (microlitres)": "",
  "Mean Sugar Concentration (%)": "20.7",
  "Flower Colour": "Yellow",
  "Location": "Tenerife",
  "Latitude": "28.416778",
  "Longitude": "-16.398944",
  "Source": "Valido, 2004",
  "Title": "Bird flower interactions in Macronesian islands",
  "Plant Native Status": "Native",
  "Habitat Type": "Pine forest",
  "Successful Pollination": "Legitimate Visit (Observed)"
}
```


# Provenance / Origin

``` Vertebrate.visitation.AM.xlsx``` first shared by Dr. Maria Clara Castellanos to help reuse.

Following, derived datasets ```Vertebrate.visitation.AM.json ```, ```Vertebrate.visitation.AM.csv```, ```Vertebrate.visitation.AM..tsv' were generated using -  

```
cat Vertebrate.visitation.AM.xlsx \
 | preston track --algo md5 \
 | preston xlsx-stream --algo md5 \
 | mlr --jsonl cut -x -r -f '"column.*"'\ 
 | sed 's/\\n/ /g' \
 | tee Vertebrate.visitation.AM.json \
 | mlr --ijsonl --otsvlite cat \
 | tee Vertebrate.visitation.AM.tsv \
 | mlr --itsvlite --ocsv cat \
 > Vertebrate.visitation.AM.csv
```
