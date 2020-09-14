# TASK DESCRIPTION :

1. Create multi projects with dev and prod

2. Create VPC network for dev project

3. Create VPC network for prod project

4. Connect both the VPC network with VPC peering

5. Create a Kubernetes Cluster in dev project and launch a wordpress/Joomla application with the Load balancer

6. Create a SQL server in prod project and create a database

7. Connect the SQL database with the application launched in the K8s cluster


# SOLUTION


# STEP 1:

Creating the infrastructure  we are creating two projects in different regions.
let One project be called Production and other one for Developer.

Creating A Project for Production 
 <img src="  ">



Creating A Project for Developer
 <img src="  ">


# STEP 2:

Within the projects we have to create VPC( Virtual Private cloud).
In one vpc we'll launch our wordpress and in other our database which is mysql.

 <img src="  ">

# STEP 3:

Since we have created both the VPC in different Regions so for making connection between them so that 
wordpress can connect to our database. These VPCs can be connected trough VPC Peering.

 <img src="  ">


# STEP 4:

For deploying our wordpress on Google Cloud PLatform we are creating a Kubernetes cluster with one of the
service of GCP known as GKE(Google Kubernetes Engine).

Now for launching wordpress on GKE, we have to connect to GKE,here i'm connecting through cloud shell provided by GCP.
Also for doing the same we can install GOOGLE Cloud SDK in our system and have to configure kubectl to control pods.

We can see the nodes og the cluster with the command

       kubectl get nodes

Now we can deploy our wordpress by creating the deployment.
  
    kubectl create deployment wordpress  --image=wordpress

For checking the running pods we can run the command

     kubectl get pods

After the deployment havebeen created, we have to expoe our deployment to connect to this wordpress site
We are using LoadBalancer as a service to expose the deployment on the port number 80.
Command

      kubectl expose deployment wordpress --type=LoadBalancer --port=80

After we exposed our deployment we require the external IP and port number to connect to wordpress site.
For this we have to run the command 

     kubectl get svc
     
     
  <img src="  ">    
     
 # Step 6:
 Now we require a database to stoe the data of the worpress for backend. Here we will use SQl service of 
 GCP, using this service we will launch mysql database in Production.
 
 We can add network to public ip to connect.
  <img src="  ">
  
  
 We can create new database in the mysql or we can use the pecreated database.
 
  <img src="  ">
  
  
 # STEP 7:
 Now using the external IP we can connect to our wordpress site, here we'll require our database details to connect our 
 wordpress to backend database.
 
 
 <img src="  ">
 
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
     
