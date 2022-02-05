# Twitter-vs-Keras
## Syntax
#### Twitter API
Twitter API are straight forward in syntax, user friendly designed. Most of it's functions are based on create(POST), read(GET), update(PUT), delete(DELETE) actions. This formalized designing strategy helps users to build their own function easily. Also, Twitter API provides user with packaged functions, especially those related to Twitter website. For example, Twitter API has build in functions surpporting information lookup
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
### Twitter API
#### [Twitter API v2](https://developer.twitter.com/en/docs/twitter-api)  
![image](https://user-images.githubusercontent.com/90479627/152601903-b2316ee8-7a19-4ad2-bed1-ff96cc7d64d0.png)

_Feature:_
> * New and More detailed data objects
> * New parameters to request objects and fields
> * Advanced metrics
> * Receive and filter data with contextual Tweet annotations
> * Filter on and identify which Tweets belong to a reply thread
> * Advanced access level for Academic Researchers
> * [And so much more click here](https://developer.twitter.com/en/docs/twitter-api/getting-started/about-twitter-api#What's)
___

#### [Twitter Standard v1.1](https://developer.twitter.com/en/docs/twitter-api/v1)
**Some Available Endpoint:**
Tweets  | Users| Direct Messages| Trends| Geo|
--------- | --------| -------| --------| --------|
Post, retrieve, and engage with Tweets  | 	Manage account settings and profile | Sending and receiving events | 	Get trends near a location | 	Get information about a place
Get Tweet timelines  | Mute, block, and report users | Welcome Messages | Get locations with trending topics | Get places near a location
Search Tweets: 7 day*  | Follow, search, and get users | Quick Replies |
Curate a collection of Tweets | Create and manage lists | Conversation management |
___
#### [Twitter Premium v1.1](https://developer.twitter.com/en/docs/twitter-api/premium)
The premium Search Tweets offering provides access to the past 30 days of Twitter data or to the full history of Twitter data dependent on the endpoint selected.

These endpoints provide functionality beyond what’s available in our standard search endpoint, including:

    1. More Tweets per request
    2. Higher rate limits
    3. A counts endpoint that returns time-series counts of Tweets (only available at paid tiers)
    4. More complex querying tools
    5. Metadata enrichments, such as expanded URLs and improved profile geo information 

**Key resources:**

* [Read the docs](https://developer.twitter.com/en/docs/twitter-api/premium/search-api/overview)
* [30 day search pricing](https://developer.twitter.com/en/pricing/search-30day)
* [Full-archive search pricing](https://developer.twitter.com/en/pricing/search-fullarchive)
* [Python client](https://github.com/twitterdev/search-tweets-python)
* [Ruby client](https://github.com/twitterdev/search-tweets-ruby)
___

#### [Twitter Enterprise](https://developer.twitter.com/en/docs/twitter-api/enterprise)

The Twitter enterprise APIs offer the highest level of access and reliability to those who depend on Twitter data. Perfect as you scale beyond premium and need more reliable access, custom tailored packages, or longer-term contracts. Enterprise API access comes with dedicated account managers and personalized technical support.
![image](https://user-images.githubusercontent.com/90479627/152601991-ced1e493-a6d6-4e65-bdf8-f44a5ae287cd.png)

___
### [Keras API](https://keras.io/)

Keras is a deep learning API written in Python, running on top of the machine learning platform TensorFlow. It was developed with a focus on enabling fast experimentation. Being able to go from idea to result as fast as possible is key to doing good research.  

Keras is:
* **Simple** -- but not simplistic. Keras reduces developer cognitive load to free you to focus on the parts of the problem that really matter.
* **Flexible** -- Keras adopts the principle of progressive disclosure of complexity: simple workflows should be quick and easy, while arbitrarily advanced workflows should be possible via a clear path that builds upon what you've already learned.
* **Powerful** -- Keras provides industry-strength performance and scalability: it is used by organizations and companies including NASA, YouTube, or Waymo.

__Keras API reference:__

There are kinds of [APi in Keras](https://keras.io/api/), part of them listed below:

Models API  | Layers API| Callbacks API| Optimizers| Metrics| Built-in small datasets|
--------- | --------| -------| --------| --------| --------|
The Model class  | 	The base Layer class | TensorBoard | 	Adam | 	Accuracy metrics | MNIST digits classification dataset |
The Sequential class  | Core layers | CSVLogger | Adadelta | Probabilistic metrics | IMDB movie review sentiment classification dataset |
Model training APIs  | Recurrent layers | BackupAndRestore | Nadam | Regression metrics | Fashion MNIST dataset, an alternative to MNIST |
Model saving & serialization APIs | Convolution layers | Base Callback class | Ftrl | Image segmentation metrics | Boston Housing price regression dataset |
