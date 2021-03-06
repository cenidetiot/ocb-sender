# Query Functions
***
## Indéx navigation
* [Query Functions](#query-functions)
    * [Personalized Query Context](#personalized-query-context)
    * [Query Entities on Area](#query-entities-on-area)

## Query Functions.
### Headers 

For the examples we will use the next JSON as headers
```js
var headers = {
    'Fiware-Correlator': '3451e5c2-226d-11e6-aaf0-d48564c29d20'
}
```
But you can use another options,one empty JSON or you can ignore the headers if you don't need them

### Personalized query context.
> Example
```js
let query = "?id=.*&type=Device&georel=coveredBy&q=owner==Idowner&geometry=polygon&coords=18.879751306118546,-99.22197723761204;18.87991373199594,-99.22199869528413;18.87996449005033,-99.22190750017762;18.879984793267777,-99.2218270339072;18.879939111025056,-99.22174656763676;18.879893428769883,-99.22165537253022;18.87973100287282,-99.22145152464509;18.8795888800837,-99.22130132094026;18.879390923140832,-99.221076015383;18.87928940666914,-99.22097945585847;18.87893917436966,-99.22117793932557;18.87856356210443,-99.22121012583375;18.878675230703656,-99.22134960070255;18.878776747547473,-99.22145152464509;18.87888841600463,-99.22154808416965;18.87903053938793,-99.22144079580903;18.879203117619838,-99.22140860930085;18.87936554402868,-99.22153199091554;18.87948228791276,-99.22165537253022;18.879614259162025,-99.22181630507114;18.879751306118546,-99.22197723761204&options=keyValues"

cb.getWithQuery(query, headers)
.then((result) => console.log(result.body))
.catch((err) => console.log(err))
```

### Get headers 
if you need use the respose headers you only need to use the key headers of the result to get them
> Example
```js
cb.getWithQuery(query, headers)
.then((result) => {
    console.log(result.body) // Get the body 
    console.log(result.headers) // Get the headers
})
.catch((err) => console.log(err))
```

### Query Entities on Area.
***NOTE***: For this function the use of headers isn't available
>Usage
```js
cb.queryEntitiesOnArea(coordsPolygon, idEntity, entityType, optionskeyValues)
.then((result) => console.log(JSON.stringify(result)))
.catch((err) => console.log(err))
```
> Example
```js
cb.queryEntitiesOnArea([
    [18.879751306118546,-99.22197723761204],
    [18.87991373199594,-99.22199869528413],
    [18.87996449005033,-99.22190750017762],
    [18.879984793267777,-99.2218270339072],
    [18.879939111025056,-99.22174656763676],
    [18.879893428769883,-99.22165537253022],
    [18.87973100287282,-99.22145152464509],
    [18.8795888800837,-99.22130132094026],
    [18.879390923140832,-99.221076015383],
    [18.87928940666914,-99.22097945585847],
    [18.87893917436966,-99.22117793932557],
    [18.87856356210443,-99.22121012583375],
    [18.878675230703656,-99.22134960070255],
    [18.878776747547473,-99.22145152464509],
    [18.87888841600463,-99.22154808416965],
    [18.87903053938793,-99.22144079580903],
    [18.879203117619838,-99.22140860930085],
    [18.87936554402868,-99.22153199091554],
    [18.87948228791276,-99.22165537253022],
    [18.879614259162025,-99.22181630507114],
    [18.879751306118546,-99.22197723761204]
],".*","Device",true)
.then((result) => console.log(JSON.stringify(result)))
.catch((err) => console.log(err))
```