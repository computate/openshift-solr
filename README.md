# Containerized SOLR + OpenShift
Apache SOLR makes it easy to add search capability into your Java apps.  SOLR is a search server (backed by the Lucene serach library).  This repository provides a way for you to take advantage of that in OpenShift.

<h1> THIS IS CURRENTLY IN WORK ---- YMMV</h1>

<h3>There are 2 distinct parts to this repo:</h3>
    
*(1) A Dockerfile*

This overrides the [official SOLR image][2] to tweak a few things in order to run SOLR efficiently on OpenShift.  
<h4>FYI, you don't have to build the image, you can use a prebuilt image - I'll try to keep updated versions of it available on docker hub.</h4>
[![docker hub stats](http://dockeri.co/image/dudash/openshift-solr)](https://hub.docker.com/r/dudash/openshift-solr/)


*(2) S2I scripts (comging soon)*

These are to allow you to easily push your project specific configuration files in to SOLR.


## How to use all of this with your apps
Sounds cool right?  It is.  And here's how you can use it.

### If you just want to run SOLR in OpenShift...

Create the SOLR app from a Docker image
`> oc new-app dudash/openshift-solr`

Now you can access it via the route that was automatically exposed on port 8983 and whereever your OpenShift apps route (e.g. openshift-solr-myproject.127.0.0.1.nip.io)


### If you want to provide configuration in an automated way...
* Import/create the provided S2I image stream
`> oc create -n openshift -f XXXXX`

* Fork this repo 
* Update the config files in solr-config to your SOLR configuration

* Create a new app using S2I (this will create the SOLR core and inject your configuration)
`> oc new-app XXXX XXXX`

Now you can access it via the route that was automatically exposed on port 8983 and whereever your OpenShift apps route (e.g. openshift-solr-myproject.127.0.0.1.nip.io)


## About this repo
Here is some information about how this all works behind the scenes.

### The Dockerfile

### The S2I process
TBD

#### assemble script details
TBD

#### run script details
TBD


## Want to help?
If you find and issues, go ahead and write them up.  If you want to submit some code changes, please see the [CONTRIBUTING][3] docs.


[1]: https://github.com/docker-solr/docker-solr
[2]: https://store.docker.com/images/f4e3929d-d8bc-491e-860c-310d3f40fff2?tab=description
[3]: ./CONTRIBUTING.md