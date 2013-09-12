

at scale... getting deployments consistent
  better to use baked images

  conformance-monkey

we wanna diagram

separate instances of asgard for test, prod, etc...

stack of service-oriented projects:

- asgard
- archaius config service
- j


hysterix
  - atyuanix
  - ribbon
     uses eureka for dns-like... (eureka has its own store)
  - ebcache (?)

chronos keeps config changes
  - edda is aws specific... chronos is higher level (history of archaius properties)


turtle clusters of cass
  - cassturtle is the genesys node
  - not using vnodes
  - dev for prium on 1.2...
     good place to contribute

pytheas  build dashboards... dynamically I assume
  d3
  with backend for storing this
  cassandra mgmt dashboards

atlas metrics... not open yet
  not cost-effective until you're at scale

hadoop services... genie/lipstick
  genie... hadoop job submission... Sriram
  lipstick for pig visualization... Jeff
    maybe something else like "ss-table formats" cassandra to hadoop
  

ice
  grails... deployed similarly to asgard

---

eureka... tomcat-based... every 30 seconds things register themselves

exhibitor wraps zookeeper
  - might be a good candidate for a standalone

edda... provider-history
  (everything amazon ever returned against any of its 'describe' api calls)
  _and_ all the eureka calls
  eureka too
  scala and pluggable
  openstack edda plugin

paypal demonstrating openstack asgard integration


simian army
  janitor monkey
  snapshot monkey
    snaps all your ec2 volumes


hysterix is fast enough to propagate cache invalidation for evcache

there's another project due to be opened
  jcache w/ memcached w/ cassandra

netflix graph... 


netflix architecture plugin.... to add to memcached


hysterix w/ turbine


wtf are vnodes?
  - oh, some sort of cassandra config




---

airplane app is fork of 
rss recipe
  karyon config
  (production versions?)

flux capacitor
  beanstalk and cloudformation

each instance exposes hyssterix... turbine aggregrates tall of those
  the turbine server needs to be up too
  hysterix can send straight to graphite via servo



---

netty instead of tomcat is under consideration...

they're working against tomcat for RX 


jersey?


---

chakra
kafka

feeds into hive

more real-time pipeline

taps so kafka can feed into that pipeline

druid
maybe storm


---

denominator, would be a great project to collaborate with netflix


---

openjdk _should_ work on all netflixoss components, but cassandra's broken on openjdk 1.6.
???




