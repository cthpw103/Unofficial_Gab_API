# Unofficial Gab API
So, i was dumping stuff with the app.

Then i found out it had an api, so here's the docs
# Get Token
In the index.html source code, you can find this: 
```html
<input type="hidden" name="_token" value="BorbPurlRF4twmIYTe4IIzrrjTEZ2cKibqtZBF3v">
``` 
Hmm, so we can find the value with this simple python example :thinking:
```python
import request
import sys

def find_between( s, first, last ):
    try:
        start = s.index( first ) + len( first )
        end = s.index( last, start )
        return s[start:end]
    except ValueError:
        return ""
session = requests.Session()

headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3112.101 Safari/537.36'}
request = session.get("https://gab.ai/auth/login", headers=headers)
token = find_between(str(request.text), '<input type="hidden" name="_token" value="', '">')

print("Token:")
print(token)
```
# Login
After 2 seconds of search, we can see it find it's sending a post request to https://gab.ai/auth/login
```html
<form action="https://gab.ai/auth/login" method="post" class="auth-form">
``` 

So let's add this to the code :smile: 
```python
data = {'username':'api_rocks', 'password':'wordpass123', '_token':token}
r = s.post("https://gab.ai/auth/login", headers=headers, data=data)
print("logged in.")
```
# Register
https://gab.ai/auth/register
It's harder but it's easy
```js
jQuery.ajax({
url: "https://gab.ai/auth/register",
type: "POST",
data: form.serialize(),
dataType: "JSON",
```
>jquery
Works kindof the same
So we can do: 
```python
email
data = {'username':'API Test.','username':'api_rocks','email':'api_rocks@xss.rocks','password':'wordpass123', '_token':token}
r = s.post("https://gab.ai/auth/register", headers=headers, data=data)
print("logged in.")
```
# The End
For now.
https://gab.innocraft.cloud/ :wink:
