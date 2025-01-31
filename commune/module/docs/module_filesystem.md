The module filesystem dedicates one folder per module in the ~/.commune storage folder. 

This folder contains all of your files relating to commune, and are stored under the module folder. The module folder is named after the module name, and contains the following files:

For instance, the module folder for the module `model` would be `~/.commune/model`.


Make a new module in commune
```bash

c new_module model

```

put and get functions for json objects

```python

class Model(c.Module):
    def __init__(self, a=1):
        self.a = a
    def call2(self, b = 1):
        return self.a + b

```

```bash
c model/put a 1
{'k': 'a', 'data_size': 28, 'encrypted': False, 'timestamp': 1718133738}
```
To get the value, 

c model/get a 2
1

Max age is the maximum age of the data in seconds. If the data is older than the max age, the data is not returned. 

```bash

c mode/get a default=10 max_age=1 # max_age is in seconds of how old the data can be
```

output

```bash
a is too old (326 > 10)
10
```

Storing in the root module
The root module cli is just no module in c {module}/{function} {args}
So if you want to store a value in the root module, you can do the following

```bash
c put a 1
{'k': 'a', 'data_size': 28, 'encrypted': False, 'timestamp': 1718133738}
```

```bash
c get a 1
1
```
