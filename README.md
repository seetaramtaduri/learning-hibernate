# learning-hibernate

#Hibernate Basics
We will explore  the basics of hibernate before we jump on to further exploration

Architecture

=>Hibernate is a pure Java object-relational mapping (ORM) that allows  to map plain old Java objects to relational database tables using (XML) configuration files or by annotation methods

=>Provides a simple API for storing and retrieving Java objects directly  from the database

=>This is a middle-ware that manages persistence

=>Provides an abstraction layer between the domain model and the database

ORM  API  provides  service for performing

=>  Basic CRUD operations on objects of persistent classes

=> Is an API for specifying queries of classes

=>  A facility for specifying mapping metadata

=> A technique for the ORM implementation to interact with transactional objects .

#CORE INTERFACES IN HIBERNATE

Session interface

=>The Session interface is the primary interface used by Hibernate applications.

=>An instance of Session is lightweight and is inexpensive to create and destroy.This is important because your application will need to create and destroy sessions all the time, perhaps on every request.

=>Hibernate sessions are not thread-safe and should by design be used by only one thread at a time.

=>The Hibernate notion of a session is something between connection and transaction.

 

#Session-factory interface

=>The application obtains Session instances from a Session-factory. Compared to

the Session interface, this object is much less exciting.

=>The Session-factory is certainly not lightweight! It’s intended to be shared

among many application threads. There is typically a single Session-factory for the

whole application,created during application initialization, for example. However,

if your application accesses multiple databases using Hibernate, you’ll need

a Session Factory for each database.

=>The Session Factory caches generated SQL statements and other mapping

metadata that Hibernate uses at run-time. It also holds cached data that has been

read in one unit of work and may be reused in a future unit of work (only if class

and collection mappings specify that this second-level cache is desirable).

 

#Configuration interface

The Configuration object is used to configure and bootstrap Hibernate. The

application uses a Configuration instance to specify the location of mapping documents

and Hibernate-specific properties and then create the Session Factory.

 

#Transaction interface

=>The Transaction interface is an optional API. Hibernate applications may choose

not to use this interface, instead managing transactions in their own infrastructure

code.

=>A Transaction abstracts application code from the underlying transaction

implementation—which might be a JDBC transaction

Query and Criteria interfaces

=>The Query interface allows you to perform queries against the database and control

how the query is executed. Queries are written in HQL or in the native SQL

dialect of your database.

=>A Query instance is used to bind query parameters, limit

the number of results returned by the query, and finally to execute the query.

=>The Criteria interface is very similar; it allows you to create and execute object-oriented

criteria queries.

Hibernates Callbacks

=>Callback interfaces allow the application to receive a notification when something

interesting happens to an object

for example:

public Boolean onSave(Session s); Called before the object is saved to the database

public Boolean onUpdate(Session s); Called before the object is updated in database

public Boolean onDelete(Session s); Called before the object is deleted in database

public Boolean onLoad(Session s); Called after the object is loaded from  database

=>Hibernate applications don’t need to implement these callbacks, but

they’re useful for implementing certain kinds of generic functionality, such as creating

audit records.