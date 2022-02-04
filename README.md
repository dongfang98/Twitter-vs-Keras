# Twitter-vs-Keras
## Syntax
#### Twitter API
#### Keras API
## Entity versus procedural 
#### Twitter API
Twitter API contains only 4 kinds of operation: 
- GET, 
- POST, 
- PUT, 
- DELETE

These CRUD operations: create(POST), read(GET), update(PUT), delete(DELETE) made up most of twitter api.

Though the commands is organized by function groups, all basic operation is based on the data stucture, the entity of tweets. Thus user can have a easy start using these API command without knowing the actual procedure or state of the operation.

Also, the data relationship, or, data structure, is inherit in the call. Take the call "DELETE /2/users/:source_user_id/blocking/:target_user_id" as an example, we can see how the blocking list is organized, and we can tell that the blocking list is under source_user_id. The hierarchy is clearly shown in the call.

#### Keras API
Keras API contains a huge amount of functions and procedures, and is organized (or catagorized) under function types. For example, "model", and functions under model contains "model.fit", "model.compile", "model.evaluate", etc. 

As we can see, Keras API provide us only functions, or, group of functions to access. 

Unlike Twitter API, we have nothing to know about its data structure, and we do not care about this, nor do we have any data structure to be edited. For a deep learning API, we only need to use function calls --- the action that need the API to complete. I think this is why Keras is designed to be a procedure API instead of a Entity based one.
## Status
#### Twitter API
#### Keras API
## Documentation
#### Twitter API
#### Keras API
## Versioning
#### Twitter API
#### Keras API
