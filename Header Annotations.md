
# Metadata Annotations

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

# VDM Annotations

```
@VDM.viewType:
 #BASIC
 #COMPOSITE
 #CONSUMPTION 
```

# Object Model Performance Annotations

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
#MASTER         Business Generated Data      | Rarely Changed                          | Purchase Order
#TRANSACTIONAL  Business Generated Data      | Frequently Changed                      | Purchase Order Item
#ORGANIZATIONAL Business Configuration Data  | Created and maintained by Customer      | Company Code, Business Partner etc.
#CUSTOMIZING    Universal Configuration Data | Delivered by SAP & Extended by Customer | Countries, Language etc.
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

# OData Annotations

*Note*
- Do not use, if the length is more than 7 character Gateway will dump during SEGW generation due to offset issues. (CL_SADL_GW_MODEL_SB_GEN_MPC_PR->/IWBEP/IF_SB_GEN_MPC_PR~GET_LOCAL_TYPES)<br />
- Not required in Service Binding, can be renamed in Service Definition.

```
@OData.entitySet.name
@OData.entityType.name
```
# Object Model Annotations for CUD

For SEGW API development and ABAP Programming Model for Fiori

```
@ObjectModel.createEnabled: true | false 
@ObjectModel.updateEnabled: true | false 
@ObjectModel.deleteEnabled: true | false
}
```

# Basic View

```
@Metadata:{
 allowExtensions: true,
 ignorePropagatedAnnotations: true
}
```
