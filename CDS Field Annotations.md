# Analytical View

## Query Composition View

Add Filter

```
@Consumption: {
   filter: { selectionType: #RANGE | #INTERVAL | #SINGLE | ? #HIERARCHY_NODE,
             mandatory: true | false,
             multipleSelections: true | false }
}
```

Add Value Help 

```
@Consumption.derivation
```

Default Axis

```
@AnalyticsDetails.query.axis: #ROWS | #COLUMNS
```

Hide field from Consumption
```
@AnalyticsDetails.query.hidden: true
```

Field Text

```
@ObjectModel.text.element: 'LedgerName'
@AnalyticsDetails.query.display: #KEY | #KEY_TEXT | #TEXT | #TEXT_KEY
Ledger,
@Semantics.text
_Ledger._Text[1: Language = $parameters.P_Language].LedgerName as LedgerName,
``` 

Default Aggregation for Dimenion Field

```
@AnalyticsDetails.query.totals: #SHOW
```

Formula

```
@DefaultAggregation: #FORMULA
@AnalyticsDetails.query.formula : '$projection.IntmdDebitAmtInTransCrcy' cast( cast( 1 as abap.dec(23,2)) as fis_dr_bal_wsl ) as DebitAmountInTransCrcy,  
```

Exception Aggregation

```
@AnalyticsDetails: {
        exceptionAggregationSteps: [{ exceptionAggregationBehavior : #SUM, 
                                      exceptionAggregationElements: ['LedgerFiscalYear']
                                   }]
    }
```
