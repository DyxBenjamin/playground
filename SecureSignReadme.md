# Secure sign 

## Set parameters
1. Navigate to app and enter on parameters config

![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/593FC2CA-5FD6-4B36-86CA-69F5A89F99BD.jpeg "Logo Title Text 1")


2. Configure the secret key and email parameters
  - SECRET_KEY: Custom key for conection with the API
  - CONFIG_EMAIL_API_KEY: Provided by [Mailgun | email service](https://www.mailgun.com/es/)
  - EMAIL_DOMAIN: Provided by [Mailgun | email service](https://www.mailgun.com/es/)

![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/018AE7D9-A52F-4E5A-A031-05D0FECD18E2.jpeg "Logo Title Text 1")


## Postman requests
#### *Example API collection*
[Download postman collection](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/Secure_sign.postman_collection.json)

---

1. Configure the domain host and secret key on the collection variables

![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/CF305859-6D4D-48AB-910B-4E01A953EEDA.jpeg "Logo Title Text 1")

2. Collection contains two request
### Scan pdf
 > https://{{host}}/api/generate

Body requires a pdf form document with a key named pdfBytes in multipart form data request
     
[Download example pdf template](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/template_document.pdf)
    
![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/6863CFC0-A954-4554-A76A-48AF6BB2E70C.jpeg "Logo Title Text 1")
     
This request save the form pdf on serverless storage and returns a json with the document fields and keys for configuration,
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
  
  Each field contains especific parameters for configuration
  
  ```json
          "key": {
            "type": "String",
            "label": "customLabel",
            "defaultValue": "string value",
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
  ```
  
  - type: Automatically generated, can be String, Number or Boolean
  - label: A more descriptive custom label for the form [default = key]
  - defaultValue: A value per default for the form field 
  - optional: Required for field validation [default = false]
  
  **uniforms**
  - disable: Disable the field in the form [default = false]
  - readOnly: Disables the ability to modify the field in the form [default = false]
  - min: Minimum length for the field [default = 0] 
  - max: Maximum length for the field [default = 99]
  
  **config**
  - page: Automatically generated, number of the page that contains the field
  - initials: Tag for initials fields [default = false]
  - name: Tag for name fields [default = false] 

> ### Note
> - Fields Name and Lastname are required, if it's necessary change the display you can use label parameter
> - fields thats includes the word "Initials" automaticaly detects and apply initials config  
> - fields thats includes the word "Name" automaticaly detects and apply name config  
> - fields thats includes the word "Date" automaticaly detects and apply date config  



---
### Save document
> https://{{host}}/api/secure-sign/save

Enpoint to save the data of the document

Body requires a document json previously generated and modified


![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/24152146-4D3F-434A-9AA1-A5F402B3963A.jpeg "Logo Title Text 1")


If the data is correct the request returns a json with the document id, reference, client email and form url, similar to this:


```json
{
    "id": "2457b1e9-0855-4d40-a375-e3d01eaa4ff2",
    "reference": "xxxx-xx-xxxxxx",
    "clientEmail": "example@email.com",
    "url": "https://domain-host/secure-sign/2457b1e9-0855-4d40-a375-e3d01eaa4ff2"
}
```


Accessing the url will send us to the form page

![set parameters](https://blazing-app-9ghrk.cloud.serverless.com/public/doc/20F27426-B5A5-4EEB-9F1A-973B88179F89.jpeg "Logo Title Text 1")



