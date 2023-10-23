# Administration

```
@Semantics.user.createdBy: true
created_by     : syuname;
@Semantics.systemDateTime.createdAt: true
created_at     : timestampl;
@Semantics.user.lastChangedBy: true
last_changed_by : syuname;
@Semantics.systemDateTime.lastChangedAt: true
//@Semantics.systemDateTime.localInstanceLastChangedAt: true  //Check the difference 
```

# Curreny Amount

```
@Semantics.amount.currencyCode: 'CurrencyCode'
price           as Price,
//@Semantics.currencyCode: true ***Not allowed in View Entity***
currency_code   as CurrencyCode,
```

# Measurement Amount

```
@Semantics.quantity.unitOfMeasure: 'DistanceUnit'
Connection.distance        as Distance,
```

# Enduser Text

```
@EndUserText:{ label: 'Airline', quickInfo: 'Airline' }
AirlineID
```
