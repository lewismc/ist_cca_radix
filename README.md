OODT RADiX README
=================
# Introduction
An [OODT](http://oodt.apache.org) [RADiX Powered](https://cwiki.apache.org/confluence/display/OODT/RADiX+Powered+By+OODT) 
deployment for File Management, Metadata Extraction and Cataloging.

This will demo how to 
 * use the RADiX Maven build profiler to rapidly deploy the core components of OODT as a mechanism for building a 
 catalog and archive service
 * use Apache OODT to ingest files contained within Amazon's S3 service into the OODT File Manager service hence physically
 buidling the Catalog. This has the resulting outcome that it makes the content searchable via Apache Solr.
 
  OODT version 0.8

# Requirements:
* Java Development Kit (JDK) 1.6+
* JAVA_HOME set 
  see: http://docs.oracle.com/cd/E19182-01/820-7851/inst_cli_jdk_javahome_t/index.html
* (Snapshot releases only) OODT source tree installed. 
  see: http://oodt.apache.org/components/maven/filemgr/user/basic.html

# Contact

The first port of call for assistance is the Apache OODT [mailing lists](http://oodt.apache.org/contact/).

# Installation:

RADiX is desgined such that it takes the pain out of fetching then building the various OODT components.
You can get up and running with your RADiX project using the following *nix-style command line instructions.

## Build oodt
```
  # creates the distribution of your OODT project using *mvn package* target
  $ mvn clean package <OPTIONAL PROFILES> # see optional build profiles below
```

## Create deploy area
```
  # create a deploy directory for your data management system
  $ mkdir /some/path/to/oodt_deploy
```

## Deploy oodt
```
  # untars the distribution into the created deployment directory 
  $ tar zxf distribution/target/ist_cca_radix-distribution-0.1-bin.tar.gz -C /some/path/to/oodt_deploy
```  
  

  ---
  NOTE: For other build configurations, add the following arguments:
  (default)           : bin, crawler, data, extensions,
                        filemgr (Lucene), logs, pcs, resmgr,
                        tomcat, workflow, pge

  -Pfm-solr-catalog   : default components, filemgr (Solr),
                        solr, tomcat/webapps/solr

# Run OODT:
```
  # moves into the deployment directory and starts the OODT system
  $ cd /some/path/to/oodt_deploy
  $ cd bin
  $ ./oodt start
```
Finally,
```
  # Launches batch stub on the port 2001
  $ ./resmgr/bin/batch_stub 2001
```

Although at this stage you may see that some errors have failed to start, you can verify what is running by opening a browser and navigating to [http://localhost:8080/opsui](http://localhost:8080/opsui). Click on *PCS Status* link to get detailed information about running processes. A green arrow indicates that the corresponding process is running correctly. File Manager (http://localhot:9000), Workflow Manager (http://localhost:9001) and Resource Manager (http://localhost:9002) should all be up and running.

For more context and detail on the above content please see the [RADiX documentation](https://cwiki.apache.org/confluence/display/OODT/RADiX+Powered+By+OODT).

# File Management

Once your services are up and running as above, you are ready to begin learning about the OODT File Manager service and build your implementation.

The first point of contact is to take some time and read hrough some useful documentation, namely:
 * [OODT File Manager User Guide](https://cwiki.apache.org/confluence/display/OODT/OODT+Filemgr+User+Guide): File Management for beginners
 * [OODT PushPull User Guide](https://cwiki.apache.org/confluence/display/OODT/OODT+Push-Pull+User+Guide): A guide for pulling data products from an array of remote resources and pushing them to local staging directories ready for ingestion into the File Manager.
 * [PushPull Plugin Central](https://cwiki.apache.org/confluence/display/OODT/OODT+Push+Pull+Plugins): some non Apache released Push Pull protocol plugins that contain runtime and compile-time dependencies on LGPL licensed plugins.
 * [Solr File Manager Quick Start](https://cwiki.apache.org/confluence/display/OODT/Solr+File+Manager+Quick+Start+Guide): a guide to quickly deploy and test a system composed of the OODT File Manager and [Apache Solr](http://lucene.apache.org/solr/).
 * [OODT User Guides](https://cwiki.apache.org/confluence/display/OODT/CAS+User+Guides): A comprehensive list of resources which provide detail of OODT Cataloging an Archiving Services.
