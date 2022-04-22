---
title: "Data Push"
teaching: 10
exercises: 0
questions:
- "What is a Data Push?"
- "What are the end products of a Data Push?"
keypoints:
- "A Data Push is when we verify all the data in the system, fix any issues, and then provide detection matches to researchers"
- "Detection Extracts are the main end product of the Push"
---

## What is a Data Push?

A Data Push is when the OTN data system is re-verified and any new relevant information is sent to researchers. New data being brought in is cut off so that what's in the system can be reliably verified. This way any issues found can be fixed and the data can be in the best form based on the information available at that moment. Once verification is done detections are matched across nodes and detection extracts are sent out to researchers. This is also the time when summary schemas like `discovery`, `erddap`, and `geoserver` are updated with the newly verified and updated data.

### What is the Push Schedule?

Push events happen **three** times a year. They start on the third Thursday of the "push month" which are February, June, and October. This date is the cut-off date for all data-loading: no records can be loaded after this until important verification and processing tasks are completed.

With the increased number of Nodes joining the Pushes, we are announcing the schedule for the next year. Please prepare in advance and mark your calendars.

Push schedule through 2023:
- June 23, 2022
- October 20, 2022
- February 16, 2023
- June 15, 2023
- October 19, 2023

### Activities During the Push

Both node managers and data analysts have important roles during a push:

Node Managers need to ensure that the following is done:
1. The first job is to get the Node's data loaded in time for the cut-off date. Data is submitted by researchers on a continuous basis, and generally increases just before a cut-off date. We prioritize loading data as it arrives, to attempt to prevent a backlog near the Push date.
1. The second job for Node Managers is to create and send out Detection Extracts when they are ready to be made. 

Once the cut-off date has passed Node Managers are "off duty", then when it's time for Detection Extracts to be created and disseminated that task is assigned to the Node Managers, but this does **not** signify the end of the Push. There are several more "behind the scenes" steps required.

Data Analysts have many jobs during a Push, including:
1. verify all data in the database
1. perform cross-node matching
1. perform robust back-ups
1. repopulate our Data Portal website

## Detection Extracts

[Detection Extracts](https://members.oceantrack.org/data/otn-detection-extract-documentation-matched-to-animals) are the main output of the Push. They contain all the new detection matches for each project. There are multiple types of detection extracts OTN creates:
- 'qualified' which contain detections collected by an array but matched to animals of other projects
- 'unqualified' which contain the unmatched or mystery detections collected by an array
- 'sentinel' which contain the detections matched to test or transceiver tags collected by an array
- 'tracker' which contains detections that have been mapped to animals tagged by a project that can originate from any receiver in the entire Network

Detection Extract files are formatted for direct ingestion by analysis packages such as [*glatos*](https://github.com/ocean-tracking-network/glatos) and [*resonate*](https://gitlab.oceantrack.org/otndc/resonate). They use DarwinCore terminology where relevant.

These files are uploaded to a projects Data Portal folder and can only be shared in accordance with OTN's Data Policy.

{% include links.md %}