# CA5

Since Environment variables are being used to Login to Mongo DB and Access the Database, we need to create a .env file locally.
The following variables must be placed in the .env file:

MONGO_ADMIN_USER=admin
MONGO_ADMIN_PASS=pass
MY_DB_NAME=mlops_database

Using Mongo-Express (Port 8081), create a database named "mlops_database", within this, create a collection named "mlops_collection".
The mlops_collection will contain data in the format:

{
  id: Object(),
  "Roll#": "123",
  "Name": "ABC"

}


Since port 8080 is already in use by Jenkins, to access the app use port 8888.
The contents of the collection will be display on the route: http://localhost:8888/students




