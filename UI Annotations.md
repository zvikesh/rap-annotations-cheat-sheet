Context

# List Items
```
@UI.lineItem: [ { position: 30 } ]
Connection.airport_from_id as DepartureAirport,
```

# List Report Header

```
@UI.selectionField: [ { position: 10 } ] 
Connection.airport_from_id as DepartureAirport,
```

# Object Page
Related Information

```
@UI.headerInfo.typeName: 'Connection'
define view ZVKS_C_Connection_R
  as select from ZVKS_I_Connection as Connection
        purpose:  #STANDARD,
        type:     #IDENTIFICATION_REFERENCE,
        label:    'Connection',
        position: 10 } ]
…
@UI: { identification:[ { position: 40, label: 'Destination Airport Code'} ] }
Connection.airport_to_id   as DestinationAirport,
```

# List Filter

```
-- Enable Fuzzy Search
@Search.searchable: true
define view entity ZVKS_C_Flight_R
  as select from ZVKS_R_Flight
{
      @Search.defaultSearchElement: true
      @Search.fuzzinessThreshold: 0.7
      //@ObjectModel.text.association: '_Airline'
  key AirlineID,
```
