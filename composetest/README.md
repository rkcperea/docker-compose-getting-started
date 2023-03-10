#### copied at Time.at(1678461233) from [Docker Compose Getting Started Docs](https://stackoverflow.com/questions/2871402/ruby-rails-convert-int-to-time-or-get-time-from-integer#step-1-define-the-application-dependencies) 
# Step 1: Define the application dependencies
Create a directory for the project:
```bash
 mkdir composetest
 cd composetest
 ```
Create a file called app.py in your project directory and paste the following code in:
[`app.py`](app.py)

```python
import time

import redis
from flask import Flask

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)

def get_hit_count():
    retries = 5
    while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError as exc:
            if retries == 0:
                raise exc
            retries -= 1
            time.sleep(0.5)

@app.route('/')
def hello():
    count = get_hit_count()
    return 'Hello World! I have been seen {} times.\n'.format(count)
```

In this example, redis is the hostname of the redis container on the application’s network. We use the default port for Redis, 6379.

Handling transient errors

Note the way the get_hit_count function is written. This basic retry loop lets us attempt our request multiple times if the redis service is not available. This is useful at startup while the application comes online, but also makes the application more resilient if the Redis service needs to be restarted anytime during the app’s lifetime. In a cluster, this also helps handling momentary connection drops between nodes.

Create another file called requirements.txt in your project directory and paste the following code in:

`requirements.txt`
```
flask
redis
```
