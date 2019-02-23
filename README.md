# CosmosDB_Mongo_Django_Workaround
Workaround for Django on Cosmos DB Mongo.

Good resources to get started if you are new:
  Setting up virtual environment on Windows: http://timmyreilly.azurewebsites.net/python-pip-virtualenv-installation-on-windows/
  Setup Django sample - please follow this tutorial https://docs.djangoproject.com/en/2.1/intro/tutorial01/
  To use Mongo you need 'Djongo'(It's not Django :)) https://nesdis.github.io/djongo/get-started/#

Assuming you have working environment let's say the environment is located at Folder Name "Sample"

1. Download the files(query.py,introspection.py and base.py) from this repo to your local folder.
2. Replace 2 files in ..\sample\Lib\site-packages\djongo\ with downloaded query.py and introspection.py
3. Replace the file in ..\sample\Lib\site-packages\djongo\sql2mongo\query.py with downloaded query.py
4. Make sure settings.py file pointing to Cosmos DB Mongo endpoint (Username and password available in Azure portal):

              DATABASES = {
                 'default': {
                      'ENGINE': 'djongo',
                      'NAME': 'test',
                  'USER': 'username',  
                      'PASSWORD': 'password',  
                      'HOST': 'username.documents.azure.com',  
                      'PORT':10255,
                  'SSL':True,
                  'OPTIONS':{
                  'connectTimeoutMS':30000,
                  }
                  }
              }
 


Now run python manage.py migrate, it should migrate with out any issues.
