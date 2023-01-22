# Azure Cognitive Services

[Azure Cognitive Services](https://azure.microsoft.com/en-us/products/cognitive-services/?&ef_id=EAIaIQobChMIibaT94_c_AIVibfICh3MbQMlEAAYASAAEgIcDPD_BwE:G:s&OCID=AIDcmm5edswduu_SEM_EAIaIQobChMIibaT94_c_AIVibfICh3MbQMlEAAYASAAEgIcDPD_BwE:G:s&gclid=EAIaIQobChMIibaT94_c_AIVibfICh3MbQMlEAAYASAAEgIcDPD_BwE) are cloud-based artificial intelligence (AI) services that help developers build cognitive intelligence into applications without having direct AI or data science skills or knowledge. They are available through REST APIs and client library SDKs in popular development languages. Azure Cognitive Services enables developers to easily add cognitive features into their applications with cognitive solutions that can see, hear, speak, and analyze.


## Pre-requisites

You need an Azure Account, if you don't have one, you can create a free student account with up to $200 a year credit, tons of free stuff for more go [here](https://azure.microsoft.com/en-us/free/students/)

> Make sure to use your school email address to get the student credit.

## Create Azure Resources

You need to create an Azure Translator Resource, to do this follow [instructions on this page](https://learn.microsoft.com/en-us/azure/cognitive-services/translator/how-to-create-translator-resource)

> Be sure to create the resource on the East US region, this is the closest region to you.

Once the resource is create, navigate to your new Translator service and click on "Keys and Enpoint"

Click on show keys and copy the value of one your keys into a notepad or any other text editor, you will need this next

## Introduction to APIs

Before we jump into translating text, let's go over some programming principles you will need to translate text.

You can access Azure Cognitive Services using API's provided by the service. Why? so you can integrate this functionality into existing systems like bots, user interfaces, your phone and so on an on.

[Application programming interface (API)](https://en.wikipedia.org/wiki/API) is a way for two or more computers to communicate with each other.

### Usage

APIs are generally used to create libraries and frameworks. The API describes and prescribes the specifications while the library is an implementation of the excution rules.

For example, email APIs require the following minimum fields: to, from, subject, message.

The send command for the email API takes the information in, communicates with the server, authenticates the user and parses the content submitted and sends the email. The command will then return a status indicating success or failure.

### API Components

APIs have basic components that need to be used:

|Component        | Description      |
|:----------------|:-----------------
|URL or EndPoint| Who are you talking to|
|HTTP Protocal| How are you communicating - GET, POST|
|Headers| Meta-data associated with an API request and response|
|Parameters| Options that can be passed with the URL to influence the response|
|Body| Data for execution|

With this components, you can post an HTTP request and the request will provide an [HTTP response](https://www.geeksforgeeks.org/state-the-core-components-of-an-http-response/) with 3 components:

- Status Line
- Header
- Body (optional)

### URL

[Universal Resource Locators](https://en.wikipedia.org/wiki/URL) are web pages. Technically, a URL is a reference to a web resource that specifies its location on a computer network and a mechanism for retrieving it.

### HTTP Protocol

URLs communicate back and forth to the server hosting them using [HTTP protocol](https://www.w3schools.com/tags/ref_httpmethods.asp) (Hypertext Transfer Protocol)

This protocol is designed to communicate between web pages and the hosting server and it uses number of methods to receive and send information.

The most used HTTP methods are GET and POST:

- GET is used to request data from a specific resource
- POST is used to send data to a server to create/update a resource

## Code to translate

Replace value of Ocp-Apim-Subscription-Key with the value of the Translator Key you just created above, copy the code to your replit account and run it.

> If you don't create an azure subscription, use the key provided in class, it wil be valid for 7 days.

``` python

import requests
import json

url = "https://api.cognitive.microsofttranslator.com/translate"

payload = json.dumps([
  {
    "Text": "I want to drive your car many times around the block"
  }
])
headers = {
  'Content-Type': 'application/json',
  'Ocp-Apim-Subscription-Key': 'xxxxxxxxxxxxxxxxxxxxxx',
  'Ocp-Apim-Subscription-Region': 'eastus'
}

params = {
    'api-version': '3.0',
    'from': 'en',
    'to': ['fr', 'zu']
}


response = requests.request("POST", url, params=params, headers=headers, data=payload)

print(response.text)


```

## Want to learn more about AI and Cognitive Services?

Check this [Hands on AI Labs](https://aidemos.microsoft.com/) demos and code to learn more.
