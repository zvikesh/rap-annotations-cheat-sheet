# @Consumption.derivation
Annotation serves two purposes:
1.	It provides the default value, using a derivation logic in place of hardcoding during initial loading of the application.
2.	In case user wants to edit the default value, default value help will be shown to user with the values from lookupEntity.

## Limitation
Default value help derived from lookupEntity will not perform filtration on the displayed data, it fetches all the records.

# @Consumption.valueHelpDefinition
This annotation:
1.	Overwrites the default value help provided by @Consumption.derivation.
2.	Can also be provided filter values depending upon additional Binding.

# @Consumption.filter
To be used to make non-parameter fields a filter on the Design Studio pop up.
@Consumption.filter:{ selectionType: #RANGE, multipleSelections: true }
## Note
#RANGE is not possible for parameters of CDS view.
 

# @Consumption.hidden:true
Parameters marked with @Consumption.hidden: true should mandatorily have @Consumption.derivation or @Environment.systemField annotations to derive values at runtime.

Also, binding value used for derivation should also have @Consumption.derivation annotation to ensure the derivation logic, as the values derivation will takes place in a chain for all the CDS View parameter depending on their dependency on each other.

# @ValueHelp:’_AssociationName’
This is legacy way and can be avoided as data can only be filtered by values used in on condition and affect the result due to cardinality.
