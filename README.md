# Unofficial Gab API
So, i was dumping stuff with the app.

Then i found out it had an api, so here's the docs
# Get Token
In the index.html source code, you can find this: 
```html
<input type="hidden" name="_token" value="BorbPurlRF4twmIYTe4IIzrrjTEZ2cKibqtZBF3v">
``` 
so we can find the value with this simple thing :thinking:
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
auth_token = find_between(str(request.text), '<input type="hidden" name="_token" value="', '">')

print("Token:");
print(auth_token);
```
