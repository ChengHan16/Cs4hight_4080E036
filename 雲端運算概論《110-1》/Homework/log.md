
```
from __future__ import division, print_function
# coding=utf-8
import sys
import os
from os import name, path
import glob
import re
import numpy as np

# Keras
from keras.applications.imagenet_utils import preprocess_input, decode_predictions
from keras.models import load_model
from keras.preprocessing import image
from flask_sqlalchemy import SQLAlchemy

# Flask utils
from flask import Flask, redirect, url_for, request, render_template
from werkzeug.utils import secure_filename
#from gevent.pywsgi import WSGIServer
#https://stackoverflow.com/questions/35911252/disable-tensorflow-debugging-information
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '3'
 
# Define a flask app
app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///site.db'
db = SQLAlchemy(app)

class FileContents(db.ModeL)
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(300))
    data = db.Column(db.LargeBinary)

# Model saved with Keras model.save()
MODEL_PATH = 'models/model_vgg19.h5'
# from os import path
print("Model File exists:" + str(path.exists(MODEL_PATH)))

if path.exists(MODEL_PATH):   
    # Load your trained model
    model = load_model(MODEL_PATH)
    model.make_predict_function()          # Necessary
    # print('Model loaded. Start serving...')
else:
    # You can also use pretrained model from Keras
    # Check https://keras.io/applications/
    from keras.applications.vgg19 import VGG19
    model = VGG19(weights='imagenet')
    model.save(MODEL_PATH)
    print('Model loaded. Check http://127.0.0.1:5000/')


def model_predict(img_path, model):
    img = image.load_img(img_path, target_size=(224, 224))

    # Preprocessing the image
    x = image.img_to_array(img)
    # x = np.true_divide(x, 255)
    x = np.expand_dims(x, axis=0)

    # Be careful how your trained model deals with the input
    # otherwise, it won't make correct prediction!
    x = preprocess_input(x, mode='caffe')

    preds = model.predict(x)
    return preds

@app.route('/', methods=['GET'])
def index():
    # Main page
    return render_template('index.html')


@app.route('/predict', methods=['GET', 'POST'])
def upload():
    if request.method == 'POST':
        # Get the file from post request
        f = request.files['file']

        # Save the file to ./uploads
        basepath = os.path.dirname(__file__)
        file_path = os.path.join(
            basepath, 'uploads', secure_filename(f.filename))
        f.save(file_path)

        # Make prediction
        preds = model_predict(file_path, model)

        # Process your result for human
        # pred_class = preds.argmax(axis=-1)            # Simple argmax
        pred_class = decode_predictions(preds, top=1)   # ImageNet Decode
        result = str(pred_class[0][0][1])               # Convert to string
        
        return result
    return None

if __name__ == '__main__':
    app.run(debug=True)
```
