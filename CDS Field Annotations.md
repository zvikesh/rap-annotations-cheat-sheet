# Basic View Annotations

## Semantic Annotations 
Semantic Annotations are for Consumption View reusability

```
-- Currency
@Semantics.amount.currencyCode 
@Semantics.currencyCode 
-- Quantity
@Semantics.quantity.unitOfMeasure 
@Semantics.unitOfMeasure 
-- Change Log Date
@Semantics.systemDate...
@Semantics.systemDate...
-- Change Log Date
@Semantics.systemTime...
@Semantics.systemTime...
-- Change Log Time Stamp
//Used for Locking
@Semantics.systemDateTime...
@Semantics.systemDateTime...
-- Text View
@Semantics.language //Language Key
@Semantics.text     //Text Value

-- 
@Semantics.businessDate 
@Semantics.fiscal Information on the fiscal year

@ObjectModel.association.type
@ObjectModel.text.Association
@ObjectModel.foreignKey. association
```

## Foreign Key Association

Foreign Key Association annotation helps to derivce Value Help for Consumption View
*The cardinality of a foreign key association must be either [0..1] or [1..1] / [1].

```
@ObjectModel.foreignKey.association: '_Country'
```

# Analytical View

## Cube Composite View

```
@DefaultAggregation: #AVG | #COUNT | #COUNT_DISTINCT | #FORMULA, #MAX | #MIN | #NONE | #SUM 
@ObjectModel.foreignKey.association: '_BusinessTransactionType'
@Consumption.hidden: true
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

[rap-annotations-cheat-sheet/Value Help Annotations.md](https://github.com/zvikesh/rap-annotations-cheat-sheet/blob/main/Value%20Help%20Annotations.md)

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
