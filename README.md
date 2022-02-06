# Twitter-vs-Keras

[1. Syntax](#syntax)
## Syntax
#### Twitter API
Twitter API are straight forward in syntax, user friendly designed. Most of it's functions are based on create(POST), read(GET), update(PUT), delete(DELETE) actions. This formalized designing strategy helps users to build their own function easily. Also, Twitter API provides user with packaged functions, especially those related to Twitter website. For example, Twitter API has build in functions surpporting information lookup, information management and other list generation.


For example:

- In a Manage Like Function(https://github.com/twitterdev/Twitter-API-v2-sample-code/blob/main/Manage-Likes/like_a_tweet.py)

We use 'Get' to get tokens and keys we need:
![530-1](https://user-images.githubusercontent.com/78243340/152655011-4a866e94-ec49-452d-9742-89c19bc64b57.JPG)
![530-2](https://user-images.githubusercontent.com/78243340/152655024-1356e54e-29dd-447a-a925-512a84dcb12a.JPG)
We use 'Post' to make request:
![530-3](https://user-images.githubusercontent.com/78243340/152655046-9afb6354-6e51-4e1e-befc-7fafd54f2a40.JPG)

- In a Manage Tweet Function(https://github.com/twitterdev/Twitter-API-v2-sample-code/blob/main/Manage-Tweets/delete_tweet.py)


We use 'Delete' to delete our target:
![530-4](https://user-images.githubusercontent.com/78243340/152655171-e5f3814a-5feb-4bac-91f4-2399d7fc0875.JPG)


#### Keras API
Keras API is different from Twitter API in many ways. From a functional insight, Keras is a open source Artificial Neural Network dataset. It has many build in deep learning models.

In this case, the usecases of Keras API are mostly model based:

- model.layers returns a list, the list contains all objects that have been created. For example:'keras.layers.Dense'.
- model.inputs returns a list, this list contains  the type of data received by the input of the model. 
- models.output returns a list, this list contains the type of data recieved by the output of the model.
- models.summary returns the structural information, total parameter quantity and learnable parameters.
- model.get_ config returns a dictionary that contains the structure and compilation information of all objects of the model. Keras can use this information to build a new model.
- model.get_ weights returns a list. Each member in the list is a model weight in the form of numpy array. The order of the list is input to output.
- model.set_ weights (pre_trained_w) specifies all weights of the model. The specified weight must be the same as that of the model get_ Weights returns the same weight size.
- model.to_ yaml outputs the structure of keras model as a yaml file without model weight. After the output is completed, the keras model can be imported from the yaml file.
- model.save_ weights (filepath) saves the weight of keras model as HDF5 file, and specifies the file path filepath at runtime.
- model.load_ weights (filepath, by_name = false) export the weights to the model from the HDF5 file. model. load_ Weights usually only accept model save_ For the files output by weights, you need to specify by when receiving files from other sources_ Name = true, and the variable name of HDF5 is required to be the same as the name of the model layer object.


There are are several helpful build in models:

- keras.models.Sequential: 


  - Sequential model is a neural network model obtained by stacking its API middle-level objects.
  - Sequential model can be defined in two ways. One is to run keras models. In sequential, all layer objects are specified by the list. The other is to use model for the sequential class instead of specifying the layer API at runtime Add add layer object.
  - Example of method 1:
  ![530-5](https://user-images.githubusercontent.com/78243340/152656546-74357667-13dd-43ad-8254-f6412ae26613.JPG)
  - Example of method 2:
  ![530-6](https://user-images.githubusercontent.com/78243340/152656556-d9ea4f3d-fd1b-4486-9b13-17beed461d89.JPG)


- keras.models.Model:
 
 - Keras's functional model is also called functional API. Its function is to specify one tensor as input and the other tensor as output, and combine the nodes (layer objects) connected with the input and output tensors into a neural network model.
 - Example of initialization:
 ![530-7](https://user-images.githubusercontent.com/78243340/152656669-f41e9661-238e-4a0d-8b38-0e17a727dfb4.JPG)


The use of models:


Two steps are needed when using Keras models, the first step is compiling, the second step is learning:

- model.compile:

  - The compile of Keras model is based on model.compile, The runtime can translate the keras code into background code to perform subsequent operations such as learning and evaluation. The compilation can specify the learning component, and its use format is as follows:
  ![530-8](https://user-images.githubusercontent.com/78243340/152656837-d8539df2-43fd-41d7-bb7a-71a380204de2.JPG)

  - the meaning of components are below:
    - Optimizer is the optimizer, loss is the loss function, and metrics is the evaluation function. Multiple evaluations can be used by list.
    - loss_ weights is the loss weight. Different weight coefficients can be superimposed on the losses corresponding to different outputs in the multi output model. It is required to provide the list or tensor corresponding to the model loss.
    - sample_ weight_ Mode is the parameter for sample weighting. The default is none, which means in model One dimensional weighting in fit; When compiling the time series model, you can select sample_ weight_ Mode = "temporary", at this time, the model gives two-dimensional weight to the time series samples (according to time steps).
    - weighted_ The usage of metrics is the same as that of metrics. When sample weighting is not specified, it is equivalent to metrics. When sample weighting is specified, the learning of weighted samples will be evaluated.
    - target_ Tensor: a parameter rarely used. Keras in the background of tensorflow assigns a tensor placeholder for the learning goal by default, but the user can call this parameter to explicitly specify the tensor of the learning goal.


- model.fit and model.fit_generator:
  - After the model is compiled, you can use model Fit or model fit_ Generator for learning, and its use format is as follows:
  ![530-9](https://user-images.githubusercontent.com/78243340/152656981-f8b7c68c-c810-46b2-83be-f3591a021309.JPG)

    - the meaning of components are below:
      - verbose means to display the progress bar and current evaluation results during learning. It is on by default.
      - callback is the feedback option (see "feedback").
      - epochs is the number of learning periods, that is, the number of iterations for all learning samples.
      - initial_epoch indicates the number of epochs at the beginning of learning. If the previous learning weight is not loaded, it defaults to 0.
      - class_ weight is a parameter for category weighting in classification problems, that is, different weights are used for learning objectives of different classifications. calss_ The input of weight is a dictionary, the variable name is class alias, and the content is weight. For example, for binary classification, the class names are usually "0" and "1".
   - the components for model.fit are below:
      - X represents the input feature, Y represents the learning goal, and batch_ Size indicates the number of samples in a single batch during batch learning. steps_ per_ Epoch indicates the number of batches participating in learning. The default value of none indicates the maximum number of batches allowed by dividing the total number of samples by the number of samples in a single batch.
      - validation_ split represents the proportion of the sample used for model validation. This part of the data will be randomly selected in proportion and will not participate in learning.
      - validation_ data receives a python tuple containing or (x, y) or (x, y, sample_weight) for verification during learning.
      - validation_ freq only calls validation_ Split or validation_ Data is used to indicate the frequency of model verification. The default value is 1, indicating that verification is carried out in each era. validation_ Freq also receives the list. The elements in the list represent the number of epochs for model verification. For example, [1, 5, 10] represents model verification in the 1st, 5th and 10th epochs.
      - validation_ steps only when steps is called_ per_ Used after epoch to indicate the number of batches participating in model validation.
      - Shuffle is a shuffle option for data, which is only available when steps is called_ per_ Used when epoch = none. The default value is true, which indicates complete shuffling. In addition, false and batch are also available, which indicates shuffling in only one batch of samples.
      - sample_ weight is a parameter that weights the sample, usually not the category weighted parameter calss_ Called together with weight. In model Define sample in compile_ weight_ when mode = none, sample_ Weight receives a 1-dimensional numpy array with the same size as the total number of samples; Define sample in_ weight_ When mode = "temporary", calss_ weight receives a two-dimensional array, which represents the weight of each sample in different time steps by line, that is, the array size is (sample, timestep).
    - the components for model.fit_generator are below:
      - Generator refers to the generator (see "general tools"), which returns the input features, learning objectives and sample weights. If the sample weights are not returned, the default is equal weights.
      - steps_ per_ Epoch has the same meaning as model The same as fit, but the default is the generator's internal method__ len__ The return value of (self).
      - validation_ Data has the same meaning as model A generator that receives the same input but also validation data.
      - validation_ Step is only used in validation_ Data is used when receiving the generator, indicating the number of batches participating in model validation.
      - validation_ Freq only calls validation_ Data is valid, indicating the frequency of model verification. The use method is the same as model Same as fit.
      - max_ queue_ Size receives an integer indicating the maximum number of queues for the generator.
      - use_ Multiprocessing defaults to false, indicating that thread based processes are not used. When the computing system has multithreading capability and the generator supports Python's multithreaded processing framework, that is, it supports pickle operation, you can select true.
      - Workers refers to the number of working threads. The default value is 0, which means that it only runs on the main thread and in use_ When multiprocessing = true, an integer greater than 0 is optional.


After learning process, we can step in to evaluating(model.evaluate,model.evaluate_generator) and testing process(model.predict,model.predict_generator,model.predict_on_batch):


- model.compile:
  ![530-10](https://user-images.githubusercontent.com/78243340/152657487-670069af-7a55-4284-bc43-171de92f2e89.JPG)

- model.predict,model.predict_generator,model.predict_on_batch:

  ![530-11](https://user-images.githubusercontent.com/78243340/152657492-737393be-db5c-4d96-849f-a59191db80c8.JPG)

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
Typically, there are 4 steps involved in working with this endpoint:
- Create a compliance job  
  - You can specify the job type (with the value tweets or users to indicate whether the dataset you want to upload has Tweet IDs or user IDs. You can have one concurrent job per job type at any time.
- Upload your dataset to the upload_url. 
  - Next, you upload your dataset as a plain text file to the provided upload_url, with each line of the file containing a single Tweet ID or user ID. The upload_url expires after 15 minutes.
- Check the job status  
  - You can check the status of your compliance job to see whether it is created, in_progress, failed or complete.
- Download the results  
  - When your job is complete, you can download the results using the download_url. The download_url expires after one week (from when the job was created).  
  - This result will contain a set of JSON objects (one object per line). Each object will contain a Tweet ID, the Tweet’s creation date (useful to locate Tweets organized by date), required action, the reason for the compliance action, and its date.

#### Keras API
An important feature of Keras is callbacks, configured in fit(). Callbacks are objects that get called by the model at different point during training, in particular:  
  At the beginning and end of each batch  
  At the beginning and end of each epoch  
  Callbacks are a way to make model trainable entirely scriptable.  
You can use callbacks to periodically save your model. Here's a simple example: a ModelCheckpoint callback configured to save the model at the end of every epoch. The filename will include the current epoch.  
```
callbacks = [
    keras.callbacks.ModelCheckpoint(
        filepath='path/to/my/model_{epoch}',
        save_freq='epoch')
]
model.fit(dataset, epochs=2, callbacks=callbacks)
```
You can also use callbacks to do things like periodically changing the learning of your optimizer, streaming metrics to a Slack bot, sending yourself an email notification when training is complete, etc.  
https://keras.io/guides/writing_your_own_callbacks/  
An example:  
```
Starting training; got log keys: []
Start epoch 0 of training; got log keys: []
...Training: start of batch 0; got log keys: []
...Training: end of batch 0; got log keys: ['loss', 'mean_absolute_error']
...Training: start of batch 1; got log keys: []
...Training: end of batch 1; got log keys: ['loss', 'mean_absolute_error']
...Training: start of batch 2; got log keys: []
...Training: end of batch 2; got log keys: ['loss', 'mean_absolute_error']
...Training: start of batch 3; got log keys: []
...Training: end of batch 3; got log keys: ['loss', 'mean_absolute_error']
```

## Documentation
### Home Directory
Twitter API Documentation is mainly divided into several parts,   
```
- Getting started
- Fundamentals
- Tools and libraries
- Tutorials
- API reference index
```

And for Keras API,  
```
- About Keras
- Getting started
- Developer guides
- Keras API reference
- Code examples
- Why choose Keras?
- Community & governance
- Contributing to Keras
- KerasTuner
```

Documention for Twitter API has a more concise distinction. And both of them pay attention to quick introduce for usage (Getting started), specific usage for developers (Fundamentals/ Tools and libraries/ Developer guides), detail tutorials and examples (Tutorials/ Code examples), as well as reference list (API reference index/ Keras API reference). 

Reference part is more like detailed listing for different products， which can help us quickly get what we need.

### Reference
Twitter API reference index part introduces its products by different versions. 
```
- Twitter API v2
- Twitter API: Enterprise
- Twitter API: Premium v1.1
- Twitter API: Standard v1.1
- Twitter Ads API
- Authentication and utilities
```
Different versions or products used for different clients. For instance, Enterprise version especially created for companies, standard version mostly used for the masses and Ads API applied to advertizers. This kind of classification could benefitial for users to find what they need as soon as possible. 

For each version, documentation also lists quick links of the processing for tweets, accounts, messages, media, trends and etc. Easy way to get usage scenarios and code examples.

On the other hand, we can also find Keras API would like to list reference for all kinds of classes for different functions. Classes shown as following,  

```
- Models API
- Layers API
- Callbacks API
- Optimizers
- Metrics
- Losses
- Data loading
- Built-in small datasets
- Keras Applications
- Mixed precision
- Utilities
- KerasTuner
```
For example, Model API used for creating models. Layers API mainly for building blocks of neural networks. And Optimizers required for compiling a Keras model.   

Unlike Twitter API reference, Keras API does not have to distinguish several versions for defferent user groups. So they pay more attention on listing their classes which all included in one product.


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
