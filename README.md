</br>
</br>
<p align="center"> 
    <img height="450" src="https://github.com/rivo2302/Mvola/blob/master/assets/icon.png">
</p>

<div align="center"> 
<p>
  A <b>light</b> Python module for quickly configure your <a href="https://www.mvola.mg/devportal/"> API Mvola</a>.
  <h4>
        <a href="https://pypi.org/project/mvola/">Documentation</a>
        <span> | </span>
        <a href="https://github.com/rivo2302/Mvola/issues">Report bugs</a>
        <span> | </span>
        <a href="https://github.com/rivo2302/Mvola/fork">Contribute</a>
 </h4>
</p>
<p>
    <a href='#'> 
         <a href='#'> <img src='https://img.shields.io/badge/Maintained-Yes-darkgreen?style=for-the-badge'/></a>
    </a>
    <a href='https://pypi.org/project/mvola/'> 
       <img src="https://img.shields.io/badge/-opensource-F9F63C?style=for-the-badge&logo=appveyor&logoColor=FFFFFF"/>
    </a>
    <a href='https://github.com/rivo2302/Mvola'> 
        <img src="https://img.shields.io/badge/-python-396E9B?style=for-the-badge&logo=python&logoColor=FFFFFF"/>
    </a>
        <a href='https://pypi.org/project/mvola/'> <img src='https://img.shields.io/pypi/v/mvola?style=for-the-badge'/></a>
    </p>
</div>

## Installation

You can consult the link on pypi.org <a href="https://pypi.org/project/mvola/"> Click here</a>.

```s
pip install mvola==1.0.0
```


## Usage 
> Check the demo file<a href="https://github.com/rivo2302/Mvola/blob/master/demo.py"> here</a>


#### Start the API 
Create your account <a href="https://www.mvola.mg/devportal/">here</a>.
After your create application , you should have Consummer_key and Consummer_secret.

```python
# Import the module mvola
from mvola import API

# Initiate the api => API(Consummer_key, Consummer_secret)
api = API("{consummer_key}","{consummer_secret}")

```

#### Generate token
Check the documentation <a href="https://www.mvola.mg/devportal/apis/5fb6b560-ef7e-49ad-b3c7-5335b7ca45f6/documents/89b6b1d0-b3c9-4758-a548-47889825bc68"> here</a>


```python
res = api.generate_token()
if res.success :
    api.token = res
    print(res)
else :
    print(f"Status_code[{res.status_code}] \n {res.error}")
```

###### OUTPUT
> Success
```s
eyJ4NXQiOiJPRE5tWkRFMll6UTRNVEkxTVRZME1tSmhaR00yTUdWa1lUZGhOall5TWpnM01XTmpNalJqWWpnMll6bGpNRGRsWWpZd05ERmhZVGd6WkRoa1lUVm1OZyIsImtpZCI6Ik9ETm1aREUyWXpRNE1USTFNVFkwTW1KaFpHTTJNR1ZrWVRkaE5qWXlNamczTVdOak1qUmpZamcyWXpsak1EZGxZall3TkRGaFlUZ3paRGhrWVRWbU5nX1JTMjU2IiwiYWxnIjoiUlMyNTYifQ.eyJzdWIiOiJyaXZvMjMwMkBnbWFpbC5jb21AY2FyYm9uLnN1cGVyIiwiYXV0IjoiQVBQTElDQVRJT04iLCJhdWQiOiIwekw3ZVRyU0VmWGY2a2t3SjUzRFNlZ0NiQndhIiwibmJmIjoxNjUxNzk1NTUyLCJhenAiOiIwekw3ZVRyU0VmWGY2a2t3SjUzRFNlZ0NiQndhIiwic2NvcGUiOiJFWFRfSU5UX01WT0xBX1NDT1BFIiwiaXNzIjoiaHR0cHM6XC9cL2FwaW0ucHJlcC50ZWxtYS5tZzo5NDQzXC9vYXV0aDJcL3Rva2VuIiwiZXhwIjoxNjUxNzk5MTUyLCJpYXQiOjE2NTE3OTU1NTIsImp0aSI6IjFjNWEwNDY3LTk5NWMtNDFiNi05M2I2LWJjNzY2YTA0ZDdiZCJ9.PCijTounfH2y2-LNaRaKQleYFEV-voBb0ES-ayYRSG8NyT8GVt6BOXWFdPh4V7MNN5ArBtErVifx5MastxKRqE1-rYnekt51iynCXknEPM3hxjFepOPHPR3rIDtRrNJ0raa0oEkVcHjn6Gl9wUiai-4zepwFaR7GP3xAr6Rz42szCQo4AjDiuJkGMNEhQqgL17AYpjOHE8mXf_Jeth7VpcgUTXDwRRNAGhCzUEHqwQpW-7TPryeTHFzj8HPySy3RWBI5bUjYfVoXWL_yg__RxM0YlPX7JE3ycs75yANbWyQ4WdSc3vZhPCkKusERajxlQCIwBxmVUmALp9YRn0wjfg

```

> Failed (example)
```s
Status_code[401] 
{'error_description': 'A valid OAuth client could not be found for client_id: 0zL7eTrSEfXf6kwJ53DSegCbBwa', 'error': 'invalid_client'}
```
The token generated by this function must expire after 3600s by default, to manage app  go to the dashboard of Mvola API Application.

#### Generate token
Check the documentation <a href="https://www.mvola.mg/devportal/apis/5fb6b560-ef7e-49ad-b3c7-5335b7ca45f6/documents/b36ca2a3-f339-43a1-88d3-bbee6c77b06f"> here</a>

```python
from mvola.tools import Transaction

transaction = Transaction(
    token="{{token}}" #[Token] Requiered fields,
    UserLanguage="FR", # MG or FR
    UserAccountIdentifier="0343500003" #[UserAccountIdentifier] Requiered fields ,
    partnerName="Marketbot" #Name of your application,
    amount="1500",
    currency="Ar" # Possible Values : Ar only,
    descriptionText="Unedescription" #String(len<50Characters)without special character. ,
    requestDate="2022-05-06T02:14:59.567Z",
    debit="0343500003" #[Debit] Required fields | Phone number of subscriber .In preprod it’s fixed: 034350003 or 0343500004,
    credit="0343500004" #[Credit] Required fields | Phone number of merchant. In preprod it’s fixed: 034350003 or 0343500004
)

#The function to init the transaction
init = api.init_transaction(transaction.headers,transaction.dataJson)

if init.success :
    print(init.value)
else :
    print(f"Status_code [{init.status_code}] \n {init.error}")
```
###### OUTPUT
> Success :
```s
{'status': 'pending', 'serverCorrelationId': '6f10a6a4-9daf-4d37-b373-80cab3bed1e7', 'notificationMethod': 'polling'}
```

> Failed (example):
```s
Status_code:[401] 
{'fault': {'code': 900901, 'message': 'Invalid Credentials', 'description': 'Invalid Credentials. Make sure you have given the correct access token'}}
```

## How contribute

- Make a fork of the repository
- Clone the repos 
- TODO List 
- Create a Pull Request 

## Contributors

![Image des contributeurs GitHub](https://contrib.rocks/image?repo=rivo2302/Mvola)
