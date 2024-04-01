# Meteorological_data_collection

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

__2. Create the Docker image of the python script__ 

In your shell, access the current directory of the python script

Create the image from the dockerfile using this command in your shell:
```docker build -t get_data .```

Check that the image has been created using this command:

```docker images```

__3. Create the dockercompose__

In your shell, stay in the current directory.

Create the docker compose with the docker-compose.yml command in your shell:

```docker-compose up```


To check that all the commands have worked, access your Mongodb set up database with docker-compose.

You should find 2 collections there:

- city (with all the city data stored)

- weather (with the first collection of meteorological data launched with docker-compose)

__Good to know:__

Data is collected every 15 minutes for all cities.

