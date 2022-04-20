# fast_api_intro
An intro to fastapi making a basic CRUD app for a users database

## Steps
### set up the virtual environment
in the root folder run the following script in the terminal to make a virtual environment

```
python3 -m venv venv
```

this will create a venv folder in your root folder. To access the virtual environment on a mac run the script:

```
source venv/bin/activate
```

once inside the virtual environment you can download the fastapi packages with the script:

```
pip install "fastapi[all]"
```

this will download all the packages you'll need for your project

### creating api routes
in the main.py file you import fastapi and then create a demo route by typing this:

```
from fastapi import Fastapi

app = Fastapi()

@app.get("/")
async def root:
  return {"message":"Hello World"}
```

the route uses the decorator for the type of route method and the path. the function will enable you to provide logic to perform the 
activity for that route. this is the same for all route methods and paths. for the get, post, put and delete methods you might need to use a parameter
in the path. you can do that using the {parameter} syntax then using the same name as a parameter for the function.

```
@app.get("/post/{post_id}")
async def get_post(post_id: int):
  #logic to get data from db
  return db data
  
  
@app.post("/post/create")
async def create_post(post: Post):
  # save data to the db
  return post that was saved
```

if you want to convert the payload data to a python dictionary then just do post.dict() and then it will be that data type in your function.

### set up schema or modal for the db and structure of data
using pydantic you can set up the schema, modal with the types. you can import this package then make the schema

```
from pydantic import BaseModel
from typing import Optional


class Post(BaseModel):
    title: str
    content: str
    published: bool = True
    rating: Optional[int] = None
```

optional fields can be done making a default value as shown with the boolean value. this can be for any other data type as well. the other way to do 
this is to use the Optional package from typing.
