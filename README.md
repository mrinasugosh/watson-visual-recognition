# IBM Watson Studio Visual Recognition Workshop

Build and train AI & machine learning models, prepare and analyze data – all in a flexible, hybrid cloud environment

### What is IBM Watson Studio?
Analyze data using RStudio, Jupyter, and Python in a configured, collaborative environment that includes IBM value-adds, such as managed Spark. IBM Watson Studio offers all this functionality, including:
  - a single workspace for your tools
  - a searchable, growing community
  - shareable, collaborative projects
  - supporting content, where you need it
  

### What is Watson Studio: Visual Recognition Essentials?

The IBM Watson Visual Recognition service uses deep learning algorithms to analyze images for scenes, objects, faces, and other content. IBM Watson Studio provides a collaborative environment in the cloud where you can work with your images and your Visual Recognition custom models.

Product Link: https://www.ibm.com/cloud/watson-studio


## Getting Started

You're just a few steps away from getting started with IBM Watson™.

### Getting a free IBM Cloud account
Create an account on IBM Cloud to try Watson services for free with no time restrictions: [Sign up for free](https://cloud.ibm.com/registration/?target=%2Fdeveloper%2Fwatson%2Fdashboard). You'll receive an email to confirm and activate your account.

### Watson Studio Visual Recognition Service
After you activate your account and log in, click [Browse Services](https://cloud.ibm.com/developer/watson/services) from the Watson console.
Select the  Watson Visual Recognition Service.
Create an instance of the service for free.

#### Before you begin
* Create an instance of the service:
1. Go to the Visual Recognition page in the catalog.
2. Sign up for a free IBM Cloud account or log in.
3. Click Create.

* Copy the credentials to authenticate to your service instance:
1. On the Manage page, click Show Credentials.
2. Copy the API Key and URL values.
3. Make sure that you have the curl command.

* Test whether curl is installed
    -  Run the following command on the command line. If the output lists the curl version with SSL support, then you should be all set:
    ```
    $ curl -V
    ```
    - If necessary, install a version with SSL enabled from [curl.haxx.se](curl.haxx.se). Add the location of the file to your PATH environment variables if you want to run curl from any command-line location.

* NOTE: IBM Cloud Dedicated plans authenticate by using -u "{username}:{password}". Use the username and password values for your specific instance.

### Demo 1: Classify an image
* We are going to classify the following image using a general pre-trained General Model by IBM.

![alt text](https://tinyurl.com/vory3jd)

To classify the image above. Run the following command and replace {apikey} and {url} with the service credentials from earlier. Also, replace {img_url} with the url of the image above(`https://tinyurl.com/vory3jd`):
```
$ curl -u "apikey:{apikey}" "{url}/v3/classify?url={img_url}&version=2019-12-10"
```
Response:
```
{
    "images": [
        {
            "classifiers": [
                {
                    "classifier_id": "default",
                    "name": "default",
                    "classes": [
                        {
                            "class": "retriever dog",
                            "score": 0.969,
                            "type_hierarchy": "/animal/domestic animal/dog/retriever dog"
                        },
                        {
                            "class": "dog",
                            "score": 0.982
                        },
                        {
                            "class": "domestic animal",
                            "score": 0.982
                        },
                        {
                            "class": "animal",
                            "score": 0.982
                        },
                        {
                            "class": "golden retriever dog",
                            "score": 0.856,
                            "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                        },
                        {
                            "class": "sporting dog",
                            "score": 0.5,
                            "type_hierarchy": "/animal/domestic animal/dog/sporting dog"
                        },
                        {
                            "class": "light brown color",
                            "score": 0.995
                        }
                    ]
                }
            ],
            "source_url": "https://tinyurl.com/vory3jd",
        }
    ],
    "images_processed": 1,
    "custom_classes": 0
}
```
#### [API Reference](https://cloud.ibm.com/apidocs/visual-recognition/visual-recognition-v3)


### Demo 2: Classify an image with a Food Model

* Watson Visual Recognition Studio includes a built-in Food model that might be more accurate for your images with food items.

![alt text](https://tinyurl.com/wvph7pd)

* Using a similar command prompt issue a call to classify this image against the Food model:
```
$ curl -u "apikey:{apikey}" -F "classifier_ids=food" "{url}/v3/classify?url={img_url}&version=2019-12-10"
```

Response:
```
{
    "images": [
        {
            "classifiers": [
                {
                    "classifier_id": "food",
                    "name": "food",
                    "classes": [
                        {
                            "class": "grape",
                            "score": 0.665,
                            "type_hierarchy": "/fruit/grape"
                        },
                        {
                            "class": "fruit",
                            "score": 0.873
                        },
                        {
                            "class": "simple fruit",
                            "score": 0.5,
                            "type_hierarchy": "/fruit/berry/simple fruit"
                        },
                        {
                            "class": "berry",
                            "score": 0.538
                        }
                    ]
                }
            ],
            "source_url": "https://tinyurl.com/wvph7pd",
        }
    ],
    "images_processed": 1,
    "custom_classes": 0
}
```
#### [API Reference](https://cloud.ibm.com/apidocs/visual-recognition/visual-recognition-v3)


### Live Demo: Custom Model on Watson Visual Service UI


