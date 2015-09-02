# redis-discovery
Redis in docker container for Giant Swarm service discovery

The way this here used Dockerfile installs redis, is heavily inspired by
https://github.com/dockerfile/redis . Why is it not just a fork?
- We don't want the repository to be named redis.
- We don't want the configuration to be done as in dockerfile/redis.
- We just used the redis installation from the dockerfile/redis Dockerfile as orientation.
