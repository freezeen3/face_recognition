# Face Recognition Authenticated Data Fetching System
## Credits
<ul>
  <li>Chan Yu Yan, Sam </li>
  <li>Kwan Man Hei, Andy </li>
  <li>Srivastava Dhruv </li>
  <li>Tamanna Singhal </li>
  <li>Oshi Garg </li>
</ul>

## Execution Instructions

### Step 1: Database Import

Run the `facerecognition.sql` file. This will create a new database `comp3278gr6`, with some dummy data for the application.

### Step 2: Environment Set Up

Create virtual environment using Anaconda with the help of the `requirements.txt` file provided (make 3.x the latest stable Python version).
```
conda create -n face python=3.x
conda activate face
pip install -r requirements.txt
```
Activate the environment once ready.

### Step 3: Set up face recognition

#### Step 3.1: Face Data Collection
Run the `face_capture.py` script to capture images for the user. As the dummy data already has entries for customers, please train the model according to the order in which the customers are present in the table by changing the value of the `user_name` variable to the names appearing in the customer table (the first name has already been added in the script). Before running the script, please ensure that a directory named `data` is present (the script may cause errors if the directory is not present).
```
"""
user_name = "Dhruv"   # the name
NUM_IMGS = 400       # the number of saved images
"""
python face_capture.py
```
#### Step 3.2: Train the Model
Run the `train.py` script to train the model.
```
python train.py
```
`train.yml` and `labels.pickle` will be created at the current folder.

### Step 4: Connect Script to the Database
Before running the `DF_App.py` script, please connect the script with the database by changing `user` and `passwd` values as follows (where `xxxxx` is the password of the user's root):
```
# create database connection
myconn = mysql.connector.connect(host="localhost", user="root", passwd="xxxxx", database="comp3278gr6")
```
### Step 5: Run the Application
Run the `DF_App.py` script to run the application (it may take some time to start). Please refer to the demo video on how to use the application.
```
python DF_App.py
```
