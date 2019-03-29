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

* 