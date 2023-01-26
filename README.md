# Basic View
**VDM Annotations**
```
@VDM.viewType: #COMPOSITE
@VDM.lifecycle.contract.type: #PUBLIC_REMOTE_API
```

**Object Model  Performance Annotations**
```
@ObjectModel.usageType:{
 serviceQuality: #C,  //(<=15 Tables)
 sizeCategory: #S (<1000) | #M (<1,00,000) | #L (<1,00,00,000) | #XL (<1,00,00,00,000) | #XXL (>1,00,00,00,000)
 dataClass: #MASTER (Rarely Changed Data), #TRANSACTIONAL (Frequently Changed Data)`
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
