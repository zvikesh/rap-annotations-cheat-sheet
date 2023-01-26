# Metadata Annotations
@Metadata.ignorePropagatedAnnotations: true

# VDM Annotations
```
@VDM.viewType:
 #BASIC
 #COMPOSITE
 #CONSUMPTION
```
# Object Model Performance Annotations
To estimate resource requirement for data fetching. <br />
**Service Quality**
Quality of service with respect to the expected performance of the CDS view.<br />
'A' has the highest requirements and 'D' the lowest. 
```
@ObjectModel.usageType.serviceQuality:
#A (<=3 Tables)  | High Volume - Business Logic and Background        | Basic Views for ABAP Consumption
#B (<=5 Tables)  | High Volume - Business Logic and Background        | Composite Views for ABAP Consumption
#C (<=15 Tables) | UI Consumption for Transactional or List Reporting | Consumption View 
#D (>=15 Tables) | Analytical Reporting                               | Consumption View for Anlaytical Engine
#D Code Push Down to HANA DB
#P Reserved for views building hierarchy and consumed by Hierarchal View
```
**Size Category**
Expected data volume to compute the result set.
```
@ObjectModel.usageType.sizeCategory: 
#S   (<1000)
#M   (<1,00,000)
#L   (<1,00,00,000)
#XL  (<1,00,00,00,000)
#XXL (>1,00,00,00,000) 
```
**Data Class**
To support the decision on cache strategies for higher layers.
```
@ObjectModel.usageType.dataClass:
#MASTER         Business Generated Data      | Rarely Changed                          | Purchase Order
#TRANSACTIONAL  Business Generated Data      | Frequently Changed                      | Purchase Order Item
#ORGANIZATIONAL Business Configuration Data  | Created and maintained by Customer      | Company Code, Business Partner etc.
#CUSTOMIZING    Universal Configuration Data | Delivered by SAP & Extended by Customer | Countries, Language etc.
#META           Used by for shipped content  | how the system is configured or describes the technical structure of entities 
MIXED           If the CDS view contains data of multiple data classes
```
# OData Annotations

# Basic View
```
@VDM.viewType: #BASIC
```
**Object Model   Annotations**



- @OData.entitySet.name
- @OData.entityType.name

```
