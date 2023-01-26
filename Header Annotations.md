
# Database Table

```
```

# Basic View

```
-- Data Model
@VDM.viewType: #BASIC
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #A,
    dataClass: #CUSTOMIZING | #ORGANIZATIONAL | #MASTER | #TRANSACTIONAL,
    sizeCategory: #S (#CUSTOMIZING) | #M (#ORGANIZATIONAL) | #L (#MASTER) | #XL  (#TRANSACTIONAL)
}
--- Analytical
@Analytics : {
    dataCategory: #DIMENSION | ?, 
    dataExtraction.enabled : true | false ?Reference?
}
```

# Composite View

```
-- Data Model
@VDM.viewType: #COMPOSITE
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #B,
    dataClass: #CUSTOMIZING | #ORGANIZATIONAL | #MASTER | #TRANSACTIONAL,
    sizeCategory: #S (#CUSTOMIZING) | #M (#ORGANIZATIONAL) | #L (#MASTER) | #XL  (#TRANSACTIONAL)
}
```

# Consumption or Projection View

```
@Metadata:{
 allowExtensions: true,
 ignorePropagatedAnnotations: true
}
-- Data Model
@VDM.viewType: #CONSUMPTION
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #B,
    dataClass: #CUSTOMIZING | #ORGANIZATIONAL | #MASTER | #TRANSACTIONAL,
    sizeCategory: #S (#CUSTOMIZING) | #M (#ORGANIZATIONAL) | #L (#MASTER) | #XL  (#TRANSACTIONAL)
}
```

# SEGW API View

```
@Metadata:{
 allowExtensions: true,
 ignorePropagatedAnnotations: true
}
-- Data Model
@VDM.viewType: #COMPOSITE
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #B,
    dataClass: #CUSTOMIZING | #ORGANIZATIONAL | #MASTER | #TRANSACTIONAL,
    sizeCategory: #S (#CUSTOMIZING) | #M (#ORGANIZATIONAL) | #L (#MASTER) | #XL  (#TRANSACTIONAL)
}
@ObjectModel:{
    createEnabled: true | false 
    updateEnabled: true | false 
    deleteEnabled: true | false
}
@OData{
    entitySet.name: ***Do not use***
    entityType.name: ***Do not use***
}
```

# Behavoiur Definition API View

```
@Metadata:{
 allowExtensions: true,
 ignorePropagatedAnnotations: true
}
-- Data Model
@VDM.viewType: #COMPOSITE ?
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #B,
    dataClass: #CUSTOMIZING | #ORGANIZATIONAL | #MASTER | #TRANSACTIONAL,
    sizeCategory: #S (#CUSTOMIZING) | #M (#ORGANIZATIONAL) | #L (#MASTER) | #XL  (#TRANSACTIONAL)
}
```

# Value Help View

```
```

# Text Table View

```
```

# Dimension View

```
```

# Analytical Query View

```
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #D
    dataClass: #MIXED
    sizeCategory: #XXL 
}
```

# Reference

## Metadata Annotations

Used in Consumption or Projection View. 

**Allow Metadata Extension**<br />

To allow Metadata Extensions.<br />

```
@Metadata.allowExtensions: true | false             
```

**Ignore Metadata Propogation**<br />

Ignore the metadata from Composite View <br />

```
@MetadataignorePropagatedAnnotations: true | false
```

## VDM Annotations

**View Type**

```
@VDM.viewType:
#BASIC         Basic View
#COMPOSITE     Helpoer Composite View or SEGW API View
#CONSUMPTION   Read Only Projection View
#TRANSACTIONAL Transactional BO or Projection View
#EXTENSION:    (Used by SAP)
```

**VDM Lifecycle Contract**

```
@VDM.lifecycle.contract.type:
#SAP_INTERNAL_API:   (Used by SAP) for Transactional View
#PUBLIC_LOCAL_API:   (Used by SAP) for Views published for local use in Custom Development 
#PUBLIC_REMOTE_API:  For API Composite View 
```

## Object Model Performance Annotations

To estimate resource requirement for data fetching. <br />

**Service Quality**<br />

Quality of service with respect to the expected performance of the CDS view.<br />
'A' has the highest requirements and 'D' the lowest. 

```
@ObjectModel.usageType.serviceQuality:
#A (<=3 Tables)   | High Volume - Business Logic and Background        | Basic Views for ABAP Consumption
#B (<=5 Tables)   | High Volume - Business Logic and Background        | Composite Views for ABAP Consumption
#C (<=15 Tables)  | UI Consumption for Transactional or List Reporting | Consumption or Projection View 
#D (=<100 Tables) | Analytical Reporting                               | Consumption View for Analytical Engine
#D Code Push Down to HANA DB
#P Reserved for views building hierarchy and consumed by Hierarchal View
```

**Data Class**<br />

To support the decision on cache strategies for higher layers.

```
@ObjectModel.usageType.dataClass:
#CUSTOMIZING    Universal Configuration Data | Delivered by SAP & Extended by Customer | Countries, Language etc.
#ORGANIZATIONAL Business Configuration Data  | Created and maintained by Customer      | Company Code, Business Partner etc.
#MASTER         Business Generated Data      | Rarely Changed                          | Purchase Order
#TRANSACTIONAL  Business Generated Data      | Frequently Changed                      | Purchase Order Item
#MIXED          If the CDS view contains data of multiple data classes                 | Analytical Reporting
#META           How the system is configured or technical structure of entities. Used by for shipped content
```

**Size Category**<br />

Expected data volume to compute the result set.

```
@ObjectModel.usageType.sizeCategory: 
#S   (<1000)           | #CUSTOMIZING
#M   (<1,00,000)       | #ORGANIZATIONAL 
#L   (<1,00,00,000)    | #MASTER
#XL  (<1,00,00,00,000) | #TRANSACTIONAL
#XXL (>1,00,00,00,000) | Analytical Reporting
```

## OData Annotations

**Note**
- *Do not use*, if the length is more than 7 character Gateway will dump during SEGW generation due to offset issues. (CL_SADL_GW_MODEL_SB_GEN_MPC_PR->/IWBEP/IF_SB_GEN_MPC_PR~GET_LOCAL_TYPES)<br />
- *Not required* in Service Binding, can be renamed in Service Definition.

```
@OData.entitySet.name
@OData.entityType.name
```

## Object Model Annotations for CUD

For SEGW API development and ABAP Programming Model for Fiori.<br />
Below annotations will impact the generated metadata of Fiori Application (ABAP Programming Model for Fiori) and OData (Refer to Datasource).

```
@ObjectModel.createEnabled: true | false 
@ObjectModel.updateEnabled: true | false 
@ObjectModel.deleteEnabled: true | false
```

## Object Model Annotations for Text Table

```
@ObjectModel.dataCategory: #TEXT
```
