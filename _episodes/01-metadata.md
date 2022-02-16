---
title: Reporting to the Database
teaching: 30
exercises: 0
questions:
    - "How do I report to the MigraMar Database?"
    - "Why should I report my data?"
    - "How do I receive my detection matches?"
---
## Reporting Data to an OTN Node

As researchers who are part of the MigraMar Network, you are encouraged to register your projects and report your data and metadata in a timely manner to your Data Manager. This will benefit all researchers in the region through the database's detection-matching system.

This presentation **LINK TO PPT HERE** will cover some of the following topics.

You are encouraged to read the [OTN FAQs Page](https://members.oceantrack.org/faq) for more information.

### How to register with the MigraMar Database

If you wish to register your project with MigraMar you can email OTNDC@DAL.CA for assistance. We require 3 metadata types: 1) project metadata, 2) instrument deployment metadata and 3) tagging metadata. See the templates [here](https://members.oceantrack.org/data/data-collection). These will soon be translated to Spanish for your use!

### What is the benefit of registering with the MigraMar Database?

MigraMar and affiliated networks provide automated cross-referencing of your detection data with other tags in the system to help resolve "mystery detections" and provide detection data to taggers in other regions. MigraMar's Data Manager will also extensively quality control your submitted metadata for errors to ensure the most accurate records possible are stored in the database. MigraMar's database and Data Portal website are excellent places to archive your datasets for future use and sharing with collaborators. We offer pathways to publish your datasets with [OBIS](https://obis.org/), and via open data portals like ERDDAP, GeoServer etc. The data-product format returned by MigraMar is directly ingestible by analysis packages such as [glatos](https://github.com/ocean-tracking-network/glatos) and [resonATe](https://gitlab.oceantrack.org/otndc/resonate) for ease of analysis. OTN offers support for the use of these packages and tools.

### What is the Data Portal?

OTN/MigraMar's `Data Portal` website (https://members.oceantrack.org) is similar to DropBox or another file repository service. While there are helpful links and tools to explore, this site is mainly used to hold private repository folders for each project. In your project folder, you can add files which can be viewed ONLY by anyone who has been given access. These folders are also where the Data Manager will upload your Detection Extracts when they are ready. 

Soon there will  be a website for MigraMar members only!

MigraMar's `database` is built on PostgreSQL/PostGIS and is hosted on OTN hardware at Dalhousie University. Many partner Nodes are hosted at other locations. Users do not have direct write access to the database: the files posted in your Data Portal folder will be downloaded, quality controlled and loaded into the database by a Data Manager.


## Receiving Detection Matches

As researchers who have already submitted data and metadata to the MigraMar Database, you will receive detection-matches for the tags detected on your array and the tags you have release. These are in standard formats call "Detection Extracts" and are provided to you several times a year during a "data push".

### What are Detection Extract data products?

OTN and all of its partner Nodes create Detection Extracts on a semi-regular basis, approximately every 4 months, following a cross-Node coordinated detection matching event known as a Data Push. These Detection Extract files contain only the detections for the year corresponding to the suffix on the file name. See the detailed documentation here [Detection Extract Documentation](https://members.oceantrack.org/data/otn-detection-extract-documentation-matched-to-animals).

### What is a Data Push?

In order to create meaningful Detection Extracts, OTN and affiliated Nodes only perform cross-matching events every 4 months or so (when enough data has been processed). During this Data Push process our databases are backed up, the website is updated and detection matches are released to all relevant projects.

If you're expecting detection extracts but have not yet received them, it is likely that your project is queued for the next Data Push.
