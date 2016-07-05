# SemanticTransformation
A web based annotation system which enables the transformation of existing, published web content. 


# release 0 instructions

## make the code / doc 
A makefile exists to setup the execution environment. This will setup the build directory with the necessary code and documentation files. The docs are in build/doc directory. The code is present in build/code directory. These two directories are untangled from the literate code that we have used to document this application

```
make clean
make
```

## Setup the Selinium Server
The following steps are needed for setting up the Selenium server. This is needed in the backend to inject the first JavaScript code bookmarklet code (called Annolet for r0, annd Joiner for r1). 

### Configure Selenium 
we need to configuration of the Selenium Server with a secret key and path for the Selenium Chrome Driver. To do this we need to edit the conf.py file in build/code/selenium directory. 
```
cd /build/code/selenium
```
Change secret key in the config file by editing the string inside the conf.py file. You may add any string you like between the two single quotes on the right hand side.
```
vi conf.py
```
Add the full absolute path for the Selenium Chrome Driver. The changed file should look like this:
```
SECRET_KEY = ('mySecretKey',) # some long string
CHROME_DRIVER_PATH = ('/home/workingFolder/src/selenium/chromedriver',) #complete path to chromedriver
```

### Create Virtual Environment
Now we need to create a virtual environment in which we can execute the Selenium code. This is facilitated thru the setup.sh file. Run the file setup.sh by command
```
bash setup.sh
```
Here you will be asked to enter your root password. This is for agt-get command and not for pip install. Packages for virtual environment, Selinium and the application are being installed. This command will take a few minutes to execute.
This should setup a new flask directory for you. This is where the virtual environment exists.

### Activate Virtual Environment
Now you can activate the virtual enviornment by command
```
source ./flask/bin/activate
```

### Run Selenium Server
run the Selinium Server application in the background by command
```
python app.py &
```
When you run the Selenium Server, you should see this prompt on your terminal
```
Running on http://127.0.0.1:8000/ (Press CTRL+C to quit)
```

### To deactivate Server...
After you are done and you no longer need the server, you may choose to deactivate the virtual environment by command
```
deactivate
```


## Setup & execute the server for webservices

### Goto proper directory
In a new terminal, goto web services directory
```
cd /build/code/webservices
```
Note that Selinium Server will have its own virtual environment and this will have its own virtual environment. It is for this reason that we opened a new Terminal window.

### setting up Virtual Environment
we need to create a virtual environment in which we can execute the Web Services code. This is facilitated thru the setup.sh file. Run the file setup.sh by command
```
bash setup.sh
```
Here you will be asked to enter your root password. This is for agt-get command and not for pip install. Packages for virtual environment, Web Services are being installed. This command will take a few minutes to execute.
This should setup a new flask directory for you. This is where the virtual environment exists.

### Activate Virtual Environment
Now you can activate the virtual enviornment by command
```
source ./flask/bin/activate
```

### Run Web Services Server
Run the Web Services server in the background with the command
```
python run.py &
```
When you run the Web Services Server, you should see this prompt on your terminal
```
* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```
Note that the server for Selenium is on port 8000 and web services server is running on port 5000
This command takes a few minutes to run. Delay is due to background initialization of 1000 popular words (which are used for Phonetics Web Service).
The prompt should be something like this
``` 
* Restarting with stat
* Debugger is active!
* Debugger pin code: 327-972-303
```

### To Deactivate...
After you are done and you no longer need the server, you may choose to deactivate the virtual environment by command
```
deactivate
```

## run the application on the browser
open a browser. We recommend Firefox (as Selenium is set to run on it). Chrome, IE browsers require a special driver. This has not been tested yet.
### Browser setup
In the URLbox of the Firefox browser enter
```
127.0.0.1:8000
```
This is the local host addr with the 8000 port for running Selenium

## 


