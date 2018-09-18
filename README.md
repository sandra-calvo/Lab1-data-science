# IBM Cloud Workshop :cloud:

## Introduction 
In this guide:
  - [Overview](#overview)
  - [Introduction](#introduction)
  - [PHASE 1](#phase-1): Data Preparation using Data Refinery
  - [PHASE 2](#phase-2): Data analysis using Modeler
  - [PHASE 3](#phase-3): Create your custom machine learning model 
  - [PHASE 4](#phase-4): Deploy ML model 
  - [PHASE 5](#phase-5): OPTIONAL - Data science with Jupyter Notebooks in Python, R or Scala


#### Prerequisites
- IBM Cloud account
  - Create a free account www.bluemix.net
  
# Overview 

The purpose of this lab is to guide the user in the data science life cycle from raw data to an application with a machine learning model. All this using IBM Cloud tools. 

**Part 1:** Data science and data analytics part using Watson Studio, Cloud Object Storage and Watson Machine Learning services. https://github.com/sandra-calvo/Lab1-data-science

**Part 2:** Application development section using Node-RED and Watson Assistant services to connect a web application with the machine learning model deployed in Part 1. https://github.com/sandra-calvo/Lab2-application-development

# Introduction 
The purpose of this lab is to guide the user in the data science life cycle from raw data to an application with a machine learning model. All this using IBM Cloud tools. 

**IBM Cloud** is a suite of cloud computing services from IBM that offers both platform as a service (PaaS) and infrastructure as a service (IaaS). 

<img src="/images/IBMCloud.png" width="90%" height="90%">

**Watson Studio** is an integrated environment designed to make it easy to develop, train, manage models and deploy AI-powered applications. It is a solution delivered on the IBM Cloud. Watson Studio provides a suite of tools for data scientists, application developers and subject matter experts to collaboratively and easily work with data.

![](/images/Tools.png?raw=true)

In the picture above you can see the collection of IBM Cloud tools we are going to use in this workshop:

      - Watson Studio  - Data science, ML
      - Cloud Object Storage -  Storage
      - Watson Machine Learning - ML Model deployment
      - Node-RED - Application logic
      - Watson Assistant - Bot service integration 


# PHASE 1
## Data Preparation using Data Refinery

**Data Refinery** it’s a self-service data preparation client for data scientists, data engineers, and business analysts. With it, you can quickly transform large amounts of raw data into consumable, quality information that’s ready for analytics. Data Refinery makes it easy to explore, prepare, and deliver data that people across your organization can trust.

### Step 1: Create a Watson Studio Project
Before we start with the data preparation we need to create a project in Watson Studio. In order to create a project login to Watson Studio: https://eu-gb.dataplatform.ibm.com/ 

To create a project with all tools click on the _New Project_ icon in the dashboard. 
![](/images/Picture1.png?raw=true)

Next you will see the different types of projects available in Watson Studio. For this lab we will use the _Complete_ project. Select that and click on _OK_.

<img src="/images/Picture2.png" width="60%" height="60%">

On the New project screen, add a name and optional description for the project.
You could restric who can be a collaborator. For example, if you want to restrict the project to internal users for security reasons. In this case we don't need to apply any restrictions. 
Choose whether to restrict who you can add as a collaborators. You can't change this setting after you create the project.

<img src="/images/Picture3.png" width="80%" height="80%">

Every project needs a Cloud Object Storage service associated. **Cloud Object Storage** is storage for the cloud. Essentially a key-value store, files (or any binary data) are given an identifying key (or name) and stored as an 'object' in a uniquely named 'bucket' or 'container'. 

Click _Add_ to connect with your existing instance or to create a new one. If you have an existing Object Storage instance select the "Existing" tab and connect with your instance. If you need to create a new Object Storage select the pricing plan, in this case Lite, the free plan, is enough. Then click on _Create_.

<img src="/images/Picture4.png" width="80%" height="80%">

A new window will be prompted to confirm the creating of the service. Confirm the plan is Lite, resource group is default and you can edit the name of the service if you want. When you are ready click on _Confirm_.

<img src="/images/Picture5.png" width="50%" height="50%">

Click on _Refresh_ and you will see the Cloud Object Storage service associated with the project. Click on _Create_.
![](/images/Picture6.png?raw=true)

Your project is ready! 👍

### Step 2: Add data to your project

After you create a project, you add data assets to it so that you can work with data. All the collaborators in the project are automatically authorized to access the data in the project. 
You can add data assets from these sources to legacy projects:

    Local files
    Community
    Database connections
    
In this lab we will add a simple .csv file from our local collection. Download the file from this link: **BOX LINK WITH THE DATA SET** Password will be delivered during the workshop. 

From your project's _Assets_ page, click the Find and add data icon (<img src="/images/Icon1.png" width="3%" height="3%">).

Browse the file or drag them onto the Load pane.
![](/images/Picture7.png?raw=true)

The files are saved in the object storage that is associated with your project and are listed as data assets on the Assets page of your project.

### Step 3: Data refinery

Refining data consists of cleansing and shaping it. When you cleanse data, you fix or remove data that is incorrect, incomplete, improperly formatted, or duplicated. And when you shape data, you customize it by filtering, sorting, combining or removing columns, and performing operations.

As you manipulate your data, you build a customized data flow that you can modify in real time and save for future re-use. When you save the refined data set, you typically load it to a different location than where you read it from. In this way, your source data can remain untouched by the refinement process.

If you want to be able to save refined data to cloud or on-premises data sources, create connections for this purpose. Source connections can only be used to read data; target connections can only be used to load (save) data. 

In this lab we will create a new .csv file with our refined data set. 

Open Data Refinery by clicking Tools > Data Refinery.

<img src="/images/DR1.png" width="30%" height="30%">

Select the project you want to work in and then click _Select Data_ to select the data you want to work with.

<img src="/images/DR2.png" width="100%" height="100%">

On the Data tab, apply operations to cleanse, shape, and enrich your data. You can enter R code in the command line and let autocomplete assist you in getting the syntax right. Or you can use the Operations menu to browse operation categories or search for a specific operation, then let the UI guide you.

<img src="/images/DR3.png" width="30%" height="30%">

**--> OPERATIONS TO THE SAMPLE DATA DESCRIBED**

Validate your data throughout the data refinement process.
Use visualizations to gain insights into your data and to uncover patterns, trends, and correlations within your data.

When you've refined the sample data set to suit your needs, click the _Run data flow_ icon in the toolbar to run the data flow on the entire data set.

By default, Data Refinery uses the name of the data source to name the data flow and the target data set. You can change these names, but you can't change the project that these data assets belong to.

a. In the Data flow details pane, optionally edit the name of the data flow and enter a description for it. You can also add a one-time or repeating schedule for the data flow.

b. In the Data flow output pane, optionally edit the name of the target data set and enter a description for it. You can save the target data set to the project, to a connection, or to a connected data asset . If you save it to the project, you can save it as a new data asset (by default) or you can replace an existing data asset. To save the target data set to a connection or as a connected data asset or to replace an existing data asset, use Change Location.

Click _Save and Run_.

**SANDRA** https://dataplatform.cloud.ibm.com/docs/content/refinery/refining_data.html?context=analytics&linkInPage=true

# PHASE 2
## Data analysis using Modeler
**Modele: Flow editor** You can create a machine learning flow, which is a graphical representation of a data model, or a deep learning flow, which is a graphical representation of a neural network design, by using the Flow Editor. Use it to prepare or shape data, train or deploy a model, or transform data and export it back to a database table or file.

### Step 4: 

### Step 5:

# PHASE 3
## Create your custom machine learning model

### Step 6:

# PHASE 4
## Deploy ML model
**IBM Watson Machine Learning** is a full-service IBM Cloud offering that makes it easy for developers and data scientists to work together to integrate predictive capabilities with their applications. The Machine Learning service is a set of REST APIs that you can call from any programming language to develop applications that make smarter decisions, solve tough problems, and improve user outcomes.

### Step 7: Create a Watson machine learing service

To design, train, and deploy machine learning models in IBM Watson Studio, you need to associate an IBM Watson Machine Learning service instance, as well as some supporting services (such as IBM Cloud Object Storage), with a project.

Services are added in the _Settings_ page of your project in Watson Studio.

<img src="/images/Model1.png" width="70%" height="70%">

Click _Add service_ under Associated Services and choose Watson.

<img src="/images/Model2.png" width="100%" height="100%">

Select Watson Machine Learning from the Catalog and click _Add_.

<img src="/images/Model3.png" width="100%" height="100%">

If you already have a service created in IBM Cloud you can connect that to your project in the _Existing_ tab. In this case we are going to create a new machine learning instance. 
Select the Lite plan, for this workshop the free plan will be enough. Then click on _Create_.

<img src="/images/Model4.png" width="100%" height="100%">

You will need to confirm the creation of the service. In this step it is possible to change the name of the service. Feel free to edit the name and then click on _Confirm_.

<img src="/images/Model5.png" width="50%" height="50%">

Great! You created a Watson Machine Learning service and associated it with your Watson Studio project. In the list of services connected to the project you should see now Watson machine learning. 

<img src="/images/Model6.png" width="70%" height="70%">

### Step 8: Deploy the ML model

### Step 9: Test the ML model

# PHASE 5
## OPTIONAL - Data science with Jupyter Notebooks in Python, R or Scala
A Jupyter notebook is a web-based environment for interactive computing. You can run small pieces of code that process your data, and you can immediately view the results of your computation. Notebooks include all of the building blocks you need to work with data:

    The data
    The code computations that process the data
    Visualizations of the results
    Text and rich media to enhance understanding
