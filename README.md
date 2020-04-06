# Containers & The Secure App
## A Palo Alto Tech Challenge Experience

**Author: Thomas Linkin**

**Date: 4-6-2020**

### Overview

These contents setup a two container secure "app" scenario in which an application
served by one container is protected by a proxy container that performs basic
authentication and ensures the use of SSL. The application is only accessible at a
special URL which provides another layer of protection. The containers utilize
NginX as both the web server and the proxy. The base containers are the official
alpine based containers released by NginX on Docker Hub.

### Instructions

The instructions to setup this solution are as they appear in outline presented
in the challenge description. Those commands should be run from the root of this
project.

### Assumptions

This challenge solution has the following assumptions:

- The instructions to run the solution do not deviate from the outline in the
challenge description

- The system from which this solution will be run has access to Docker Hub

- Standard HTTP and HTTPS ports are used (80/443)

- The containers will be accessed either by using `localhost` or resolving `container`
to the proxy container

### Considerations

To ensure that the end result was as "secure" as possible for this challenge, the
following considerations were made in addition to the requirements from the
challenge description:

- NginX on the web container will only respond to the name 'web' as resolved by the
proxy container in the internal Docker bridge network.

- NginX on the web container has been instructed to only allow requests from the
`172.16.0.0/12` subnet in order to limit exposure in the event the application
container ports are accidentally exposed. The `/12` netmask was used to account for
reasonable variation in Docker's internal networking. For example when tested "on
my laptop" the internal Docker network used `172.19` for the first two octets.

- The default NginX configurations were fully replaced to ensure they did not
introduce any unexpected behavior.
