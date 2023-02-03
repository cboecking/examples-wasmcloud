# wasmCloud Pet Clinic
The wasmCloud Pet Clinic example application is a WebAssembly and wasmCloud-based reimagining of the classic [Spring Boot microservices Pet
Clinic](https://github.com/spring-petclinic/spring-petclinic-microservices) example.

The purpose of this readme is to help you learn the wasmCloud application runtime. We took great care to describe how we designed the application and how you can extend it. We paid special attention to vocabulary. If you have questions or concerns about any aspect of this application, please discuss it here...

## Application Architecture
The wasmCloud Pet Clinic application has a simple architecture: start all five of the actors,
push a link definition between the **Clinic API** actor and an **HTTP Server** capability provider,
and then push link definitions between the Customers, Vets, and Visits actors and a relational
database. Lastly, ensure that both the HTTP Server and relational database capability providers are
started.

The wasmCloud Pet Clinic consists of the following five [actors](./actors):
* [Clinic API](./actors/clinicapi/README.md) - The main JSON (aka "REST") API gateway for
  interacting with the service
* [Customers](./actors/customers/README.md) - Customers/Owners Actor - roughly equivalent to the
  original Customers/Owners microservice.
* [Vets](./actors/vets/README.md) - Veterinarians actor, roughly equivalent to the original Vets
  service.
* [Visits](./actors/visits/README.md) - Visits service, roughly equivalent to the original visits
  service.
* [UI](./actors/ui/README.md) - An actor that contains all assets for the petclinic UI. This actor
  will serve the assets through the Clinic API
  
And the following two capabilities:
* Http Server - Provides functionality needed to interact with the outside world via http/https
* Postgres - Provides functionality needed to CRUD records in a PostgreSQL database

## Inspecting the Code


## Running the Petclinic

If you'd like a quick out of the box example of the petclinic, you can use the included `run.sh`
script to automatically spin up a running wasmcloud host, database, and all the actors. This does
require `docker` to be installed as all the dependencies are run as docker images. To start
everything, run:

```console
$ ./run.sh all
```

To cleanup everything when you are done:

```console
$ ./run.sh wipe
```

Once it is running, you should be able to access the PetClinic application on `localhost:8080`
