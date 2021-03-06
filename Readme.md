
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
## Dessigning DB objects

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
***
### Locales
#### Labels
There is the perfect object to be managed from i18n. Why? Because all Labels, usually are shared in every point and page of our app, all they are common terms that we need, also are terms needed in the translation.json objects (i18n),  to fill labels such as 'title', 'description' and so, in many cases, more than single translations. Then, we need to have a dictionary easy to access to easily translate our labels. We'll need just a couple of languages to load in the browser (app native and locale settings), but  other languages will lay  available  from a separated server request. I put below one example of how could be a namespace for './locales/es/translate.json' file, to store all labels.
```
{
    "geo": {
        "location": "ubicaci??n",
        "coordinates": "coordenadas",
        "points": "puntos",
        "point": "punto"
      },
      "locales": {
        "language_one": "lengua",
        "language_other": "idiomas",
        "choose language": "escoja idioma, actual: ",
        "current language_one": "idioma actual",
        "current language_other": "idiomas actuales"
      },
      "shop": {
        "currency": "moneda",
        "price": "precio",
        "purchase_one": "compra",
        "purchase_other": "compras"        
      },
      "time": {
        "date": "fecha",
        "last edit": "??ltima edici??n"
        }
   }
```
***

#### Values

There is the 'Locale' model to get fields with 'internationalizable texts', so we'll add a field named 'code'. Don't forget that the reference to all available translations were stored in previous Entity object (
```
name: 'Babbu E Fillu',
    location: { coordinates: [ '11.000', '22.000' ] },
    locales: [
      { ref: '61fa0925ad3a10b4940abe96', code: 'es' },
```

***
So next we'll write our extensible translation whith same 'ref' id, and it will be stored in our 'Locale' collection...

```
{
    _id: ObjectId("61fa0925ad3a10b4940abe96"),
    code: 'es',
    scope: 'card',
    author: 'DaSaddori',
    name: 'Profile Card',: 
    caption: 'I would like to tell you more about my life there',
    description: 'Don??t have much more to say, just send a kiss to you and good vibes'
  }, 
  
```
***
According the example above, we'll see that secondary data, such as 'read more...' links, could be loaded from another query, once the main list were loaded.

### Media 
In a simmilar way, we'll need to store some useful metadata in a table apart. This table will have name fields such as: source, MIME type, date information, description, name, and so on.
 ***
 
