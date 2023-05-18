# dpsir.rq
**Code examples:** [curl](#curl)
### SPARQL
```sparql
PREFIX wdt: <https://kg-ipclimatec-reports.wikibase.cloud/prop/direct/>
PREFIX wd:  <https://kg-ipclimatec-reports.wikibase.cloud/entity/>
PREFIX p:   <https://kg-ipclimatec-reports.wikibase.cloud/prop/>
PREFIX pq:  <https://kg-ipclimatec-reports.wikibase.cloud/prop/qualifier/>

SELECT ?driver ?driverLabel ?pressure ?pressureLabel ?state ?stateLabel ?impact ?impactLabel ?response ?responseLabel WHERE {
  ?paragraph wdt:P1 wd:Q18; p:P3 ?fact .
  OPTIONAL { ?fact pq:P18 ?driver }
  OPTIONAL { ?fact pq:P19 ?pressure }
  OPTIONAL { ?fact pq:P20 ?state }
  OPTIONAL { ?fact pq:P10 ?impact }
  OPTIONAL { ?fact pq:P21 ?response }

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```
[run](https://kg-ipclimatec-reports.wikibase.cloud/query/embed.html#PREFIX%20wdt%3A%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fprop%2Fdirect%2F%3E%0APREFIX%20wd%3A%20%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fentity%2F%3E%0APREFIX%20p%3A%20%20%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fprop%2F%3E%0APREFIX%20pq%3A%20%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fprop%2Fqualifier%2F%3E%0A%0ASELECT%20%3Fdriver%20%3FdriverLabel%20%3Fpressure%20%3FpressureLabel%20%3Fstate%20%3FstateLabel%20%3Fimpact%20%3FimpactLabel%20%3Fresponse%20%3FresponseLabel%20WHERE%20%7B%0A%20%20%3Fparagraph%20wdt%3AP1%20wd%3AQ18%3B%20p%3AP3%20%3Ffact%20.%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP18%20%3Fdriver%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP19%20%3Fpressure%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP20%20%3Fstate%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP10%20%3Fimpact%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP21%20%3Fresponse%20%7D%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A) or [edit](https://kg-ipclimatec-reports.wikibase.cloud/query/#PREFIX%20wdt%3A%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fprop%2Fdirect%2F%3E%0APREFIX%20wd%3A%20%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fentity%2F%3E%0APREFIX%20p%3A%20%20%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fprop%2F%3E%0APREFIX%20pq%3A%20%20%3Chttps%3A%2F%2Fkg-ipclimatec-reports.wikibase.cloud%2Fprop%2Fqualifier%2F%3E%0A%0ASELECT%20%3Fdriver%20%3FdriverLabel%20%3Fpressure%20%3FpressureLabel%20%3Fstate%20%3FstateLabel%20%3Fimpact%20%3FimpactLabel%20%3Fresponse%20%3FresponseLabel%20WHERE%20%7B%0A%20%20%3Fparagraph%20wdt%3AP1%20wd%3AQ18%3B%20p%3AP3%20%3Ffact%20.%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP18%20%3Fdriver%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP19%20%3Fpressure%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP20%20%3Fstate%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP10%20%3Fimpact%20%7D%0A%20%20OPTIONAL%20%7B%20%3Ffact%20pq%3AP21%20%3Fresponse%20%7D%0A%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A)


### Output
<table>
  <tr>
    <td><b>driver</b></td>
    <td><b>pressure</b></td>
    <td><b>state</b></td>
    <td><b>impact</b></td>
    <td><b>response</b></td>
  </tr>
  <tr>
## Code examples
### curl
```shell
curl -s https://raw.githubusercontent.com/egonw/IPCC-Queries/master/sparql/dpsir.rq \
  | sed 's+<lang/>+en+' > dpsir.rq

curl -H "Accept: text/tab-separated-values" \
  -G https://kg-ipclimatec-reports.wikibase.cloud/query/sparql \
  --data-urlencode query@dpsir.rq
```
This SPARQL query is available under CCZero.