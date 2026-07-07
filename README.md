[![GloBI Review by Elton](../../actions/workflows/review.yml/badge.svg)](../../actions/workflows/review.yml) [![GloBI](https://api.globalbioticinteractions.org/interaction.svg?accordingTo=globi:globalbioticinteractions/european-vertebrate-flower-visitation&refutes=true&refutes=false)](https://globalbioticinteractions.org/?accordingTo=globi:globalbioticinteractions/european-vertebrate-flower-visitation)

Configuration to help Global Biotic Interactions (GloBI, https://globalbioticinteractions.org) index: 

M. Anna, Castellanos, Maria Clara. 2026. Vertebrate Flower Visitation in Europe.

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
