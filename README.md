# Basic View
**VDM Annotations**
```
@VDM.viewType: #BASIC
```
**Object Model  Performance Annotations**
```
@ObjectModel.usageType:{
 serviceQuality: #A (<=3 Tables) | #B (<=5 Tables) | #C (<=15 Tables) | #X (?) | #P (?)
 sizeCategory: #S (<1000) | #M (<1,00,000) | #L (<1,00,00,000) | #XL (<1,00,00,00,000) | #XXL (>1,00,00,00,000)
 dataClass: #MASTER (Rarely Changed) | #TRANSACTIONAL (Frequently Changed) | #ORGANIZATIONAL (Configuration) | #CUSTOMIZING (?) | #META (?) 
}
```

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
