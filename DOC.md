---
description: |
    API documentation for modules: knowl, knowl.database, knowl.databaseAPI, knowl.db_config.

lang: en

classoption: oneside
geometry: margin=1in
papersize: a4

linkcolor: blue
links-as-notes: true
...


    
# Module `knowl` {#knowl}




    
## Sub-modules

* [knowl.database](#knowl.database)
* [knowl.databaseAPI](#knowl.databaseAPI)
* [knowl.db_config](#knowl.db_config)






    
# Module `knowl.database` {#knowl.database}

@author: Radoslav Škoviera

  This Source Code Form is subject to the terms of the Mozilla Public
  License, v. 2.0. If a copy of the MPL was not distributed with this
  file, You can obtain one at <http://mozilla.org/MPL/2.0/.>




    
## Functions


    
### Function `interact_with_db` {#knowl.database.interact_with_db}




>     def interact_with_db(
>         func: <built-in function callable>
>     )


This function is used as a wrapper for most DB interacting functions.
Its purpose is to take care of the fact that the connection to the DB can
occasionally fail after some period of inactivity.

###### Parameters

**```func```** :&ensp;<code>callable</code>
:   A function to be called

###### Returns

[type]
    Returns the value returned by the callable function. Return type depends on the returned value.


    
## Classes


    
### Class `OntologyDatabase` {#knowl.database.OntologyDatabase}




>     class OntologyDatabase(
>         config=None,
>         create=None
>     )


A front-end of an ontology database. This class provides "safe" access to most of the standard
operations provided by the rdflib.Graph class. The "safeness" of the methods lies in catching
exceptions and reconnecting shall the connection to the database "die" for whatever reason.
Additionally, this class implements the SQLAlchemy store for the triples

Create ontology database API with SQLAlchemy store.

#### Parameters

**```config```** :&ensp;<code>\[str, knowl.DBConfig]</code>, optional
:   The path to a configuration file or the configuration object. By default None,
    which results in a configuration with default parameters (see knowl.DBConfig).


**```create```** :&ensp;<code>bool</code>, optional
:   Whether or not the tables for the ontology (triplestore) should be initalized.
    Set to True if you are creating a new database, by default None.
    As per SQLAlchemy documentation, the creation operation is idempotent. Thus,
    could be left at True, unless you specifically do not want to create a new database
    if one does not exist.





    
#### Descendants

* [knowl.databaseAPI.OntologyAPI](#knowl.databaseAPI.OntologyAPI)



    
#### Instance variables


    
##### Variable `config` {#knowl.database.OntologyDatabase.config}






    
##### Variable `graph` {#knowl.database.OntologyDatabase.graph}






    
##### Variable `identifier` {#knowl.database.OntologyDatabase.identifier}








    
#### Methods


    
##### Method `add` {#knowl.database.OntologyDatabase.add}




>     def add(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `addN` {#knowl.database.OntologyDatabase.addN}




>     def addN(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `bind` {#knowl.database.OntologyDatabase.bind}




>     def bind(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `closelink` {#knowl.database.OntologyDatabase.closelink}




>     def closelink(
>         self
>     )


Closes the database connection.

    
##### Method `compute_qname` {#knowl.database.OntologyDatabase.compute_qname}




>     def compute_qname(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `destroy` {#knowl.database.OntologyDatabase.destroy}




>     def destroy(
>         self,
>         confirmation: str = None
>     )


Destroys the store for the Ontology

This will erase/destroy the database (triplestore) used to store the data.
Be very careful when calling this function.

###### Parameters

**```confirmation```** :&ensp;<code>str</code>, optional
:   [description], by default None



    
##### Method `mergeFileIntoDB` {#knowl.database.OntologyDatabase.mergeFileIntoDB}




>     def mergeFileIntoDB(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `objects` {#knowl.database.OntologyDatabase.objects}




>     def objects(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `predicate_objects` {#knowl.database.OntologyDatabase.predicate_objects}




>     def predicate_objects(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `predicates` {#knowl.database.OntologyDatabase.predicates}




>     def predicates(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `query` {#knowl.database.OntologyDatabase.query}




>     def query(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `remove` {#knowl.database.OntologyDatabase.remove}




>     def remove(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `set` {#knowl.database.OntologyDatabase.set}




>     def set(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `setCredentials` {#knowl.database.OntologyDatabase.setCredentials}




>     def setCredentials(
>         self,
>         username: str = None,
>         password: str = None
>     )


Set access credentials for the database server containing the triplestore.

###### Parameters

**```username```** :&ensp;<code>str</code>, optional
:   The username, by default None


**```password```** :&ensp;<code>str</code>, optional
:   The password. Warning, this will be visible in the DB URL! By default None



    
##### Method `setup` {#knowl.database.OntologyDatabase.setup}




>     def setup(
>         self,
>         create=False,
>         username: str = None,
>         password: str = None
>     )


Sets-up a new database connection. Call this to initialize access to the database.

###### Parameters

**```create```** :&ensp;<code>bool</code>, optional
:   Whether the tables should be created (idempotent). Only set to True if creating a new database, by default False.
    Setting the object property self.create to anything but None will override this value!


**```username```** :&ensp;<code>str</code>, optional
:   Database access credentials. Only set this if you didn't set it before (e.g. in the config file), by default None


**```password```** :&ensp;<code>str</code>, optional
:   Database access credentials. Only set this if you didn't set it before (e.g. in the config file), by default None



    
##### Method `subject_objects` {#knowl.database.OntologyDatabase.subject_objects}




>     def subject_objects(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `subject_predicates` {#knowl.database.OntologyDatabase.subject_predicates}




>     def subject_predicates(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `subjects` {#knowl.database.OntologyDatabase.subjects}




>     def subjects(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `transitive_objects` {#knowl.database.OntologyDatabase.transitive_objects}




>     def transitive_objects(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `transitive_subjects` {#knowl.database.OntologyDatabase.transitive_subjects}




>     def transitive_subjects(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `triples` {#knowl.database.OntologyDatabase.triples}




>     def triples(
>         self,
>         *args,
>         **kwargs
>     )




    
##### Method `value` {#knowl.database.OntologyDatabase.value}




>     def value(
>         self,
>         *args,
>         **kwargs
>     )






    
# Module `knowl.databaseAPI` {#knowl.databaseAPI}

@author: Radoslav Škoviera

  This Source Code Form is subject to the terms of the Mozilla Public
  License, v. 2.0. If a copy of the MPL was not distributed with this
  file, You can obtain one at <http://mozilla.org/MPL/2.0/.>




    
## Functions


    
### Function `castIntoProperURI` {#knowl.databaseAPI.castIntoProperURI}




>     def castIntoProperURI(
>         ref,
>         baseNS
>     )




    
### Function `castIntoValidTerm` {#knowl.databaseAPI.castIntoValidTerm}




>     def castIntoValidTerm(
>         val
>     )




    
### Function `isValidURI` {#knowl.databaseAPI.isValidURI}




>     def isValidURI(
>         ref
>     )





    
## Classes


    
### Class `OntoEntity` {#knowl.databaseAPI.OntoEntity}




>     class OntoEntity(
>         onto: knowl.databaseAPI.OntologyAPI,
>         **kwargs
>     )


Ontology entity (subject or object)
This class provides a convenience access to the entities inside the ontologic database.
Creating this object directly is not recommended. Use OntologyAPI.makeObject or similar function instead.

# TODO: check whether an object should be a VALUE or not (i.e. update only once)





    
#### Instance variables


    
##### Variable `exists` {#knowl.databaseAPI.OntoEntity.exists}




Returns whether this entity is still contained in the database.
More specifically, whether there are any entries containing this entity
as subject.

###### Returns

<code>bool</code>
:   Whether the entity is in the ontology



    
##### Variable `list` {#knowl.databaseAPI.OntoEntity.list}






    
##### Variable `localType` {#knowl.databaseAPI.OntoEntity.localType}




Returns local type of this entity.
That is, only the last part of the type URI (e.g., "Cube")

    
##### Variable `node` {#knowl.databaseAPI.OntoEntity.node}




BNode or other Identifier identifying this entity in the database

###### Returns

<code>Identifier</code>
:   &nbsp;



    
##### Variable `properties` {#knowl.databaseAPI.OntoEntity.properties}






    
##### Variable `type` {#knowl.databaseAPI.OntoEntity.type}






    
##### Variable `usage` {#knowl.databaseAPI.OntoEntity.usage}








    
#### Methods


    
##### Method `destroy` {#knowl.databaseAPI.OntoEntity.destroy}




>     def destroy(
>         self
>     )


Removes any entries containing this entity. Removes entries containing this entity
as subjects and objects alike.

    
##### Method `n3` {#knowl.databaseAPI.OntoEntity.n3}




>     def n3(
>         self,
>         namespace_manager=None
>     )




    
### Class `OntoProperty` {#knowl.databaseAPI.OntoProperty}




>     class OntoProperty(
>         onto: knowl.databaseAPI.OntologyAPI,
>         **kwargs
>     )


Proxy for ontologic property/predicate.
Contains various properties for quick access - i.e. properties like "functional"
can be queried from this proxy instead of the database, which should provide
some speedup. Only works if properties are queried multiple times (the first time
everything has to be loaded from the database).
Also, provides convenience access using the OOP approach.

TODO







    
### Class `OntologyAPI` {#knowl.databaseAPI.OntologyAPI}




>     class OntologyAPI(
>         config=None
>     )


A front-end of an ontology database. This class provides "safe" access to most of the standard
operations provided by the rdflib.Graph class. The "safeness" of the methods lies in catching
exceptions and reconnecting shall the connection to the database "die" for whatever reason.
Additionally, this class implements the SQLAlchemy store for the triples

Create ontology database API with SQLAlchemy store.

#### Parameters

**```config```** :&ensp;<code>\[str, knowl.DBConfig]</code>, optional
:   The path to a configuration file or the configuration object. By default None,
    which results in a configuration with default parameters (see knowl.DBConfig).


**```create```** :&ensp;<code>bool</code>, optional
:   Whether or not the tables for the ontology (triplestore) should be initalized.
    Set to True if you are creating a new database, by default None.
    As per SQLAlchemy documentation, the creation operation is idempotent. Thus,
    could be left at True, unless you specifically do not want to create a new database
    if one does not exist.




    
#### Ancestors (in MRO)

* [knowl.database.OntologyDatabase](#knowl.database.OntologyDatabase)




    
#### Instance variables


    
##### Variable `baseNS` {#knowl.databaseAPI.OntologyAPI.baseNS}






    
##### Variable `namespaces` {#knowl.databaseAPI.OntologyAPI.namespaces}




Returns a dictionary of namespaces binded to the database



    
#### Methods


    
##### Method `existEntity` {#knowl.databaseAPI.OntologyAPI.existEntity}




>     def existEntity(
>         self,
>         reference,
>         anyRecord: bool = False
>     )


Checks if the entity corresponding to the reference exists in the ontology.

###### Parameters

**```reference```** :&ensp;<code>RDF.term</code>
:   reference to the entity


**```anyRecord```** :&ensp;<code>bool</code>, optional
:   If set to True, will search for any entry referencing the object. If set to False,
    existence of the entity's type is required (searched for). By default False

###### Returns

<code>bool</code>
:   Whether the specified entity exists within the database



    
##### Method `getEntity` {#knowl.databaseAPI.OntologyAPI.getEntity}




>     def getEntity(
>         self,
>         reference,
>         makeIfDoesNotExist: bool = False
>     )


Returns a proxy to an entity in the ontology.
If the object corresponding to the reference already exists in the database then simply the reference
is returned. If it does not exist, it will be created.

###### Parameters

**```reference```** :&ensp;<code>Identifier</code>
:   [description]


**```makeIfDoesNotExist```** :&ensp;<code>bool</code>
:   If set to True, a blank entity with the specified reference will be created and returned.
    I.e., an entity will be created even if one does not exist within the database.

###### Returns

<code>[OntoEntity](#knowl.databaseAPI.OntoEntity "knowl.databaseAPI.OntoEntity")</code>
:   A proxy for the entity in the ontology.



    
##### Method `getEntsByClass` {#knowl.databaseAPI.OntologyAPI.getEntsByClass}




>     def getEntsByClass(
>         self,
>         cls,
>         typePredicate: rdflib.term.URIRef = rdflib.term.URIRef('http://www.w3.org/1999/02/22-rdf-syntax-ns#type')
>     )


Returns a list of entities of the specified class or type.

###### Parameters

**```cls```** :&ensp;<code>\[str, URIRef]</code>
:   The identifier of the class to be searched for.


**```typePredicate```** :&ensp;<code>URIRef</code>, optional
:   This paramaters can optionally by changed to modify the predicate
    denoting the "entity is of class" statement. Under normal circumstances,
    there shall be no need to actually change this, by default RDF.type.

###### Returns

<code>list</code> of <code>[OntoEntity](#knowl.databaseAPI.OntoEntity "knowl.databaseAPI.OntoEntity")</code>
:   A list of objects with the specified type.



    
##### Method `getProperty` {#knowl.databaseAPI.OntologyAPI.getProperty}




>     def getProperty(
>         self,
>         property
>     )




    
##### Method `isAncestorOf` {#knowl.databaseAPI.OntologyAPI.isAncestorOf}




>     def isAncestorOf(
>         self,
>         alleged_ancestor,
>         thing
>     )




    
##### Method `makeEntity` {#knowl.databaseAPI.OntologyAPI.makeEntity}




>     def makeEntity(
>         self,
>         reference,
>         attributes: dict = {},
>         **kwargs
>     )


Creates and object in this ontology
Objects should only be created using this function (i.e. not by instantiating the OntoObject class directly).
The main reason for this is that the OntoObject does not existence of such object in the current ontology
and thus duplicates could be produced.

###### Parameters

**```reference```** :&ensp;<code>URIRef</code> or <code>similar</code>
:   URI reference of the object to be created. If the provided reference referres to a class a new object
    is instantiated instead of providing reference to an object already existing in the database.

###### Returns

<code>[OntoEntity](#knowl.databaseAPI.OntoEntity "knowl.databaseAPI.OntoEntity")</code>
:   A proxy for the entity in the ontology.



    
### Class `ProxyAttribute` {#knowl.databaseAPI.ProxyAttribute}




>     class ProxyAttribute(
>         ns,
>         caller
>     )


This object serves as proxy for OntoEntity's property.
It is a "hack" to make namespace work in the dot notation.
I.e., entity.Namespace.property







    
### Class `ProxyReference` {#knowl.databaseAPI.ProxyReference}




>     class ProxyReference(
>         name,
>         namespace,
>         caller
>     )


RDF URI Reference: <http://www.w3.org/TR/rdf-concepts/#section-Graph-URIref>


    
#### Ancestors (in MRO)

* [rdflib.term.URIRef](#rdflib.term.URIRef)
* [rdflib.term.Identifier](#rdflib.term.Identifier)
* [rdflib.term.Node](#rdflib.term.Node)
* [builtins.str](#builtins.str)








    
# Module `knowl.db_config` {#knowl.db_config}

@author: Radoslav Škoviera

  This Source Code Form is subject to the terms of the Mozilla Public
  License, v. 2.0. If a copy of the MPL was not distributed with this
  file, You can obtain one at <http://mozilla.org/MPL/2.0/.>





    
## Classes


    
### Class `DBConfig` {#knowl.db_config.DBConfig}




>     class DBConfig(
>         host: str = '127.0.0.1',
>         port: int = 3306,
>         username: str = None,
>         password: str = None,
>         dialect: str = 'mysql',
>         driver: str = 'pymysql',
>         database: str = 'onto',
>         baseURL: str = 'http://dbpedia.org/ontology/',
>         namespaces: dict = {'foaf': Namespace('http://xmlns.com/foaf/0.1/')}
>     )


Creates a configuration object for RDFLib-SQLAlchemy store database.

#### Parameters

**```host```** :&ensp;<code>str</code>, optional
:   The location/hostname (e.g. IP address) where the database is running.
    Use the "localhost" to target DB running on the local machine -which is also the default "127.0.0.1"


**```port```** :&ensp;<code>int</code>, optional
:   The port on which the database server is running, by default 3306


**```username```** :&ensp;<code>str</code>, optional
:   Username credential to sign into the database. Make sure the provided user
    has the proper rights for the database, by default the username is not specified


**```password```** :&ensp;<code>str</code>, optional
:   The password for the user. Warning: this is visible in the DB URI string!, by default the password is not specified


**```dialect```** :&ensp;<code>str</code>, optional
:   Database "dialect", e.g., mysql, postgresql and so on. Search for SQLAlchemy dialects for more info, by default "mysql"


**```driver```** :&ensp;<code>str</code>, optional
:   Driver for the database, i.e. the library that will be used to communicate with the database.
    Make sure to install and select the proper driver for the chosen dialect, by default "pymysql"


**```database```** :&ensp;<code>str</code>, optional
:   Name of the specific database on the database server, where data will be saved, by default "onto"


**```baseURL```** :&ensp;<code>str</code>, optional
:   Base URL or ontology IRI. This is basically the identifier of the ontology.
    Multiple ontologies can coexist inside a single database (specified by the "database" argument)
    provided they have different identifiers. Also, objects from an ontology with different IRI/base URL
    are not visible to other ontology IRI, by default "http://dbpedia.org/ontology/"


**```namespaces```** :&ensp;<code>dict</code>, optional
:   Additional namespaces to bind to the database. When creating custom ontology classes,
    you are most likely using a custom namespace (e.g. your ontology IRI). You can bind that namespace
    (add shorthand reference to it) by specifing it here. Also, additional/non-standard namespaces
    or collections of ontology classes can be provided, by default {"foaf": FOAF}






    
#### Class variables


    
##### Variable `IN_MEMORY` {#knowl.db_config.DBConfig.IN_MEMORY}







    
#### Instance variables


    
##### Variable `DB_URI` {#knowl.db_config.DBConfig.DB_URI}




Database URI or database access string that is used to access the database.
This property never contains the access credentials and thus can be used e.g.,
to display the access string for verification. Use the "getDB_URI" method
to generate the propper access string that can be used to connect to the database.

###### Returns

<code>str</code>
:   Database access string without the access credentials.



    
##### Variable `baseURL` {#knowl.db_config.DBConfig.baseURL}






    
##### Variable `database` {#knowl.db_config.DBConfig.database}






    
##### Variable `dialect` {#knowl.db_config.DBConfig.dialect}






    
##### Variable `driver` {#knowl.db_config.DBConfig.driver}






    
##### Variable `host` {#knowl.db_config.DBConfig.host}






    
##### Variable `namespaces` {#knowl.db_config.DBConfig.namespaces}






    
##### Variable `port` {#knowl.db_config.DBConfig.port}






    
##### Variable `uniqueID` {#knowl.db_config.DBConfig.uniqueID}




Complete unique identifier of the specific ontology. Unlike the IRI or the DB URI,
this ID takes into consideration both resource identifiers and combines them. Also,
unlike the DB URI, which includes the plain login credentials for the database,
this ID is hashed, therefore it can be used as a public identifier without
the risk of exposing sensitive information.
The property only works properly if access credentials are set. Otherwise,
it is recommended to use the "getUniqueID function that allows to enter the credentials.

###### Returns

<code>int</code>
:   Hashed ID of the specific ontology database.




    
#### Static methods


    
##### `Method factory` {#knowl.db_config.DBConfig.factory}




>     def factory(
>         cfg=None
>     )


Universal factory funciton for creating a database config.
One of three parameters could be specified:
    None - will create a new config with the default parameters
    str - path to the YAML or JSON file containing the configuration parameters
    DBConfig - an already initialized configuration object
The purpose of this factory funciton is to make universal interface.

###### Parameters

**```cfg```** :&ensp;<code>\[None, str, [DBConfig](#knowl.db\_config.DBConfig "knowl.db\_config.DBConfig")]</code>, optional
:   Initialization parameters for the configuration object, by default None

###### Returns

<code>[DBConfig](#knowl.db\_config.DBConfig "knowl.db\_config.DBConfig")</code>
:   &nbsp;



    
##### `Method fromFile` {#knowl.db_config.DBConfig.fromFile}




>     def fromFile(
>         filepath: str
>     )


Initialize the config from a YAML or JSON file. The configuration could be partial,
i.e. the values not directly specified in the file will be initialized
with the default values (see DBConfig constructor)

###### Parameters

**```filepath```** :&ensp;<code>str</code>
:   Path to the configuration file

###### Returns

<code>[DBConfig](#knowl.db\_config.DBConfig "knowl.db\_config.DBConfig")</code>
:   The configuration object with values inilitalized from the provided



    
##### `Method getInMemoryConfig` {#knowl.db_config.DBConfig.getInMemoryConfig}




>     def getInMemoryConfig(
>         database: str = 'onto',
>         baseURL: str = 'http://dbpedia.org/ontology/',
>         namespaces: dict = {'foaf': Namespace('http://xmlns.com/foaf/0.1/')}
>     )





    
#### Methods


    
##### Method `getDB_URI` {#knowl.db_config.DBConfig.getDB_URI}




>     def getDB_URI(
>         self,
>         username: str = None,
>         password: str = None
>     )


Generates database access string that can be used to connect to the database.
This string will contain the access credentials (username and password)!

###### Parameters

**```username```** :&ensp;<code>str</code>, optional
:   DB access credentials (if not provided before), by default None


**```password```** :&ensp;<code>str</code>, optional
:   DB access credentials (if not provided before), by default None

###### Returns

<code>Literal</code>
:   The DB access string.



    
##### Method `getUniqueID` {#knowl.db_config.DBConfig.getUniqueID}




>     def getUniqueID(
>         self,
>         username: str = None,
>         password: str = None
>     )


Works exactly like the "uniqueID" property but allows specification
of the access credentials for the database server.

###### Parameters

**```username```** :&ensp;<code>str</code>, optional
:   DB server access credentials, by default None


**```password```** :&ensp;<code>str</code>, optional
:   DB server access credentials, by default None

###### Returns

<code>int</code>
:   Unique ontology ID.



    
##### Method `setCredentials` {#knowl.db_config.DBConfig.setCredentials}




>     def setCredentials(
>         self,
>         username: str = None,
>         password: str = None
>     )


Set access credentials for the database server.

###### Parameters

**```username```** :&ensp;<code>str</code>, optional
:   The username, by default None


**```password```** :&ensp;<code>str</code>, optional
:   The password. Warning, this will be visible in the DB URL! By default None



    
### Class `MissingParameterWarning` {#knowl.db_config.MissingParameterWarning}




>     class MissingParameterWarning(
>         *args,
>         **kwargs
>     )


Helper class meaning a necessary parameter was not provided.


    
#### Ancestors (in MRO)

* [builtins.Warning](#builtins.Warning)
* [builtins.Exception](#builtins.Exception)
* [builtins.BaseException](#builtins.BaseException)







-----
Generated by *pdoc* 0.9.2 (<https://pdoc3.github.io>).
