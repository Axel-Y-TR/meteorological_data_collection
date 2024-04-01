# Meteorological_data_collection

Description:

This work was done as part of a class project to discover the functionality of Mongodb with Docker (Docker compose).

**__Composition of the repository📂:__**

```A total of 5 files```

1. app.py (Script used to collect data from the open weather website)

2. city.json (Json file containing information about the cities whose data we want to collect, name, location, etc.)

3. requirement.txt (file containing the dependencies and their version to be used to create the docker app.py image)

4. dockerfile (file with specifications for creating the docker app.py image)

5. docker-compose.yml (specification file for the docker-compose with a script_python container + a MongoDB container)

**__User guide😊__** 

__1. Clone the repository__

Do not hesitate to clone this repo in order to have access to these resources locally and test the set up.

__2. Put your API Key on the python script__ 

Create your Openweather api key on this site - https://openweathermap.org/api.
You need to register in the data current section to obtain the API key to use with python.

Go to the app.py script, then insert your key in the api-key variable in the get_data function


__3. Create the Docker image of the python script__ 

In your shell, access the current directory of the python script

Create the image from the dockerfile using this command in your shell:

```docker build -t get_data .```

Check that the image has been created using this command:

 ```docker images```

__4. Create the dockercompose__

In your shell, stay in the current directory.

Create the docker compose with the docker-compose.yml command in your shell:

```docker-compose up```


To check that all the commands have worked, access your Mongodb set up database with docker-compose.

You should find 2 collections there:

- city (with all the city data stored)

- weather (with the first collection of meteorological data launched with docker-compose)

__Good to know:__

Data is collected every 15 minutes for all cities.

**__Files description🎼__** 

__Docker-compose.yml:__

This YAML file is a configuration for Docker Compose:

- `version: '3.8'`: This specifies the version of the Docker Compose syntax used in this file.

- `services`: This section defines the Docker services you want to run.

  - `mongodb`: A service using the `mongodb/mongodb-community-server:latest` image, which is the official Docker image for MongoDB Community Server. This service will be accessible on port 27017 of the host. It also uses a named volume `mongodb_data` to store MongoDB database data persistently.

  - `python_script`: A service that builds an image from a Dockerfile in the current directory (context `.`). The Dockerfile is specified as `Dockerfile`. This service depends on the `mongodb` service to ensure MongoDB is started before running the Python script. It also mounts the `app.py` file into the container and sets an environment variable `MONGO_URI` to instruct the Python application how to connect to MongoDB. Finally, it executes a Python script named `app.py` in a loop every 900 seconds.

- `volumes`: This section defines the Docker volumes used by the services.

  - `mongodb_data`: A named volume that will be used to store persistent data for MongoDB.

In summary, this Docker Compose file defines two services: a MongoDB service and a Python service that runs a Python script in a loop while connecting to the MongoDB database.





