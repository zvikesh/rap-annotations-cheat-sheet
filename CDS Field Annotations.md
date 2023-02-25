# Analytical View

## Cube Composite View

```
@DefaultAggregation: #AVG | #COUNT | #COUNT_DISTINCT | #FORMULA, #MAX | #MIN | #NONE | #SUM 
@ObjectModel.foreignKey.association: '_BusinessTransactionType'
```

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
@Consumption.hidden: true
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
@AnalyticsDetails.query.formula : '$projection.EndingBalAmtInFreeDfndCrcy7 - $projection.DebitAmountInFreeDfndCrcy7 - CreditAmountInFreeDefinedCrcy7' 
cast( cast( 1 as abap.dec(23,2)) as fis_start_bal_fsl_ui ) as StrtgBalAmtInFreeDfndCrcy7,    
```

Exception Aggregation

```
@AnalyticsDetails: {
        exceptionAggregationSteps: [{ exceptionAggregationBehavior : #SUM, 
                                      exceptionAggregationElements: ['LedgerFiscalYear']
                                   }]
    }
```
