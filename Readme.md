### First commit

# Learning Database Schemas

## Relationships between models
#### Load performance
#### Locale Tables
#### NoSQL

![RelantionshipsBetweenEntityLocaleAndMediaModelsForReactiveInterfacesAndNoSqlDatabases](https://user-images.githubusercontent.com/57029303/151325242-4b81754e-3eed-4346-b7b1-fc89b770059c.png)

***
The aim of this schema is to increase freedom on select language different to profile, or default, and build lightweight objects, ready to perform a sorted list, and a separated demmand for fill the Locale objects, first labels, second texts, and last, media associated (maybe filtered by locale, too) to get the full object, in such steps as tables (1. sorted list of Entities,2. locale labels,3. locale values and 4. docs attached...), trying to imitate the NoSQL [MongoDB style](https://docs.mongodb.com/manual/tutorial/model-embedded-one-to-one-relationships-between-documents/) of schemas. 

***
