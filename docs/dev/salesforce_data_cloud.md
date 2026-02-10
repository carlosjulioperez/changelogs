- [Salesforce Data Cloud Consultant Certification](#salesforce-data-cloud-consultant-certification)
  - [Data Cloud Process Overview](#data-cloud-process-overview)
    - [Data Cloud Lifecycle](#data-cloud-lifecycle)
  - [Data Cloud Setup and Administration](#data-cloud-setup-and-administration)
    - [Data Cloud Tenant Endpoint](#data-cloud-tenant-endpoint)
    - [Load Data into Contact Object](#load-data-into-contact-object)
    - [Data Streams](#data-streams)
    - [Create new Data Stream](#create-new-data-stream)
  - [Data Ingestion and Modeling](#data-ingestion-and-modeling)
    - [Data Space](#data-space)
    - [Data Explorer and Query Editor](#data-explorer-and-query-editor)
    - [Upload Reservation and Contacts Records on Amazon S3](#upload-reservation-and-contacts-records-on-amazon-s3)
    - [Create Connection between Amazon S3 and Data Cloud](#create-connection-between-amazon-s3-and-data-cloud)
      - [Connect Salesforce with Amazon S3](#connect-salesforce-with-amazon-s3)
      - [Create New Data Stream to get information from Amazon S3](#create-new-data-stream-to-get-information-from-amazon-s3)

# Salesforce Data Cloud Consultant Certification

## Data Cloud Process Overview

![alt text](img/datacloudworks.png)

| Etapa | Descripción |
|-------|-------------|
| Data Sources | Data is collected from multiple sources such as CRM, first- and third-party data, cloud storage, APIs, and devices. |
| Connect | Data is ingested in real time or in batches and scaled to handle large volumes efficiently. |
| Harmonize | Data is cleaned, standardized, and mapped to **common data models** so all data speaks the same language. |
| Unify | Records are unified to create a **Single Source of Truth**, building a unified customer profile using the **Customer Graph**. |
| Analyze & Predict | Insights are generated through analytics, business intelligence, and AI-powered predictions. |
| Activation | Insights are activated through **applications, flows, and actions** across marketing, sales, and service. |

**In short:** connect data → harmonize it → unify it → analyze it → act on it to deliver smarter, more personalized experiences.

### Data Cloud Lifecycle

![alt text](img/dc_lifecycle.png)

## Data Cloud Setup and Administration

### Data Cloud Tenant Endpoint

* https://developer.salesforce.com/agentforce-workshop/data-cloud/1-ingest-crm-contacts
* Self-Service Workshop Setup
* Quick Start: Explore the Coral Cloud Sample App
* Deploy the Coral Cloud Sample App / Sign Up
* Create playground
* Verify email
* Click link to Reset password

![alt text](img/seller_home.png)

* Data Cloud Setup

![alt text](img/datacloud_setup.png)

* Quick find: Salesforce CRM

![alt text](img/salesforce_crm.png)

### Load Data into Contact Object

* In the URL remove from /lightnin until end
* Install package 1

![alt text](img/install_package1.png)

  * /packaging/installPackage.apexp?p0=04tWx0000001WU5IAM
  * Install for All Users / Install / Yes, grant access...

![alt text](img/install_coral_cloud_base.png)<

* Sample Data Import / Import Sample Data (Import Contact Data)

![alt text](img/contacts_imported.png)

* Install package 2

![alt text](img/install_package2.png)

  * /packaging/installPackage.apexp?p0=04tHr000000ku4k
  * Install for Admins Only / Install

![alt text](img/install_package2_completed.png)

### Data Streams

![alt text](img/data_stream1.png)
![alt text](img/data_stream2.png)

### Create new Data Stream

* Data Streams / New / Salesforce CRM
* EPIC OrgFarm / Custom Data Bundle 

![alt text](img/salesforce_contacts.png)

* Select fields / Next / Deploy
* Contact_Home will be create

![alt text](img/contact_home.png)

![alt text](img/datalake_object.png)

* Data Streams / Contact_Home / Review

![alt text](img/conrtacthome_mapping.png)

* Contact_Home Mappings / Save
* Data Explorer / Object - Data Lake Object - Contact_Home

![alt text](img/datamodelobjects_mapped.png)

![alt text](img/dataexplorer_objects.png)

## Data Ingestion and Modeling
### Data Space

Permission Set Data Space Management
* Clic on Config (Engine icon)
* Home / Quick Find: Permission Sets
* Access Agentforce Default Agent
* Data Cloud Data Space Management

![alt text](img/permission-set-data-space.png)

### Data Explorer and Query Editor

* Data Explorer
* Object: Data Lake Object
* Contact Home

![alt text](img/data-explorer1.png)
![alt text](img/edit_columns.png)
![alt text](img/data_explorer2.png)

Query Editor

![alt text](img/query_editor1.png)

### Upload Reservation and Contacts Records on Amazon S3

*Download access key file*
* Search: IAM
* Quick Links: My Security Credentials
* Create access key
* Check: Continue to create access key / Create access key
* Download .csv file

*Create a bucket in S3*
* Search: S3
* Create bucket
* General purpose
* Bucket name: mydatacloudbucketcj
* Create bucket

![alt text](img/bucket1.png)

* Create a folder: contactandhotelbookings
* Create folder

![alt text](img/folder1.png)

* Upload (Coral_Clouds_Guests.csv, Coral_Clouds_Hotel_Reservations.csv)

![alt text](img/upload.png)

![alt text](img/upload1.png)
* Destination: `s3://mydatacloudbucketcj/contactandhotelbookings/`

### Create Connection between Amazon S3 and Data Cloud

#### Connect Salesforce with Amazon S3
* Setup / Home / Data Cloud / External Integrations / Other Connectors
* New / Amazon S3

![alt text](img/conn1.png)

* Connection Name:  AmazonS3
* Connection API Name:  AmazonS3
* Provide `AWS access` key and `AWS secret access key`
* Bucket name: `mydatacloudbucketcj`
* Parent directory: `contactandhotelbookings`
* Test Connection / Save

![alt text](img/testconnection.png)
![alt text](img/connectors.png)

#### Create New Data Stream to get information from Amazon S3

* Data Cloud / Data Streams / New
* Amazon S3 / Next
* New Data Stream / Connection: AmazonS3 / File Name: `Coral_Clouds_Guests.csv` / Next

![alt text](img/ds1.png)

* Data Lake Object Label: `Guest` / Data Lake Object API Name: `Guest`
* Properties
  * Category: `Profile`
  * Primary key: `Guest Id`
* In supported Fields: Adjust Data Type is needed