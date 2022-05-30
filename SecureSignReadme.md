# Secure sign 

### Set parameters
1. Navigate to app and enter on parameters config

![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/593FC2CA-5FD6-4B36-86CA-69F5A89F99BD.jpeg "Logo Title Text 1")


2. Configure the secret key and email parameters
  - SECRET_KEY: Custom key for conection with the api
  - CONFIG_EMAIL_API_KEY: Provided by [Mailgun | email service](https://www.mailgun.com/es/)
  - EMAIL_DOMAIN: Provided by [Mailgun | email service](https://www.mailgun.com/es/)

![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/018AE7D9-A52F-4E5A-A031-05D0FECD18E2.jpeg "Logo Title Text 1")


### Postman requests
---
#### *Example api collection*
[Download postman collection](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/Secure_sign.postman_collection.json)

---

1. Configure the domain host and secret key on the collection variables

![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/CF305859-6D4D-48AB-910B-4E01A953EEDA.jpeg "Logo Title Text 1")

2. Collection contains two request
  - Scan pdf


     Body requires a pdf form document with a key named pdfBytes in multipart form data request
     
     [Download example pdf template](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/template_document.pdf)

     
     ![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/6863CFC0-A954-4554-A76A-48AF6BB2E70C.jpeg "Logo Title Text 1")
     
     
     this request returns a json with the document fields and keys for configuration,
     similar to the following
     
     ```json
    {
    "emailOnSuccess": "",
    "reference": "",
    "clientEmail": "",
    "postOnSuccess": "",
    "pdfUrl": "https://blazing-app-9ghrk.cloud.serverless.com/public/templates/64f30abc-8d44-4e88-a77b-452c1ff0bd3e.pdf",
    "message": "",
    "pdfExampleReference": "https://blazing-app-9ghrk.cloud.serverless.com/public/examples/3f34e499-7625-424f-aa11-d4a4c66e2df3.pdf",
    "fields": {
        "Name": {
            "type": "String",
            "label": "Name",
            "defaultValue": "Name",
            "optional": false,
            "uniforms": {
                "disable": false,
                "readOnly": false,
                "min": 0,
                "max": 99
            },
            "configs": {
                "page": 1,
                "initials": false,
                "name": true
            }
        },
        "Lastname": {
            "type": "String",
            "label": "Lastname",
            "defaultValue": "Lastname",
            "optional": false,
            "uniforms": {
                "disable": false,
                "readOnly": false,
                "min": 0,
                "max": 99
            },
            "configs": {
                "page": 1,
                "initials": false,
                "name": false
            }
        },
        "Initials": {
            "type": "String",
            "label": "Initials",
            "defaultValue": "Initials",
            "optional": false,
            "uniforms": {
                "disable": false,
                "readOnly": false,
                "min": 0,
                "max": 99
            },
            "configs": {
                "page": 1,
                "initials": true,
                "name": false
            }
        },
        "Today Date": {
            "type": "String",
            "label": "Today Date",
            "defaultValue": "2022-05-30",
            "optional": false,
            "uniforms": {
                "type": "date",
                "disable": false,
                "readOnly": false
            },
            "configs": {
                "format": "MM/DD/YYYY"
            }
        },
        "Dropdown1": {
            "type": "String",
            "label": "Dropdown1",
            "defaultValue": "Item Optional",
            "allowedValues": [
                "Item 1",
                "Item 2",
                "Item 3",
                "Item Optional"
            ],
            "uniforms": {
                "disable": false,
                "readOnly": false
            }
        },
        "Check1": {
            "type": "Boolean",
            "label": "Check1",
            "defaultValue": false,
            "uniforms": {
                "disable": false,
                "readOnly": false
            }
        },
        "Check2": {
            "type": "Boolean",
            "label": "Check2",
            "defaultValue": false,
            "uniforms": {
                "disable": false,
                "readOnly": false
            }
        }
    }
    }
    ```

  - emailOnSuccess: 
  - reference:
  - clientEmail:
  - postOnSuccess:
  - message:
  - pdfUrl:   
  - pdfExampleReference: 
  - fields: 



+ Save document
