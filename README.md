# Flask
***

## What is it?
- Flask is a web application framework written in Python. It has multiple modules that make it easier for a web developer to write applications without having to worry about the details like protocol management, thread management, etc.
- Flask microframework is an easy-to-use microframework that can be used to build RESTful microservices, it is a very popular framework, and it is well documented.
- Essentially, Flask is used to create the web app.
- One of the most popular types of APIs for building microservices applications is known as “RESTful API” or “REST API.” REST API is a popular standard among developers because it uses HTTP commands, which most developers are familiar with.
***

## Flask vs. Django
- Flask is considered more Pythonic than the Django web framework because in common situations the equivalent Flask web application is more explicit.
- Flask is also easy to get started with as a beginner because there is little boilerplate code for getting a simple app up and running.
- **Flask or Django?** There’s no clear winner between Django and Flask, as everything depends on your final goal. Flask and Django both have their strengths and weaknesses. Django is very complete, with regard to ORM, admin interface etc. It’s well documented. But Django has a steep learning curve. Flask might be a better choice because you can learn it fast.
***

## Tools stack
- `Flask` is used for the back-end
- `React` is used for the front-end
- `Heroku` is used for the public server deployment
***

## How to run
- Step #1: run your code containing your flask API call as: `python my_app_name.py`
- Step #2: copy and past in the browser this `http://127.0.0.1:5000/`
***

## Troubleshooting
- If you get an erro like this: `OSError: [Errno 48] Address already in use` then follow this [link](https://ishaileshmishra.medium.com/the-python-flask-problem-socket-error-errno-48-address-already-in-use-4d074847587e) to resolve it. Essentially this appens, when you are the app for the first time, you kill the python thread and while relaunching it again.
- Option #1:
   - Try to locate the PID of the process with: `ps -fA | grep python`
   - Then kill the PID with: `kill PID`
   - If the one above does not work try: `kill -s KILL <pid>` or `kill -9 <pid>`
- Option #2:
   - Locate the PID with: `lsof -i:8050`
   -  Then shut the process with: `kill PID`
***

## Flask and scaling up
- Flask’s built-in server is not suitable for production as it doesn’t scale well. 
- The Flask server is not powerful enough to support production loads. Instead, you should use gunicorn and nginx for proper deployment.
- For some small project is fine but if you want to see how to deploy a Flask application properly see [this](https://flask.palletsprojects.com/en/1.1.x/deploying/)
***

## The Downside of simple model server deployment with a Python-Based APIs
- Most introductions to deploying machine learning models follow roughly the same workflow:
   1. Create a web app with Python (i.e., with web frameworks like Flask or Django).
   2. Create an API endpoint in the web app, as we show in Example 8- 1.
   3. Load the model structure and its weights.
   4. Call the predict method on the loaded model.
   5. Return the prediction results as an HTTP request.

- An example in Flask looks like this:
```
import jason
from flask import Flask, request
from tensorflow.keras.models import load_model
from utils import preprocess

model = load_model("model.h5")
app = Flask(__name__)

@app.route("/classify", methos=["POST"])
def classify():
   data_in = request.from["data"]
   proprocessed_data = preprocess(data_in)
   prediction = model.predict(proprocessed_data)
   return json.dumps({score: prediction})
```

- This setup is a quick and easy implementation, perfect for demonstration projects (an alternative is TensorFlow Serving). However, it is not recommended to deploy machine learning models to production endpoints, because of these 3 main reasons:
   - **Lack of code separation** btw the ML model and the API calls. The lack of code separation also requires that the model has to be loaded in the same programming language as the API code. This mixing of backend and data science code can ultimately prevent your API team from upgrading your API backend. 
   - **Lack of model version control** as there is no provision for different model versions. If you wanted to add a new version, you would have to create a new endpoint (or add some branching logic to the existing endpoint). This requires extra attention to keep all endpoints structurally the same, and it requires a lot of boilerplate code. 
   - **Inefficient model inference** where each request is preprocessed and inferred individually. During the training of your model, you will probably use a batching technique that allows you to compute multiple samples at the same time and then apply the gradient change for your batch to your network’s weights. 
***

## Resources
- [list of resources](https://www.fullstackpython.com/flask.html)
- [Model Deployment using Flask](https://towardsdatascience.com/model-deployment-using-flask-c5dcbb6499c9)
- [How To Build & Deploy a React + Flask](https://towardsdatascience.com/build-deploy-a-react-flask-app-47a89a5d17d9)
- [Flask Django a thorough comparison](https://codesource.io/flask-vs-django-an-in-depth-comparison/)
- Hapke, Hannes, and Catherine Nelson. Building machine learning pipelines. O'Reilly Media, 2020
***
 
