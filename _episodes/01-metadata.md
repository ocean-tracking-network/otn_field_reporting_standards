---
title: Reporting to the Database
teaching: 30
exercises: 0
questions:
    - "How do I report to the OTN Database?"
    - "Why should I report my data?"
    - "How do I receive my detection matches?"
keypoints:
    - "Metadata templates are used to report records"
    - "OTN matches data and metadata across numerous geographic areas"
    - "Detection extracts are returned to researchers after data pushes"
---
## Reporting Data to an OTN Node

As researchers who are part of the OTN Network, you are encouraged to register your projects and report your data and metadata in a timely manner to your Data Manager. This will benefit all researchers in the region through the database's detection-matching system.

**This presentation** [ONC and OTN: a Collaboration](../files/ONC_workshop_2022_04.pptx) will cover some of the following topics.

You are encouraged to read the [OTN FAQs Page](https://members.oceantrack.org/faq) for more information.

### How to register with the OTN Database

In order to register a project with OTN, we require 3 metadata types:
1. project metadata
2. instrument deployment metadata
3. tagging metadata

See the templates [here](https://members.oceantrack.org/data/data-collection).  OTNDC@DAL.CA is the best contact for assistance

### What is the benefit of registering with the OTN Database?

OTN and affiliated networks provide automated cross-referencing of your detection data with other tags in the system to help resolve "mystery detections" and provide detection data to taggers in other regions. OTN's Data Manager will also extensively quality control your submitted metadata for errors to ensure the most accurate records possible are stored in the database. OTN's database and Data Portal website are excellent places to archive your datasets for future use and sharing with collaborators. We offer pathways to publish your datasets with [OBIS](https://obis.org/), and via open data portals like ERDDAP, GeoServer etc. The data-product format returned by OTN is directly ingestible by analysis packages such as [glatos](https://github.com/ocean-tracking-network/glatos) and [resonATe](https://gitlab.oceantrack.org/otndc/resonate) for ease of analysis. OTN offers support for the use of these packages and tools.

### What is the Data Portal?

OTN's `Data Portal` [website](https://members.oceantrack.org) is similar to DropBox or another file repository service. While there are helpful links and tools to explore, this site is mainly used to hold private repository folders for each project. In your project folder, you can add files which can be viewed ONLY by anyone who has been given access. These folders are also where the Data Manager will upload your Detection Extracts when they are ready.

OTN's `database` is built on PostgreSQL/PostGIS and is hosted on OTN hardware at Dalhousie University. Many partner Nodes are hosted at other locations. Users do not have direct write access to the database: the files posted in your Data Portal folder will be downloaded, quality controlled and loaded into the database by a Data Manager.


## Receiving Detection Matches

As researchers who have already submitted data and metadata to the OTN Database, you will receive detection-matches for the tags detected on your array and the tags you have release. These are in standard formats call "Detection Extracts" and are provided to you several times a year during a "data push".

### What are Detection Extract data products?

OTN and all of its partner Nodes create Detection Extracts on a semi-regular basis (approximately every 4 months) following a cross-Node coordinated detection matching event known as a Data Push. These Detection Extract files contain only the detections for the year corresponding to the suffix on the file name. See the detailed [detection extract documentation](https://members.oceantrack.org/data/otn-detection-extract-documentation-matched-to-animals) for more information.

{% include links.md %}
