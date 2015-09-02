# redis-discovery
Redis in docker container for Giant Swarm service discovery

The way this here used Dockerfile installs redis, is heavily inspired by
https://github.com/dockerfile/redis .

Why is it not just a fork?
- We don't want the repository to be named redis.
- We don't want the configuration to be done as in dockerfile/redis.
- We just used the redis installation from the dockerfile/redis Dockerfile as orientation.

How does this diverge from the original config?
- Configure slaves to be writable. We are running into this for a jiffy when
  things are rescheduled. Then everything that tries to write against the
  discovery, will not succeed. So with this, the chance is higher to still
  propagate some updates, even when we have some movement within our
  components.
- Configure all discovery components (redis), to not persist any data. Our
  discovery is ephemeral. Everything we need to know is written over and over
  again. Backing up those information has no value. We have no restore
  mechanism either. It wouldn't make sense to have one, since all entries
  expire within 10 seconds.
