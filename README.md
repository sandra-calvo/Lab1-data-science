# IBM Cloud Workshop :cloud:

## Introduction 
In this guide, you will:
  - [Introduction](#introduction): 
  - [PHASE 1](#phase-1): Data Preparation using Data Refinery
  - [PHASE 2](#phase-2): Data analysis using Modeler
  - [PHASE 3](#phase-3): Create your custom machine learning model 
  - [PHASE 4](#phase-4): Deploy ML model 
  - [PHASE 5](#phase-5): Create an application that uses custom ML model 
  - [PHASE 6](#phase-6): Data science with Jupyter Notebooks in Python, R or Scala


#### Prerequisites
- IBM Cloud account
  - Create a free account www.bluemix.net

# Introduction 
--> Introduce the workshop and maybe add a picture of how Watson Studio and the other services we are going to use in this workshop fit together.

![](/images/Tools.png?raw=true)

**IBM Cloud** is a suite of cloud computing services from IBM that offers both platform as a service (PaaS) and infrastructure as a service (IaaS). 

![](/images/IBMCloud.png?raw=true)

**Watson Studio** is an integrated environment designed to make it easy to develop, train, manage models and deploy AI-powered applications. It is a solution delivered on the IBM Cloud. Watson Studio provides a suite of tools for data scientists, application developers and subject matter experts to collaboratively and easily work with data.

# PHASE 1
## Data Preparation using Data Refinery

**Data Refinery** it’s a self-service data preparation client for data scientists, data engineers, and business analysts. With it, you can quickly transform large amounts of raw data into consumable, quality information that’s ready for analytics. Data Refinery makes it easy to explore, prepare, and deliver data that people across your organization can trust.

## Step 1: Create a Watson Studio Project
Before we start with the data preparation we need to create a project in Watson Studio. In order to create a project login to Watson Studio: https://eu-gb.dataplatform.ibm.com/ 
**Notice** I am using the UK platform. 

To create a project with all tools click on the _New Project_ icon in the dashboard. 
![](/images/Picture1.png?raw=true)

Next you will see the different types of projects available in Watson Studio. For this lab we will use the _Complete_ project. Select that and click on _OK_.
![](/images/Picture2.png?raw=true)

On the New project screen, add a name and optional description for the project.
You could restric who can be a collaborator. For example, if you want to restrict the project to internal users for security reasons. In this case we don't need to apply any restrictions. 
Choose whether to restrict who you can add as a collaborators. You can't change this setting after you create the project.
![](/images/Picture3.png?raw=true)

Every project needs a Cloud Object Storage service associated. **Cloud Object Storage** is storage for the cloud. Essentially a key-value store, files (or any binary data) are given an identifying key (or name) and stored as an 'object' in a uniquely named 'bucket' or 'container'. 

Click _Add_ to connect with your existing instance or to create a new one. If you have an existing Object Storage instance select the "Existing" tab and connect with your instance. If you need to create a new Object Storage select the pricing plan, in this case Lite, the free plan, is enough. Then click on _Create_.
![](/images/Picture4.png?raw=true)

A new window will be prompted to confirm the creating of the service. Confirm the plan is Lite, resource group is default and you can edit the name of the service if you want. When you are ready click on _Confirm_.
![](/images/Picture5.png?raw=true)

Click on _Refresh_ and you will see the Cloud Object Storage service associated with the project. Click on _Create_.
![](/images/Picture6.png?raw=true)

Your project is ready! 👍

## Step 2: Add data to your project

After you create a project, you add data assets to it so that you can work with data. All the collaborators in the project are automatically authorized to access the data in the project. 
You can add data assets from these sources to legacy projects:

    Local files
    Community
    Database connections
    
In this lab we will add a simple .csv file. Download the file from this link: **BOX LINK WITH THE DATA SET**
Password will be delivered during the workshop. 

You can add a file as a data asset from your local system to your project.
From your project's _Assets_ page, click the Find and add data icon (![](/images/Icon1.png?raw=true)).
Browse the file or drag them onto the Load pane.
![](/images/Picture7.png?raw=true)

The files are saved in the object storage that is associated with your project and are listed as data assets on the Assets page of your project.

## Step 3: Data refinery

Refining data consists of cleansing and shaping it. When you cleanse data, you fix or remove data that is incorrect, incomplete, improperly formatted, or duplicated. And when you shape data, you customize it by filtering, sorting, combining or removing columns, and performing operations.

As you manipulate your data, you build a customized data flow that you can modify in real time and save for future re-use. When you save the refined data set, you typically load it to a different location than where you read it from. In this way, your source data can remain untouched by the refinement process.

SANDRA!!! --> https://dataplatform.cloud.ibm.com/docs/content/refinery/refining_data.html?audience=wdp&context=wdp&linkInPage=true

# PHASE 2
# Data analysis using Modeler
**Modele: Flow editor** You can create a machine learning flow, which is a graphical representation of a data model, or a deep learning flow, which is a graphical representation of a neural network design, by using the Flow Editor. Use it to prepare or shape data, train or deploy a model, or transform data and export it back to a database table or file.


# PHASE 3
# Create your custom machine learning model


# PHASE 4
# Deploy ML model
**IBM Watson Machine Learning** is a full-service IBM Cloud offering that makes it easy for developers and data scientists to work together to integrate predictive capabilities with their applications. The Machine Learning service is a set of REST APIs that you can call from any programming language to develop applications that make smarter decisions, solve tough problems, and improve user outcomes.

# PHASE 5
# Create an application that uses custom ML model 
**Node-RED** is a visual tool for wiring the internet of things - connecting hardware devices, APIs and online services in a new and interesting way. Node-RED provides a browser-based flow editor that makes it easy to wire together flows using the wide range nodes in the palette. Flows can be then deployed to the runtime in a single-click.


# PHASE 6
# Data science with Jupyter Notebooks in Python, R or Scala
A Jupyter notebook is a web-based environment for interactive computing. You can run small pieces of code that process your data, and you can immediately view the results of your computation. Notebooks include all of the building blocks you need to work with data:

    The data
    The code computations that process the data
    Visualizations of the results
    Text and rich media to enhance understanding
