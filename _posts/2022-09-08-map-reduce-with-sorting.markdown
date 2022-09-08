---
layout: post
title:  "Map/Reduce (with sorting)"
date:   2022-09-08 13:01
categories: Javascript
---
# Cool Javascript Stuff

## Map/Reduce (with sorting)

```javascript
const data = [
  { Year: 2021, Month: 12, ElectricityCost: 42432 },

  { Year: 2020, Month: 1, ElectricityCost: 4393 },
  { Year: 2020, Month: 2, ElectricityCost: 1245 },
  { Year: 2020, Month: 3, ElectricityCost: 8658 },
  { Year: 2020, Month: 4, ElectricityCost: 7546 },
  { Year: 2020, Month: 5, ElectricityCost: 3545 },
  { Year: 2020, Month: 6, ElectricityCost: 2323 },
  { Year: 2020, Month: 7, ElectricityCost: 7674 },
  { Year: 2020, Month: 8, ElectricityCost: 3154 },
  { Year: 2020, Month: 9, ElectricityCost: 1354 },
  { Year: 2020, Month: 10, ElectricityCost: 4355 },
  { Year: 2020, Month: 11, ElectricityCost: 4313 },
  { Year: 2020, Month: 12, ElectricityCost: 4232 },
  
  { Year: 2021, Month: 11, ElectricityCost: 43213 },
  { Year: 2021, Month: 6, ElectricityCost: 23523 },
  { Year: 2021, Month: 7, ElectricityCost: 76574 },
  { Year: 2021, Month: 8, ElectricityCost: 32154 },
  { Year: 2021, Month: 1, ElectricityCost: 43493 },
  { Year: 2021, Month: 2, ElectricityCost: 12345 },
  { Year: 2021, Month: 3, ElectricityCost: 86758 },
  { Year: 2021, Month: 4, ElectricityCost: 75646 },
  { Year: 2021, Month: 5, ElectricityCost: 35445 },
  { Year: 2021, Month: 9, ElectricityCost: 13254 },
  { Year: 2021, Month: 10, ElectricityCost: 43255 },
  
  { Year: 2022, Month: 1, ElectricityCost: 59835 }
]

const workingSet = data
    .map(item => ( { SortableDate: (item.Year * 100) + item.Month, Cost: item.ElectricityCost } ))
    .sort((a,b) => a.SortableDate - b.SortableDate)
    .splice(-12);
  
const result = workingSet
    .map(item => item.Cost)
    .reduce((prev, current) => prev + current);
```
