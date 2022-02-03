
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
***
### Entity

At level of dessigning models in the DB, we could draw some preview like the one below, 
wich uses references to fields in other tables ( 'Locales.id' and 'Locales.code', 'Media.video.id', 'Media.link', arrays from fields, etc.)
That object allows to perform lightweight lists, wich could load default translations, or on demmand translations, also in case of having other docs attached.
That schema is 100% independant from system or browser settings, such as i18n.lang.
```
{
    _id: ObjectId("61f217c7ad3a10b4940abe7b"),
    author: 'DaSaddori',
    image: 'Mini.png',
    name: 'Babbu E Fillu',
    location: { coordinates: [ '11.000', '22.000' ] },
    locales: [
      { ref: '61fa0925ad3a10b4940abe96', code: 'es' },
      { ref: '61fa08cdad3a10b4940abe95', code: 'en' }
    ],
    media: {
      video: [
        { ref: '61fa0925ad3a10b4940abe59', code: 'es' },
        { ref: '61fa08cdad3a10b4940abe60', code: 'en' }
      ],
      text: [
        { ref: '61fa0925ad3a10b4940abe57', code: 'es' },
      ],
      link: [
        { ref: '61fa0925ad3a10b4940abe96', code: 'es' },
        { ref: '61fa08cdad3a10b4940abe95', code: 'en' }
      ]
    }
}
```
*Note that 'ref' should be '$ref' fields in case of use MongoDB with foreign keys*

### Locales
Coming soon...
### Media 
Coming soon...
 ***
 
