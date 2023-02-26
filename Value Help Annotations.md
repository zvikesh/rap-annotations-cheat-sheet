# Paremeter and Field Annotations

## @Consumption.derivation
Annotation serves two purposes:
1.	It provides the default value, using a derivation logic in place of hardcoding during initial loading of the application.
2.	In case user wants to edit the default value, default value help will be shown to user with the values from lookupEntity.

Limitation
Default value help derived from lookupEntity will not perform filtration on the displayed data, it fetches all the records.

## @Consumption.valueHelpDefinition
This annotation:
1.	Overwrites the default value help provided by @Consumption.derivation.
2.	Can also be provided filter values depending upon additional Binding.

## @Consumption.filter
To be used to make non-parameter fields a filter on the Design Studio pop up.
@Consumption.filter:{ selectionType: #RANGE, multipleSelections: true }

Note
#RANGE is not possible for parameters of CDS view.

## @Consumption.hidden:true
Parameters marked with @Consumption.hidden: true should mandatorily have @Consumption.derivation or @Environment.systemField annotations to derive values at runtime.

Also, binding value used for derivation should also have @Consumption.derivation annotation to ensure the derivation logic, as the values derivation will takes place in a chain for all the CDS View parameter depending on their dependency on each other.

## @ValueHelp:’_AssociationName’
This is legacy way and can be avoided as data can only be filtered by values used in on condition and affect the result due to cardinality.

# Domain Value Help

## Value Help View

```
@AbapCatalog.sqlViewName: '<SQLVIewName>' //Input: <SQLVIewName>
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: '<Value Help Description>' //Input: <Value Help Description>
-- Data Model
@VDM.viewType: #BASIC
@ObjectModel.dataCategory: #VALUE_HELP
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #A,
    dataClass: #CUSTOMIZING | #ORGANIZATIONAL | #MASTER | #TRANSACTIONAL,
    sizeCategory: #S (#CUSTOMIZING) | #M (#ORGANIZATIONAL) | #L (#MASTER) | #XL  (#TRANSACTIONAL)
}
-- Drop Down
@ObjectModel.resultSet.sizeCategory: #XS
--- Analytical
@Analytics : {
    dataCategory: #DIMENSION, 
    dataExtraction.enabled : true | false ?Reference?
}
-- Fuzzy Search
@Search.searchable: true
-- Foreign Key Associations
@ObjectModel.representativeKey: 'Code'
define view <Z1I_ViewNameVH> //Input: <Z1I_ViewNameVH>
  as select from dd07l
  association [0..*] to <Z1I_ViewNameVHText> as _Text on $projection.Code = _Text.Code //Input: <Z1I_ViewNameVHText>
{
      @ObjectModel.text.association: '_Text'
      @Search.defaultSearchElement: true
key cast( domvalue_l as <DataElementName> ) as Code, //Input: <DataElementName>
      _Text
}
where
      dd07l.domname  = '<DomaintName>' //Input: <DomainName> 
  and dd07l.as4local = 'A'
```

## Value Help Text View

```
@AbapCatalog.sqlViewName: '<SQLVIewName>' //Input: <SQLVIewName>
@AbapCatalog.compiler.compareFilter: true
@AbapCatalog.preserveKey: true
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: '<Value Help Description> Text' //Input: <Value Help Description>
-- Data Model
@VDM.viewType: #BASIC
@ObjectModel.dataCategory: #TEXT
-- Performance
@ObjectModel.usageType:{
    serviceQuality: #A,
    dataClass: #CUSTOMIZING | #ORGANIZATIONAL | #MASTER | #TRANSACTIONAL,
    sizeCategory: #S (#CUSTOMIZING) | #M (#ORGANIZATIONAL) | #L (#MASTER) | #XL  (#TRANSACTIONAL)
}
-- Fuzzy Search
@Search.searchable: true
-- Foreign Key Associations
@ObjectModel.representativeKey: 'Code'
define view <ZI1_ViewNameVHText> //Input: <ZI1_ViewNameVHText> 
  as select from dd07t 
  association [0..*] to <ZI1_ViewNameVH> as _Code     on $projection.Code     = _Code.Code //Input: <ZI1_ViewNameVH>
  association [0..1] to I_Language       as _Language on $projection.Language = _Language.Language
{
      @Search.defaultSearchElement: true
  key cast( domvalue_l as <DataElementName> ) as Code, //Input: <DataElementName>
      @Semantics.language: true
      @ObjectModel.foreignKey.association: '_Language'
  key ddlanguage                              as Language,
      @Search.defaultSearchElement: true
      @Semantics.text: true
      ddtext                                  as Description,
      _Code,
      _Language
}
where
      domname  = '<DomaintName>' //Input: <DomainName>
  and as4local = 'A'
```
