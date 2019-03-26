# GCP Linux Academy

### Setting Up Cloud Projects and Accounts

#### Projects

* Everything in GCP is encapsulated in a project
* A project can be associated to an organization
  * Will allow project to live past life of user account
* Project info
  * Project name - self assigned not globally unique
  * Project ID - self or automatically assigned must be globally unique
  * Project number - automatically assigned globally unique identifier

#### IAM (Identity Access Management) & Admin

* Users must be associated with Google
  * Gmail
  * Google Groups
  * Service Accounts
  * G Suite
  * Cloud Identity
  * GCDS (Google Cloud Directory Sync) to link with AD or LDAP
* Roles
  * Primitive Roles: predate IAM and project level roles - really basic and not recommended
    * Project Owner
    * Project Editor
    * Project Viewer
  * Predefined Roles: target specific use cases and precreated
  * Custom Roles: must be created manually

#### Stackdriver

* Stackdriver was acquired by Google and implemented into Google Cloud in 2015
* Uptime monitoring, Performace Metrics, Alerting, AWS monitoring
* Services: Monitoring, Debug, Trace, Logging, Error Reporting, Profiler
* Monitoring
  * Must install driver on VMs to enable monitoring
* Alerting
  * Can be based on conditions and multiple notification methods (SMS, Slack, HipChat, etc...)
  * Documentation: can send documentation with a specific problem to help fix the issue
* Groups
  * monitor multiple applications as under one group
* Dashboard
  * view metrics
* Stackdriver APM (Application Performance Management)
  * Debug allows debugging on live application without affecting users
  * Trace finds performance bottlenecks
  * Logging centralizes logs of all apps
  * Error reporting pulls all errors out of logs in one place
* Stackdriver Host Project
  * If setting up Stackdriver for one project use that project specifically
  * If setting up Stackdriver for multiple projects create custom Stackdriver project


### Managing Billing and Configuration

#### Billing Accounts

* Billing Accounts can be attached to multiple projects
* Best Practice is to have separate billing accounts for each department or project
* Types of Billing Accounts
  * Self-server
    * billed at threshold or monthly (30 days)
  * Invoiced
    * billed monthly
    * check or wire transfer payment
    * contact Google Cloud to set up
* Different IAM Access for billing access
  * Billing Admin
    * owner role to management payment details, link/unlink project, assign billing roles
  * Billing User
    * unlink/link project from billing account
  * Billing Viewer
    * look at spending data

#### Billing Budgets and Alerts

* Can be based on project or billing account
* Send notifications to Pub/Sub

#### Billing Exports

* Export Types
  * Big Query
    * more detailed
    * allows Big Query for analyzing
  * File Export
    * saved to json or csv each day


### Cloud SDK

#### Cloud Servers

* Allow up to 6 servers
* Can specify region and OS
* Default login credentials - user 123456

#### Cloud SDK

* <a href="#">Installation Docs</a>
* Initial steps
  * gcloud init
  * link to browser to associate account

#### Using the Cloud SDK

* Components
  * gcloud - Tools
    * alpha
    * beta
  * bq - Big Query
  * gsutil
  * core
* --help: flag shows help
* man -k gcloud: shows all man pages for gcloud


### Planning and Configuration

#### Compute Resources

* App Engine
  * Web applications, web backend
  * Use Cases
    * Value deployment over Ops
    * High availability
    * App portability not a concern
    * Application HTTP based
    * Underlying OS not important
* Cloud Functions
  * Javascript code in response to events
  * Use Cases
    * Code to execute cloud events
    * Javascript development
    * Code executes within 540 seconds
    * Underlying OS not important
* Kubernetes Engine
  * Run containerized applications
  * Use Cases
    * Containerized workloads
    * Containers more important than OS
    * Application portability important
    * Container focused unit of deployment
* Compute Engine
  * Virtual machine service
  * Use Cases
    * OS control
    * Specify CPU, GPU, SSD, RAM
    * Lift-and-shift existing application
    * Bulk processing and require preemptive instances

#### Compute Engine

* Machine Types
  * Standard: balance between CPU and Memory
  * High Memory
  * High CPU
  * Shared-core
  * Memory Optimized
  * Custom
* Metadata
  * Project: http://metadata.google.internal/computeMetadata/v1/project
  * Instance: http://metadata.google.internal/computeMetadata/v1/instance

#### Autoscaling with Managed Instance Groups

* Managed Instance Groups
  * Template based autoscaling based on metrics (CPU, HTTP, Stackdriver)
  * Uses identical template to scale
  * Great for stateless applications
* Unmanaged Instance Groups
  * Don't require template
  * Use existing instancs with different configs
  * Don't support autoscaling

#### Kubernetes Engine

* Kubernetes
  * Cluster: Made up of many pods (services)
* Kubernetes Engine
  * GCP managed way to run Kubernetes
* Reasons to use Kubernetes Engine
  * High level of application portability
  * Avoid development and production discrepancies
  * Help migrate from on-premise to cloud
* Master Zone vs Region
  * zone subject to outage
  * region more resilient and thus more expensive

#### App Engine

* Standard Environment
  * Specific Runtimes: Python 2.7, Java 7 & 8, Node.js 8, PHP 5.5, Go 1.6 & 1.8 & 1.9
  * No custom runtimes, 3rd party binaries, writing to disk, ssh
  * Inexpensive
  * Fast start-up
* Flexible Environments
  * Managed runtimes
  * Customizable w/ Dockerfile

### Planning and Configuring Data Storage Options

* Cloud Storage
  * Highly available and durable object store
  * Objects are immutable but overwritable
  * Signed URLs available for time based access
  * Can host static website
  * Durability for all classes 99.99999999%
  * Storage Classes
    * Multi-Regional
      * Frequently accessed
      * Geo-reduntant
      * 99.95% SLA
      * Common Use: content storage and delivery, business continuity
      * Application Types: video, multimedia, business continuity
    * Regional
      * Accessed frequently within region
      * regional, redundant, across AZs
      * 99.9% SLA
      * Common Uses: store data and run analytics within region
      * Aplication Types: transcoding, data analytics, compute intensive data processing
    * Nearline
      * Data accessed less than once a month
      * regional
      * 99% SLA
      * Common Uses: store infrequently accessed content
      * Application Types: backup long-tail content, rarely accessed docs
    * Coldline
      * Accessed less than once a year
      * Regional
      * 99% SLA
      * Common Uses: archive storage, backup & recovery
      * Appliaction Types: archive source file backup, disaster recovery
* Big Table
  * designed for scalability and durability
  * Meant for massive amounts of data (pentabytes)
  * Only pay for streaming updates and reads
    * Check amount of reads for pay by using query validator, --dry-run, or dry-run = True
* Cloud SQL
  * Data is relational and horizontal scaling not needed
  * Patches, OS updates, etc... are automatic
* Cloud Spanner
  * Modern day database for the cloud
  * Globally distributed, strongly consistent, highly available, secure (emcrypted at rest and transit), familiar
* Cloud Datastore
  * Web & Mobile for less complex queiries
  * Fully managed no SQL built on Big Table
  * Lookup by key strong consistency
  * Lookup by query eventual consistency
* Cloud Firestore
  * Mobile application usage

#### Networking Options

* VPCs
  * Two Types
    * Auto
      * Automatically create subnets in each region
    * Custom
      * Create subnet manually by controlling IP Range
  * By default has routes to connect internally and externally
  * Firewall rules allowed
* Load Balancing
  * Uses over 80 worldwide locations
  * HTTP TCP and UDP accessible
* Cloud DNS
  * Scalabale, reliable, managed authoritative DNS

### Practical Exercise

#### Reviewing the Codebase

* <a href="https://github.com/whelmed/la-ace-find-seller">LA Ace Find Seller</a>

#### Service Accounts

* Special accounts for services and code

#### App Engine

* One per project
* Can't delete only disable
* Can't change region upon creation

### Managing Services

#### Gcloud configurations

* Can have multiple configurations for each project

        gcloud config configurations create config-name
        gcloud config configurations list
        gcloud config configurations activate config-name
        gcloud config set account user@email.com

#### Managing Compute Engine

* Available GPU types vary my zone
* Firewall rule must be created to allow SSH
* Use network tagging to add firewall rules effeciently
* SSH via CLI using gcloud tool

        gcloud compute instances list #list all compute instances
        gcloud compute ssh ben@development-server #user@nameofserver

* Must create an ssh key to use third party ssh
* Creating snapshot on CLI

        gcloud snapshots list #list all snapshots
        gcloud compute disks list #list all disks
        gcloud compute disks snapshot disk-name #take a snapshot

* Can create instance using snapshot

#### Managing Kubernetes Engine

* Resize a cluster
  * GUI cluster -> edit -> # of instances
* List all container clusters

        gcloud container clusters list

* CLI resize cluster

        gcloud container cluster resize --size=1 --zone=us-central-b cluster name

* kubectl commands

        kubectl get         #get list of resource (ex nodes)
        kubectl describe    #info about specific resource
        kubectl logs        #
        kubectl exec        #flag with -it to run cli command
        kubectl run         #creates new deployment
        kubectl delete      #deletes deployment

#### Managing App Engine Resources

* Traffic splitting
  * default behavior sets 100 percent of traffic to new version
  * CLI split traffic set version followed by percent in decimal of traffic
    ```gcloud app services set-traffic default -splits={version}=.5,{version}=.5```
  * GUI split traffic
    * versioning -> split traffic
    * IP address saves IP info of end user and redirect to same version, also cookie or random
* Scaling
  * Automatic - creates based on several factors (request rate, instance metrics, etc...) metrics can be set
  * Manual - set scaling yourself
  * Basic Scaling - standard environment only

#### Managing Cloud Storage

* CLI commands

        gsutil list #list storage
        gsutil mb -c {storage class regional|multi-regional|nearline|coldline} -l {region-name} gs://bucket-name/
        gsutil lifecycle set lifecycle.json gs://bucket-to-apply
        gsutil cp source gs://storage-bucket #copy file
        gsutil mv gs://source-bucket gs://destination-bucket
        gsutil signurl -d {time-limit-to-expire|3m} key.json gs://file-to-allow-access

* Lifecycle conditions allows delete or change storage class
  * Options
    * age of object
    * all objects created before specific date
    * check if object is live
    * matches storage class
    * numberofnewerversions
* Signed URLs
  * need service account and key

#### Managing Networking Resources

* CIDR notation for subnets
* Google does not charge for reserved IP address if being used

#### Monitoring and Logging - Stackdriver

* Alerting Policy - one or more conditions, one or more notifications, documentation optional
* Stackdriver metrics agent - install on instances to consolidate logging
* Metrics Explorer
  * Custom logging metric allows to filter logs, extract data, and present
* Log syncs allow logs to exporet to big-data, pub-sub, etc...

#### Managing Audit Logs

* Log who makes changes to project
* Simple way to filter out the logs for the project changes
* Logging CLI ```gcloud logging read```


### Domain Objectives

* Setting up cloud projects and accounts
* Managing billing configuration
* Installing and configuraing Cloud SDK (CLI)

* Planning and estimating GCP with Pricing Calculator
* Planning and configuring data storage options
* Planning and configuring network resources

* Deploying and implementing Compute Enging resources
* Deploying and implementing Kubernetes Engine resources
* Deploying and implementing App Engine and Cloud Functions
* Deploying and implementing data solutions
* Deploying and implementing network resources
* Deploying a solution using Cloud Launcher
* Deploying an application using Deployment Manager

* Managing App Engine resources
* Managing data solutions
* Managing network solutions
* Monitoring and logging

* Managing IAM
* Managing service accounts
* Viewing audit logs