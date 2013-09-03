
% netflix recipes-rss

---

# the goal

    juju bootstrap

    juju deploy cassandra -n3

    juju deploy rss rss-backend -n2 # (config pointing to ribbon external rss publishers)
    juju deploy rss rss-edge -n10
    juju add-relation rss-backend:middletier rss-edge:edge
    juju add-relation rss-backend cassandra

    juju deploy haproxy
    juju add-relation haproxy rss-edge

    # attach subs to backend services
    juju deploy-subordinate eureka-client --with rss-backend
    juju deploy-subordinate archaius-client --with rss-backend
    juju deploy-subordinate servo-client --with rss-backend
    # attach subs to edge services
    juju deploy-subordinate eureka-client --with rss-edge
    juju deploy-subordinate archaius-client --with rss-edge

    juju deploy archaius
    juju add-relation archaius-client archaius

    juju deploy servo
    juju add-relation servo servo-client

    # we might be able to replace eureka server with calls to juju API instead
    juju deploy eureka
    juju add-relation eureka-client eureka


## embedded services

- common

  - karyon
  - blitz4j
  - ribbon

- backend

  - astyanix in relation to cassandra

- edge

  - hystrix in relation to backend

---

# first iteration


    juju bootstrap

    juju deploy cassandra

    juju deploy rss-backend # (config pointing to ribbon external rss publishers)
    juju deploy rss-edge
    juju add-relation rss-backend cassandra

    # attach subs to backend services
    juju deploy-subordinate eureka-client --with rss-backend
    juju deploy-subordinate archaius-client --with rss-backend
    juju deploy-subordinate servo-client --with rss-backend
    # (all of the above configured with standalone fallbacks to localhost)
    # attach subs to edge services
    juju deploy-subordinate eureka-client --with rss-edge
    juju deploy-subordinate archaius-client --with rss-edge
    # (all of the above configured with standalone fallbacks to localhost)


---

# next steps... 

## other services

charming up archaius et al will be a bit more work.  This is actually more
interesting than the recipes-rss components itself... and tells a more complete
netflix story, but it's a decent start to either:

- just use the localhost defaults for the clients for now
- externalize config to point the servo-client to an out-of-band servo server


## use a single rss charm

not really all that important for this rss hello world app... just showing off juju

