
# Learning Database Schemas

## Relationships between models: Entity, Locale, Media
##### Topics:
#### Load performance, on demmand
#### Locale Translation Tables, i18n, i18next, node, npm
#### E/R Modelling
#### Reactive interfaces
#### NoSQL

![RelantionshipsBetweenEntityLocaleAndMediaModelsForReactiveInterfacesAndNoSqlDatabases](https://user-images.githubusercontent.com/57029303/151651517-648ad2aa-e787-462c-96d8-88263a1f3325.png)



***
The aim of this schema is to increase freedom on select language different to profile, or default, and build lightweight objects, ready to perform a sorted list, and a separated demmand for fill the Locale objects, first labels, second texts, and last, media associated (maybe filtered by locale, too) to get the full object, in such steps as tables (1. sorted list of Entities,2. locale labels,3. locale values and 4. docs attached...), trying to imitate the NoSQL [MongoDB style](https://docs.mongodb.com/manual/tutorial/model-embedded-one-to-one-relationships-between-documents/) of schemas. 

***
