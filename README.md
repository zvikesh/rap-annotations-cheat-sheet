# Header Annotations
## VDM Annotations
```
@VDM.viewType:
 #BASIC
 #COMPOSITE
 #CONSUMPTION
```
## Object Model Performance Annotations
To estimate resource requirement for data fetching.
**Service Quality**
Quality of service with respect to the expected performance of the CDS view. 'A' has the highest requirements and 'D' the lowest. 
```
@ObjectModel.usageType.serviceQuality: 
- #A (<=3 Tables)  | High Volume - Business Login and Background        | Basic Views for ABAP Consumption
- #B (<=5 Tables)  | High Volume - Business Login and Background        | Composite Views for ABAP Consumption
- #C (<=15 Tables) | UI Consumption for Transactional or List Reporting | Consumption View 
- #X (>=15 Tables) | Analytical Reporting                               | Consumption View for Anlaytical Engine
- #P Reserved for views that are used to structure the view hierarchy and that don't have any consumer outside of the hierarchy
```
**Size Category**
```
@ObjectModel.usageType.sizeCategory: 
- #S (<1000)
- #M (<1,00,000)
- #L (<1,00,00,000)
- #XL (<1,00,00,00,000)
- #XXL (>1,00,00,00,000) 
```
**Data Class**
```
@ObjectModel.usageType.dataClass: #MASTER (Rarely Changed) | #TRANSACTIONAL (Frequently Changed) | #ORGANIZATIONAL (Configuration) | #CUSTOMIZING (?) | #META (?) 
```


# Basic View
**VDM Annotations**
```
@VDM.viewType: #BASIC
```
**Object Model   Annotations**


**Metadata Annotations**
- @Metadata.ignorePropagatedAnnotations: true

**OData Annotations**
- @OData.entitySet.name
- @OData.entityType.name

**Object Model CUD Annotations**
```
ObjectModel:{
    createEnabled: true | false, 
    updateEnabled: true | false, 
    deleteEnabled: true | false
}
```
