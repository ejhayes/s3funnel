# s3 funnel install instructions

- launch ec2 instance (hub-dev*, latest version) and login as user ubuntu

- install git

  sudo apt-get install git

- install pip

  sudo apt-get install python-pip

- install virtualenv

  sudo pip install virtualenv

- clone repository from github

  git clone https://github.com/ejhayes/s3funnel
  cd s3funnel
  virtualenv v
  source v/bin/activate
  python setup.py install
  
  
BOTO Configuration
==================

Config File
-----------

- Edit ~/.boto

  [Credentials]
  aws_access_key_id = YOUR_KEY_HERE_
  aws_secret_access_key = YOUR_SECRET_HERE_

Environment Variables
---------------------

- Export environment variables

  export AWS_ACCESS_KEY_ID=YOUR ACCESS KEY
  export AWS_SECRET_ACCESS_KEY=YOUR SECRET ACCESS KEY
  
  
Doing a mass delete
===================

- We can run multiple threads for taking inventory of the files, but there is a chance of collision when deleting.  Delete operations will run much faster with more threads!

  s3funnel BUCKET_NAME list --threads=5 | s3funnel BUCKET_NAME delete --threads=10