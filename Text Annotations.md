# Text View

In BI Query, @ObjectModel.foreignKey.association overwrides the @objectmodel.text.association


Using Master Data (Method 1)	Using Text (Method 2)
Everything related to Master Data, Text and even Heirarchy can be achived from one view	Only used for text
Association with Dimension View withText View is required	Only Text View is enough
Annotation to be used at composite level:@ObjectModel.foreignKey.association: ”	Annotation to be used at composite level:@objectmodel.text.association: ”
It will take care of language automatically	Language has to be filtered at text level if present in text, not suitable where we have muktple language Reports
