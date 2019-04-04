# GCP ACE Study Questions

* Your development team has asked you to set up an external TCP load balancer with SSL offload. Which load balancer should you use?
    * SSL Proxy

* Your team uses a third-party monitoring solution. They've asked you to deploy it to all nodes in your Kubernetes Engine Cluster. What's the best way to do that?
    * Deploy the monitoring pod as a DaemonSet.
        * DaemonSets run a pod on each node in the cluster. Using a DaemonSet allows you to deploy your pod in the same way you deploy your other containers. This makes it easy to do without adding new tools.

*  You have a simple web application that you're trying to deploy in a secure and inexpensive way. The application is running inside a Docker container on port 8080. Once the application is initially deployed, the developers are going to take ownership of future deployments. What is the best option for running the application?
    * Use an App Engine Flexible Environment. 
      * Flexible environments are able to use a Dockerfile to create custom runtimes. They specifically run on port 8080.

* You have a Cloud Storage bucket that needs to host static web assets. How do you make the bucket public? 
  * Set allUsers to have the Storage Object Viewer role. 

* You've created the code for a Cloud Function that will respond to HTTP triggers and return some data in JSON format. You have the code locally, it's tested and working. Which command can you use to create the function inside Google Cloud? 
  * gcloud functions deploy
    * This command creates and deploys.

*  Your team has some new functionality that they want to roll out slowly so they can monitor for errors. The change contains some significant changes to the user interface. You've chosen to use traffic splitting to perform a canary deployment. You're going to start by rolling out the code to 15% of your users. How should you go about setting up traffic splitting?
   * Deploy the new version using the no-promote flag. Split the traffic using distribution.
     * Cookie-based will allow for a level of persistence so if a user reloads the page, they'll see the version they're supposed to. By default deploying a new application it becomes promoted.

*  You're trying to provide temporary access to some files in a Cloud Storage bucket. You want to limit the time that the files are available to 10 minutes. With the fewest steps possible, what is the best way to generate a signed URL?
    * Create a service account and JSON key. Use the gsutil signurl -d 10m command and pass in the JSON key and bucket. 

* You're trying to create a new Compute Engine instance with the Cloud SDK using the create command from the compute group and the instances sub-group. You've forgotten some of the flags and want to look them up using the man pages. Which command will display the documentation you need?
    * man gcloud_compute_instances_create


*  You've installed the Cloud SDK natively on your Mac. You'd like to install the kubectl component. Which command would accomplish this?
    * gcloud components install kubectl

*  What are some of languages the App Engine Standard Environment supports? (Choose all that apply)
    * Python, Go, PHP

* What is the retrieval time of ColdLine and NearLine storage
  * All retrieval time for GCP Storage is the same being near instant

*  When would you want to use Kubernetes Engine over App Engine? Choose two answers.
    * Need to use protocols beyond HTTP/S 
    * Hybrid or multi-cloud development 

* Separate access of recources
  * VPCs

* Separate access of users
  * Projects

* Kubernetes change the machine type
  * Create new node pool in same cluster, migrate workload to new pool

* Snapshots cannot be shared across projects
  * Turn snapshot into a custom image to use in different projects

* Allow acces to a GCE instance
  * Project's project number
  * Email address of project service account

* Allow GCE instance to access other services
  * Grant service account access to required resources
  * Access the token via the metadata service

* GCE instances default scopes allow reading from GCS, for one project bucket to read from another grant the bucket read access

* Compute Engine Start-Up Procedure
  * OS starts booting
  * Instance considered running
  * Gcloud them complete (unless ran with --async)
  * Metadata service will provide startup script to OS boot process
  * Gsutil command gets metadata like service account token
  * Stackdriver will have a chance to push logs
  * Startup script completes and more logs will be pushed to Stackdriver Logging

* GKE nodes are GCE instances, if one dies GKE will bring another node to replace it

* GCPs global by default and only individual resources live in certain location
    so when creating a bucket you can specify region during creation then not again

* App Engine Standard logging should be using the APpp Engine SDK, Stacdriver installation is configured automatically

* GCE logging should be sending logs to file, install StackDriver agent on VM, configure Stackdriver to monitor and push log file

* Allowed as many projects as based on your quota

* Gcloud predefines machine types named by their CPU counts in powers of 2

* Cloud Bigtable is most performant product for IoT and time series data

* MySQL database point-in-time recover use Binary Logging

* Extract IP address of Kubernetes Service: kubectl get svc -o jsonpath='{.items[*].status.loadBalancer.ingress[0].ip}'

* Enable CORS on bucket: gsutil cors set

* Stackdriver custom metric: create custom logging metric using regex to extract into a label

* Gcloud compute instances store the SSH keys in the metadata so to add: `gcloud compute project-info add-metadata`

* Each sink destination has it's own time window for saving data so may take a while to persist

* Allow COmpute Engine instance to make cals to Cloud Storage and Big Table
  * Use default Compute Engine service acount and set scopes, code find service account using 'ApplicationDefault Credentials'

* gcloud info shows details about components, libraries, system details, and the log directory

* To use alpha command install the alpha component

