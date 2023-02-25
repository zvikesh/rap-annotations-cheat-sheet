# Analytical Views

## Query Composition View

```
-- Value Help
  @Consumption: {
     filter: { selectionType: #RANGE | #INTERVAL | #SINGLE | ? #HIERARCHY_NODE,
               mandatory: true | false,
               multipleSelections: true | false }
  }
```
