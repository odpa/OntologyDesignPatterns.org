# OntologyDesignPatterns.org Docker Configuration

This repository contains a Docker configuration supporting the community
[Ontology Design Patterns portal](http://ontologydesignpatterns.org).

This is early work/work in progress and subject to change at any time.

## Getting started

1. Install a recent version of Docker. If you are on a Mac, ensure that you are
not using the older version that depends on VirtualBox.

2. Clone this repository.

3. Step into the repository, then run:

`docker-compose up`

## Where is my data?

The data for the two component Docker images (mysql and smw) should be
automatically stored in a subdirectory called "data" beneath the directory
where the docker-compose.yml file is kept.

## How do I configure things?

Look in the two files mysql-variables.env and smw-variables.env for environment
variables that will be used by the two Docker containers spawned by this
compose configuration. Note especially that for real deployment you will need
to change the passwords in these files!

## How do I access it?

Port 80 on the SMW container is mapped against port 80 on localhost, and the
Apache instance within that container will respond to requests to the host name
beta.ontologydesignpatterns.org. So, ensure that the DNS name
beta.ontologydesignpatterns.org points to localhost (easiest way: add a line in
  your system hosts file), and just go there in your browser.

## But what if I run other stuff on port 80?

Modify the port mapping line in docker-compose.yml for the smw service, so that
the container port 80 is exposed on another external port. For instance, to
use port 8080 the relevant lines might read:

`ports`<br/>
`- 8080:80`
