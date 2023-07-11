# Motion Prediction for Autonomous Cars 

## Abstract 

Motion prediction is one of the few outstanding unsolved tasks of autonomous
driving, and is critical to the deployment of safe autonomous vehicles (AV)s
that are able to navigate complex environment. We evaluate a number of deep
learning approaches to motion prediction, and propose a novel combination of a 
convolutional social pooling and BEV convolutions to predict vehicle trajectories.

Link to paper / report: https://github.com/RahulMaganti47/Motion-Prediction-for-Autonomous-Cars/blob/master/MotionPredictionForAutonomousCars_Report.pdf

# Setup 

## AWS Setup

### Assumptions

1. Have a `key.pem` file from AWS in the local directory
1. Have your public IPv4 instance address from AWS console
1. Have a Deep learning AMI instance running

### SSH

````sh
ssh -L 8000:localhost:8000 -i ese650.pem ubuntu@3.85.16.98 
````
If you run into:
````sh
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for 'ese650.pem' are too open.````
````

Simply run:
````sh
sudo chmod 600 /path/to/my/key.pem
````
and try again.

### Setting up Jupyter Notebook

After running the above ssh command:

````sh
source activate pytorch_latest_p37

jupyter notebook --no-browser --port=8888
````

### View Jupyter Notebook

From a seperate shell than the previous one, run

````sh
ssh -i ese650.pem -L 8888:localhost:8888 ubuntu@54.167.21.28
````

Go to your browser and visit: 

````
localhost:8888
````

### Uploading file

````sh
scp -i sheils.pem kaggle.json ubuntu@54.90.44.142:~/ext_vol/kaggle.json
scp -i sheils.pem lyft-ese650finalproj.ipynb ubuntu@54.90.44.142:~/lyft_model.ipynb
````

### Downloading dataset 

````sh
sudo mv ext_vol/kaggle.json .kaggle/
sudo chmod 777 ext_vol
kaggle competitions download -c lyft-motion-prediction-autonomous-vehicles
````

### Unzip

````sh
sudo apt-get install unzip
unzip lyft-motion-prediction-autonomous-vehicles.zip  lyft_dataset
cd ..
sudo du -sh ext_vol/
````

