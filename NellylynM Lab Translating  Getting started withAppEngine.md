#LAB Google Cloud Fundamentals: Getting Started with App Engine

# Objectives

1 In this lab, you learn how to perform the following tasks:
2 Initialize App Engine.
3 Preview an App Engine application running locally in Cloud Shell.
4 Deploy an App Engine application, so that others can reach it.
5 Disable an App Engine application, when you no longer want it to be visible.

#step1 the command ($ gcloud auth list)give output of an active accont name 

nellylynn_moyo@cloudshell:~ (focal-caster-289121)$ gcloud auth list
#Results 
     Credentialed Accounts
ACTIVE  ACCOUNT
*       nellylynn.moyo@gmail.com
To set the active account, run:
    $ gcloud config set account `ACCOUNT`
nellylynn_moyo@cloudshell:~ (focal-caster-289121)$

	
#step 2this command will ($ gcloud config list project) will list the project ID 

nellylynn_moyo@cloudshell:~ (focal-caster-289121)$ gcloud config list project

# results 
[core]
project = focal-caster-289121
Your active configuration is: [cloudshell-4104]
nellylynn_moyo@cloudshell:~ (focal-caster-289121)$

#step 3 this command ($gcloud app create --project=$DEVSHELL_PROJECT_ID )will initialise a project then it prompt theuser to choose a region you have to select a number next to the region of your choice  you get a message to say if the deployment was a success 

nellylynn_moyo@cloudshell:~ (focal-caster-289121)$ gcloud app create --project=$DEVSHELL_PROJECT_ID
#Results 

You are creating an app for project [focal-caster-289121].
WARNING: Creating an App Engine application for a project is irreversible and the region
cannot be changed. More information about regions is at
<https://cloud.google.com/appengine/docs/locations>.
Please choose the region where you want your App Engine application
located:
 [1] asia-east2    (supports standard and flexible)
 [2] asia-northeast1 (supports standard and flexible)
 [3] asia-northeast2 (supports standard and flexible)
 [4] asia-northeast3 (supports standard and flexible)
 [5] asia-south1   (supports standard and flexible)
 [6] asia-southeast2 (supports standard and flexible)
 [7] australia-southeast1 (supports standard and flexible)
 [8] europe-west   (supports standard and flexible)
  [9] europe-west2  (supports standard and flexible)
 [10] europe-west3  (supports standard and flexible)
 [11] europe-west6  (supports standard and flexible)
 [12] northamerica-northeast1 (supports standard and flexible)
 [13] southamerica-east1 (supports standard and flexible)
 [14] us-central    (supports standard and flexible)
 [15] us-east1      (supports standard and flexible)
 [16] us-east4      (supports standard and flexible)
 [17] us-west2      (supports standard and flexible)
 [18] us-west3      (supports standard and flexible)
 [19] us-west4      (supports standard and flexible)
 [20] cancel
Please enter your numeric choice: 4

Creating App Engine application in project [(focal-caster-289121]and region [asia-northeast3]....done.
Success! The app is now created. Please use `gcloud app deploy` to deploy your first app

#step 4 this command ($ git clone)clones a sample file from git hub on the specified URL to a Phython location on the sdk. it gives a statistics of the files size and notifiyes with you with "done"


nellylynn_moyo@cloudshell:~ (focal-caster-289121)$ git clone https://github.com/GoogleCloudPlatform/python-docs-samples

#results
Cloning into 'python-docs-samples'...
remote: Enumerating objects: 18, done.
remote: Counting objects: 100% (18/18), done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 38838 (delta 3), reused 7 (delta 1), pack-reused 38820
Receiving objects: 100% (38838/38838), 60.20 MiB | 10.31 MiB/s, done.
Resolving deltas: 100% (21652/21652), done.

#step 5 this command ($ cd python-docs-samples/appengine/standard_python3/hello_world)changes directory to a phython project which is the URLfor the source of the sample application 

nellylynn_moyo@cloudshell:~ (focal-caster-289121)$ cd python-docs-samples/appengine/standard_python3/hello_world

#step 6 this command ($ sudo apt-get update) locates downloads and update the package gives a breakdown list of packages that it has .. 
#then lists all of them it gives alist of packages that may have failed to update.

nellylynn_moyo@cloudshell:~/python-docs-samples/appengine/standard_python3/hello_world (focal-caster-289121)$ sudo apt-get update

#results 
********************************************************************************
You are running apt-get inside of Cloud Shell. Note that your Cloud Shell
machine is ephemeral and no system-wide change will persist beyond session end.
To suppress this warning, create an empty ~/.cloudshell/no-apt-get-warning file.
The command will automatically proceed in 5 seconds or on any key.
Visit https://cloud.google.com/shell/help for more information.
********************************************************************************
Err:1 http://apt.llvm.org/buster llvm-toolchain-buster-9 InRelease
  Temporary failure resolving 'apt.llvm.org'
Hit:2 http://deb.debian.org/debian buster InRelease                                                                                                      
Get:3 http://deb.debian.org/debian buster-updates InRelease [51.9 kB]
Hit:4 http://security.debian.org/debian-security buster/updates InRelease
Hit:5 http://storage.googleapis.com/bazel-apt stable InRelease
Hit:6 http://repo.mysql.com/apt/debian buster InRelease
Hit:7 https://packages.microsoft.com/repos/microsoft-debian-buster-prod buster InRelease                                                                                    
Get:8 http://packages.cloud.google.com/apt gcsfuse-buster InRelease [3,724 B]
Hit:9 https://download.docker.com/linux/debian buster InRelease                                                                                       
Get:10 https://packages.cloud.google.com/apt cloud-sdk-buster InRelease [6,384 B]                                               
Hit:11 https://packages.sury.org/php buster InRelease                                                     
Ign:12 http://ftp.debian.org/debian jessie InRelease     
Ign:13 http://ftp.debian.org/debian stretch InRelease
Get:14 http://ftp.debian.org/debian stretch-backports InRelease [91.8 kB]
Get:15 http://ftp.debian.org/debian stretch-updates InRelease [93.6 kB]
Hit:16 http://ftp.debian.org/debian jessie Release
Hit:18 http://ftp.debian.org/debian stretch Release
Fetched 247 kB in 3s (77.9 kB/s)
Reading package lists... Done
W: Failed to fetch http://apt.llvm.org/buster/dists/llvm-toolchain-buster-9/InRelease  Temporary failure resolving 'apt.llvm.org'
W: Some index files failed to download. They have been ignored, or old ones used instead.


#step 7 this command ($ sudo apt-get install virtualenv) creates a virtual environment in which you will run your application as you are working on it Python uses these environments to have the advantage of isolating package installations from the system.

nellylynn_moyo@cloudshell:~/python-docs-samples/appengine/standard_python3/hello_world (focal-caster-289121)$ sudo apt-get install virtualenv

#Results

********************************************************************************
You are running apt-get inside of Cloud Shell. Note that your Cloud Shell
machine is ephemeral and no system-wide change will persist beyond session end.
To suppress this warning, create an empty ~/.cloudshell/no-apt-get-warning file.
The command will automatically proceed in 5 seconds or on any key.
Visit https://cloud.google.com/shell/help for more information.
********************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  python3-virtualenv
The following NEW packages will be installed:
  python3-virtualenv virtualenv
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 78.2 kB of archives.
After this operation, 171 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://deb.debian.org/debian buster/main amd64 python3-virtualenv all 15.1.0+ds-2 [58.1 kB]
Get:2 http://deb.debian.org/debian buster/main amd64 virtualenv all 15.1.0+ds-2 [20.1 kB]
Fetched 78.2 kB in 0s (4,971 kB/s)    
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package python3-virtualenv.
(Reading database ... 129614 files and directories currently installed.)
Preparing to unpack .../python3-virtualenv_15.1.0+ds-2_all.deb ...
Unpacking python3-virtualenv (15.1.0+ds-2) ...
Selecting previously unselected package virtualenv.
Preparing to unpack .../virtualenv_15.1.0+ds-2_all.deb ...
Unpacking virtualenv (15.1.0+ds-2) ...
Setting up python3-virtualenv (15.1.0+ds-2) ...
Setting up virtualenv (15.1.0+ds-2) ...
Processing triggers for man-db (2.8.5-2) ...


#step 8 this command ($ virtualenv -p python3 venv) gives a breakdown on the environmentthat has been created and the duration it took 

nellylynn_moyo@cloudshell:~/python-docs-samples/appengine/standard_python3/hello_world (focal-caster-289121)$ virtualenv -p python3 venv
#results 
created virtual environment CPython3.7.3.final.0-64 in 1067ms
  creator CPython3Posix(dest=/home/nellylynn_moyo/python-docs-samples/appengine/standard_python3/hello_world/venv, clear=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/home/nellylynn_moyo/.local/share/virtualenv)
    added seed packages: pip==20.2.2, setuptools==49.6.0, wheel==0.35.1
  activators BashActivator,CShellActivator,FishActivator,PowerShellActivator,PythonActivator,XonshActivator
  
#step 9 this command ($ source venv/bin/activate) activates a the virtual environment 

nellylynn_moyo@cloudshell:~/python-docs-samples/appengine/standard_python3/hello_world (focal-caster-289121)$ source venv/bin/activate

 #step 10 this command ($ pip install  -r requirements.txt)goes to the projetcs diretory an then install dependences this gives you a breakdown of venvshows its a virtula environmnet the results shows breakdown of packages it has installed all the versions that are currently running on the virtual environmnet ad then gives a breakdown list of the envoromnets that has newer versions and also gives a URL to download if you wish to upgrade ton latest versions that may not be installed.
 
(venv) nellylynn_moyo@cloudshell:~/python-docs-samples/appengine/standard_python3/hello_world (focal-caster-289121)$ pip install  -r requirements.txt

#Results 
Collecting Flask==1.1.2
  Downloading Flask-1.1.2-py2.py3-none-any.whl (94 kB)
     |████████████████████████████████| 94 kB 2.1 MB/s
Collecting Werkzeug>=0.15
  Downloading Werkzeug-1.0.1-py2.py3-none-any.whl (298 kB)
     |████████████████████████████████| 298 kB 18.3 MB/s
Collecting click>=5.1
  Downloading click-7.1.2-py2.py3-none-any.whl (82 kB)
     |████████████████████████████████| 82 kB 929 kB/s
Collecting Jinja2>=2.10.1
  Downloading Jinja2-2.11.2-py2.py3-none-any.whl (125 kB)
     |████████████████████████████████| 125 kB 38.6 MB/s
Collecting itsdangerous>=0.24
  Downloading itsdangerous-1.1.0-py2.py3-none-any.whl (16 kB)
Collecting MarkupSafe>=0.23
  Downloading MarkupSafe-1.1.1-cp37-cp37m-manylinux1_x86_64.whl (27 kB)
Installing collected packages: Werkzeug, click, MarkupSafe, Jinja2, itsdangerous, Flask
Successfully installed Flask-1.1.2 Jinja2-2.11.2 MarkupSafe-1.1.1 Werkzeug-1.0.1 click-7.1.2 itsdangerous-1.1.0
WARNING: You are using pip version 20.2.2; however, version 20.2.3 is available.
You should consider upgrading via the '/home/nellylynn_moyo/python-docs-samples/appengine/standard_python3/hello_world/venv/bin/python -m pip install --upgrade pip'
 command.
 
#step11this command $ python main.py)loads a main app for development gives a notification if you want to use a production environ,ment you can use listed URL
 
 (venv) nellylynn_moyo@cloudshell:~/python-docs-samples/appengine/standard_python3/hello_world (focal-caster-289121)$ python main.py
 #results
 * Serving Flask app "main" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: on
 * Running on http://127.0.0.1:8080/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 124-257-297


#step 12 this command ($ gcloud app deploy) updates the details of the application and then prompts to deploy if you accept deployent satrts and gives a total number of files that it has uploaded 

(venv) nellylynn_moyo@cloudshell:~/python-docs-samples/appengine/standard_python3/hello_world (focal-caster-289121)$ gcloud app deploy
#results
Services to deploy:
descriptor:      [/home/nellylynn_moyo/python-docs-samples/appengine/standard_python3/hello_world/app.yaml]
source:          [/home/nellylynn_moyo/python-docs-samples/appengine/standard_python3/hello_world]
target project:  [focal-caster-289121]
target service:  [default]
target version:  [20200911t013709]
target url:      [https://focal-caster-289121.du.r.appspot.com]
Do you want to continue (Y/n)?  y
Beginning deployment of service [default]...
╔════════════════════════════════════════════════════════════╗
╠═ Uploading 363 files to Google Cloud Storage              ═╣
╚════════════════════════════════════════════════════════════╝
File upload done.
Updating service [default]...done.
Setting traffic split for service [default]...done.
Deployed service [default] to [https://focal-caster-289121.du.r.appspot.com]
You can stream logs from the command line by running:
  $ gcloud app logs tail -s default
To view your application in the web browser run:
#step13 command opens the main oage on he browser 
  $ gcloud app browse opens a URL of the hello app that you have created 
  
  
  