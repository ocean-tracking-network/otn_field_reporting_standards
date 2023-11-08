---
title: Introduction to the Data Portal
teaching: 30
exercises: 0
questions:
    - "What is the Data Portal?"
    - "What features will be most useful to me?"
keypoints:
    - "The Data Portal has many useful features"
---

# What is the Data Portal?

OTN's `Data Portal` [website](https://members.oceantrack.org) is similar to DropBox or another file repository service. This is built using the open-source `Plone` software, and is sometimes called Plone around OTNHQ. While there are helpful links and tools to explore, this site is mainly used to hold private repository folders for each project. In a project folder, you can add files which can be viewed ONLY by users who have been given access. These folders are also where the Data Manager will upload Detection Extracts when they are ready.

OTN's `database` is built on PostgreSQL/PostGIS and is hosted on OTN hardware at Dalhousie University. Many partner Nodes are hosted at other locations. Users do not have direct write access to the database: the files posted in a Data Portal folder will be downloaded, quality controlled and loaded into the database by a Data Manager. OTN Field Techs cannot access the database directly unless they are trained to do so.

# Useful tools for Field Techs

OTN's Data Portal website is used extensively by OTNHQ staff members for many purposes. A few of these are highlighted below!

## Project Pages

Each project which has registered with OTN or a partner Node will have a public project summary page. These are searchable from the `Home page` using the interactive map tool, or the map search option. An example project page for project NCAT is here [https://members.oceantrack.org/OTN/project?ccode=NCAT](https://members.oceantrack.org/OTN/project?ccode=NCAT). You should make yourselves familiar with these webpages to share with partners.

This page contains the following sections:

1. Title, citation, Node membership information and collaboration type (Tracker, Deployment or Data) - this will tell you lots about the project!
2. An interactive map showing non-clickable tagging sites and clickable station-history information (note: some Nodes do not share these locations so they will be absent from the map)
3. A list of the species studied by the project (provided by the PI)
4. Contact information for Principal Investigators and Points of Contact
5. Related URLs including:
	* for logged in users (unless project is public) - a link to the project's private repository
	* for logged in users (unless project is public) - a link to the `Detection Extracts` subfolder in the project's repository
	* a `stations` KML file containing the GPS locations of all stations (only if this project is part of a Node which shares these locations)
	* a `deployments` CSV containing a summary of all deployments (not the same format as the metadata -- not provided if this project is part of a Node which doesn't share these locations)
	* if a project is public - a KML and CSV file containing information regarding the project's tagged animal records
6. A summary of all the tag-projects whose tags have been detected on the selected array and the array-projects which have detected their tags.

**You will likely be most interested in the information from item 6 - this can be used to learn about detections without contacting OTNDC**

![Example Project Page](/fig/project_page_tools.PNG)

## Project repository

A project's repository folder is only accessible to logged-in Plone users who have been given specific permission to view the folder. OTN Field staff should have access to all folders.

This is where researchers, and OTN staff, can share files with each other in a secure manner, ensuring they are archived properly. 

![Example Repository](/fig/repository_template.PNG)

Below, a few relevant features are highlighted.

### Data and Metadata

This is a standard subfolder available in all project repository folders. This is the location for all **tagging and deployment metadata**, offloaded **data files**, and other useful documents. For OTN projects, often this folder is organized into `missions` and/or `years` for better coordination.

Files and folders can be added using the `Add new...` option on the left-hand menu. The folder organization is customizable, like Dropbox/Google Drive or similar programs.


#### TIP: Batch Uploading

If you are uploading multiple files at once, into the same folder, you can use the `Batch Upload` function to save time.

1. Choose the `Contents` option on the left-hand menu
2. Choose the `Upload` option
3. You can browse for files or drag-and-drop them into the Upload window, until all relevant files are selected.
4. Click the `Upload` button and wait for the upload to complete before navigating away.
5. When you are finished, return to your standard folder display by choosing `View` from the left-hand menu.

**Please do not Batch Upload single VRL files - these should be zipped together**


#### TIP: Editing/Renaming

You can edit a file or folder after you've created it, using the `Edit` option on the left-hand menu.

Editing a folder:
- ensure you are inside the folder when you press `Edit`
- you will be able to change the description, title, etc.

Editing a file:
- ensure you have the file open when you press `Edit`
- you will be able to choose `replace with new file`, or you may edit the title, description etc.

Plone has a version-control history, so it is possible to revert back to a previous version of a file if you edited it by mistake.

OTNDC staff receive an email each time you edit, delete or post a file.

#### TIP: Finding a current file

Within the `Data and Metadata` subfolder, it can often be difficult to find the current year/mission folder. This is because the default sorting is based on the date the file/folder was created, from oldest to newest. We have manually re-sorted for many projects, so that the newest folder is at the top for easier access, but this is not the default.

Please ensure you scroll to **check all available mission/year folders before you determine which is the newest.**

Inside the newest folder, there may be multiple files. If the titles/descriptions do not make it clear which one is newest you can always review the `last modified` date to determine this.

When in doubt: please ask OTNDC staff to help you find the newest file or export a clean file from the database for you, so you do not accidently use an outdated metadata sheet for mission planning. This will make everyone's lives easier!

### Detection Extracts

OTN and its partner Nodes create Detection Extracts on a regular basis, every 4 months (Push months are February, June, and October), following a cross-Node coordinated detection matching event known as a Data Push. These Detection Extract files contain only the detections for the year corresponding to the suffix on the file name. See the detailed [detection extract documentation](https://members.oceantrack.org/data/otn-detection-extract-documentation-matched-to-animals) for more information.

If you are ever interested in learning more about what a project has detected, you are welcome to check out the content in the Detection Extracts. Reminder that you **can not share this information** without reviewing the [OTN Data Policy](https://members.oceantrack.org/data/policies) or contacting OTNDC staff for guidance.

### Equipment

This subfolder is the location where Shipping Lists can be posted and reviewed, if relevant. The shipping/inventory tracking workflow has moved to the [SnipeIT inventory system](https://ops.oceantrack.org/snipeit/) and [Asana](https://app.asana.com/0/1203822208185209/1203822208185209).

### Background

This subfolder is the location where OTN Project Management staff will upload loan agreements, project plans, and legal paperwork, if relevant. This folder is only visible to OTN staff members by default.

## FAQ page

OTNDC has created a [Frequently Asked Questions](https://members.oceantrack.org/faq) page on the Data Portal. This will contain useful information about OTN's policies, Nodes, metadata, and data products. It is recommended you refer to this **often** and familiarize yourself with the answers to some of these questions, in case you are asked by partners.

If there are topics you think should be added, please reach out to OTNDC - this page can be updated at any time to remain valuable to users.

![Current FAQs](/fig/FAQ_page_updated.PNG)

## Statistics Page

OTNDC has created a [Statistics](https://members.oceantrack.org/statistics) page on the Data Portal. These statistics are updated every 4 months during a Data Push, and can be used for presentations, exploration and general interest. Summaries include:

- an interactive barplot showing the number of tagged individuals, per species, coloured by IUCN status
- a pie chart showing the total number of detections in the OTN database, by type
- an interactive chart showing the number of receivers "active" each month, coloured by year
- an interactive map showing the "currently active" receivers we know are still in the water at the time of publishing. Only Node's whose data policies allow the publishing of station locations are included (not FACT, ACT or MigraMar)

Additional summaries or plots can be created by OTNDC staff upon request, and if the need arises, even incorporated into this webpage. Reach out if you have ideas!

![Example from Statistics Page](/fig/stats_page.PNG)

{% include links.md %}
