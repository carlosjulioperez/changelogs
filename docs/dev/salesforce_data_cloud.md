- [Salesforce Data Cloud Consultant Certification](#salesforce-data-cloud-consultant-certification)
  - [Data Cloud Process Overview](#data-cloud-process-overview)
    - [Data Cloud Lifecycle](#data-cloud-lifecycle)
  - [Data Cloud Setup and Administration](#data-cloud-setup-and-administration)
    - [Data Cloud Tenant Endpoint](#data-cloud-tenant-endpoint)
    - [Load Data into Contact Object](#load-data-into-contact-object)
    - [Data Streams](#data-streams)
      - [Categories](#categories)
    - [Create new Data Stream](#create-new-data-stream)
    - [Data Normalization](#data-normalization)
      - [Normalize Denormalized Data Use Case](#normalize-denormalized-data-use-case)
    - [Data Transform](#data-transform)
  - [Data Ingestion and Modeling](#data-ingestion-and-modeling)
    - [Data Cloud Object](#data-cloud-object)
    - [Data Source Object](#data-source-object)
    - [Data Lake Object (DLO)](#data-lake-object-dlo)
    - [Data Model Object (DMO)](#data-model-object-dmo)
    - [Key Takeaways](#key-takeaways)
    - [Customer 360 Data Model](#customer-360-data-model)
    - [Data Space](#data-space)
      - [How Data Space Work?](#how-data-space-work)
      - [Use Case for Data Spaces](#use-case-for-data-spaces)
    - [Permission Set Data Space Management](#permission-set-data-space-management)
    - [Data Explorer and Query Editor](#data-explorer-and-query-editor)
    - [Upload Reservation and Contacts Records on Amazon S3](#upload-reservation-and-contacts-records-on-amazon-s3)
    - [Create Connection between Amazon S3 and Data Cloud](#create-connection-between-amazon-s3-and-data-cloud)
    - [Create New Data Stream to get Gest information from Amazon S3](#create-new-data-stream-to-get-gest-information-from-amazon-s3)
    - [Create New Data Stream to get Reservation information from Amazon S3](#create-new-data-stream-to-get-reservation-information-from-amazon-s3)
    - [Mapping to Guest DLO to Individual DMO](#mapping-to-guest-dlo-to-individual-dmo)
    - [Mapping to Reservation DLO to Reservation DMO](#mapping-to-reservation-dlo-to-reservation-dmo)
      - [Duplicate records](#duplicate-records)
  - [Identity Resolution](#identity-resolution)

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

* https://trailhead.salesforce.com
* Search: Quick Start: Explore the Coral Cloud Sample App
* Deploy the Coral Cloud Sample App / Sign Up
* This Badge Requires a New Custom Data Cloud Playground...
* Create Playground
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

#### Categories
![alt text](img/data_stream03.png)
![alt text](img/data_stream04.png)
![alt text](img/data_stream05.png)
![alt text](img/data_stream06.png)

### Create new Data Stream

* Data Cloud / Data Streams / New / Salesforce CRM / Next
* EPIC OrgFarm / Custom Bundles (1) / Salesforce_Contacts

![alt text](img/salesforce_contacts.png)

* Select fields / Next / Deploy
* Contact_Home will be create

![alt text](img/contact_home.png)

![alt text](img/datalake_object.png)

* Data Streams / Contact_Home / Review

![alt text](img/conrtacthome_mapping.png)

* Contact_Home Mappings / Save

![alt text](img/datamodelobjects_mapped.png)

* Data Explorer / Object - Data Lake Object - Contact_Home

![alt text](img/dataexplorer_objects.png)

### Data Normalization
![alt text](img/dc10.png)

#### Normalize Denormalized Data Use Case
* In this use case, the data comes from a single Marketing Cloud Engagement data extension but must be normalized to map to the Data 360 data model objects (DMO).
* The source data has two email addresses and two phone numbers for a customer. However, in the Data 360 data model, you can map only one email address and one phone number to the individual DMO. To retain the customer’s additional contact details, you normalize the contact point data before ingesting it.

![alt text](img/dc11.png)

To normalize the data, divide the data into three tables that can map to the Individual DMO, Contact Point Email DMO, and Contact Point Phone DMO and define the relationship between them.

![alt text](img/dc12.png)

* When mapping data to a DMO, each record requires a primary key that uniquely identifies it across all the data sources.
* To map attributes to the Contact Point Email and Contact Point Phone DMO, you need more than the Contact Id value, because you’re ingesting multiple email addresses and phone numbers for a single Contact Id. Therefore, you extend the data at ingestion through the use of formula fields and generate primary keys.
* To map to the Contact Point Phone DMO, create a primary key CP_Phone_Id using a composite key by concatenating the Contact Id and Phone Number fields. This primary key is a representative example of how primary keys can be generated at ingestion time using formula fields.

![alt text](img/dc13.png)

* Similarly, to map to the Contact Point Email DMO, create a primary key CP_Email_Id using a composite key by concatenating the Contact Id and Email Address fields.

![alt text](img/dc14.png)

### Data Transform

![alt text](img/dc15.png)

## Data Ingestion and Modeling

![alt text](img/dc16.png)

### Data Cloud Object
![alt text](img/dc01.png)

### Data Source Object
![alt text](img/dc02.png)

### Data Lake Object (DLO)
![alt text](img/dc03.png)

### Data Model Object (DMO)
![alt text](img/dc04.png)

### Key Takeaways
![alt text](img/dc05.png)

### Customer 360 Data Model
![alt text](img/dc06.png)

### Data Space
![alt text](img/dc07.png)

#### How Data Space Work?
![alt text](img/dc08.png)

#### Use Case for Data Spaces
![alt text](img/dc09.png)

### Permission Set Data Space Management
* Setup / Clic on Config (Engine icon)
* Home / Quick Find: Permission Sets
* Access Agentforce Default Agent
* Click on: Data Cloud Data Space Management

![alt text](img/permission-set-data-space.png)

### Data Explorer and Query Editor

* Data Explorer
* Object: Data Lake Object
* Contact Home

![alt text](img/data-explorer1.png)
  * Columns: Contact ID, Full Name, Email, Birthdate, Business Phone, Created Date, Data Source, Photo URL, Home Phone
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

![alt text](img/conn01.png)
![alt text](img/conn02.png)
![alt text](img/conn03.png)

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

### Create New Data Stream to get Gest information from Amazon S3
* Data Cloud / Data Streams / New
* Amazon S3 / Next
* New Data Stream / Connection: AmazonS3 / File Name: `Coral_Clouds_Guests.csv` / Next

![alt text](img/ds1.png)

* Data Lake Object Label: `Guest` / Data Lake Object API Name: `Guest`
* Properties
  * Category: `Profile` (represents an individual like Account or other profile used for segmentation and analytics)
  * Primary key: `Guest Id`
* In Supported Fields: Adjust Data Type is needed / Next

![alt text](img/ds2.png)

* Full Refresh / Deploy

![alt text](img/ds3.png)

* Deploying Guest

![alt text](img/ds4.png)

### Create New Data Stream to get Reservation information from Amazon S3

* Data Cloud / Data Streams / New
* Amazon S3 / Next
* New Data Stream / Connection: AmazonS3 / File Name: `Coral_Clouds_Hotel_Reservations.csv` / Next

![alt text](img/ds5.png)

* Data Lake Object Label: `Reservation` / Data Lake Object API Name: `Reservation`
* Properties
  * Category: `Engagement` (contains behavioral information)
  * Event Time Field: `Check-in Date`
  * Primary key: `Reservation ID`
* In Supported Fields: `Room Number` change to `Text`, `Taxes and fees`, change to `Percent`

![alt text](img/ds6.png)

* Full Refresh / Deploy

![alt text](img/ds7.png)

* Deploying Reservation

![alt text](img/ds8.png)

![alt text](img/ds9.png)

### Mapping to Guest DLO to Individual DMO

* Data Streams / Select Guest / Start

![alt text](img/gm01.png)

* Select Object
* Standard Data Model
* Select `Individual` and `Conctact Point Email` / Done

![alt text](img/gm02.png)

![alt text](img/gm03.png)

* Mapping `Individual Id` with `Guest Id`

![alt text](img/gm04.png)

![alt text](img/gm05.png)

![alt text](img/gm06.png)

* Save
* Table View

![alt text](img/gm07.png)

* Save and Close
* Refresh Now / Refresh Only New Files / Refresh Now

![alt text](img/gm08.png)

![alt text](img/gm09.png)

### Mapping to Reservation DLO to Reservation DMO

* Data Lake Objects / Select Reservation / Start
* Select Objects / Custom Data Model / Mapping each file / Save and Close

![alt text](img/gm10.png)

![alt text](img/gm11.png)

* Data Model / Individual / Relationships

![alt text](img/gm12.png)

* Data Model / Click on icon "Display as" / Graph

![alt text](img/gm13.png)
![alt text](img/gm14.png)

* Data Streams / Reservation / Refresh Now

![alt text](img/gm15.png)
![alt text](img/gm16.png)

* Data Explorer / Data Model Object / `Individual`

![alt text](img/gm17.png)

* Click on `Data Source` column

![alt text](img/gm18.png)

* Select `Contact Point Email`, click on `Data Source` column

![alt text](img/gm19.png)

#### Duplicate records

* Data Explorer / Data Model Object / `Individual`
* Click on Filter Icon / Add Filter / Done / Apply

![alt text](img/gm20.png)
![alt text](img/gm21.png)

## Identity Resolution