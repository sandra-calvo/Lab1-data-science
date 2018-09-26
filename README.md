# IBM Cloud Workshop :cloud:

## Introduction 
In this guide:
  - [Overview](#overview)
  - [Introduction](#introduction)
  - [PHASE 1](#phase-1): Data Preparation using Data Refinery
  - [PHASE 2](#phase-2): Data analysis & create a custom model using Modeler
  - [PHASE 3](#phase-3): Deploy ML model using Watson Machine Learning
  - [PHASE 4](#phase-4): OPTIONAL - Data science with Jupyter Notebooks in Python, R or Scala


#### Prerequisites
- IBM Cloud account
  - Create a free account www.bluemix.net
  
- Download the contents of the Box folder: https://ibm.box.com/v/workshop260918 
  - Password will be delivered during the workshop.
  
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
    
In this lab we will add a simple .csv file from our local collection. 
From the downloaded file's we are using the .csv file named **"Watson_Studio-sample_data.csv"**.

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

<img src="/images/DR2.png" width="70%" height="70%">

On the Data tab, apply operations to cleanse, shape, and enrich your data. You can enter R code in the command line and let autocomplete assist you in getting the syntax right. Or you can use the Operations menu to browse operation categories or search for a specific operation, then let the UI guide you.

<img src="/images/DR3.png" width="30%" height="30%">

In this case we are simply going to change the name of the columns in our data set. So click on the pen icon in each column and change the names to: 
  - punctuality 
  - period
  - month
  - acregs
  - BKDPAX
  - Fridays
  - temp_under4C
  - visibility_under550
  - snowDepth_over_ 10cm
  - flights
  
Please, do not change the names of the columns to anything else than the names above. Otherwise you will need to do several changes in the next steps and in the application development part. 

Confirm that the first column, puntuality, is using a dot as a decimal separator and not a comma. If you are using Excel in Finnish it will automatically use comma.  If your data set has a comma as decimal separator click on _Operation_ button and then replace substring and change the "," for ".".

On the right side you will see all the steps and refinements done to your data set. 

When you've refined the sample data set to suit your needs, click the _Run data flow_ (PLAY) icon in the toolbar to run the data flow on the entire data set.

<img src="/images/DR4.png" width="80%" height="80%">

By default, Data Refinery uses the name of the data source to name the data flow and the target data set. You can change these names, but you can't change the project that these data assets belong to.
In this case the data refinery will add the word "shaped" to our original file name. 

Click _Save and Run_.

Then click on View Flow to see your data refinery flows. Note that it is possible to schedule processes.

Your data is ready! Let's go back to the project view. 

# PHASE 2
## Data analysis & create a custom model using Modeler
**Modeler Flow editor** You can create a machine learning flow, which is a graphical representation of a data model, or a deep learning flow, which is a graphical representation of a neural network design, by using the Flow Editor. Use it to prepare or shape data, train or deploy a model, or transform data and export it back to a database table or file.

### Step 4: Create a modeler flow and import the stream
Create a machine learning flow to build your model. You can create a new flow or import an existing SPSS Modeler stream file.
From the toolbar for Watson Studio, click _Tools_ and then click _Modeler_.

<img src="/images/Modeler1.png" width="30%" height="30%">

In this case we are importing an existing file to save time, so select the _From File_ tab and import the file **Punctuality_Flow.srt** located in the box foldex https://ibm.box.com/v/workshop260918 where all the inputs of the workshop are stored. 

Type a name and description for your machine learning flow and select the project associated with this flow.
Select SPSS Modeler as the flow type. Select a runtime environment, such as IBM SPSS Modeler. Click _Create_.

<img src="/images/Modeler2.png" width="80%" height="80%">

### Step 5: Explore the modeler flow

After creating the flow you should see a flow like this:

<img src="/images/Modeler3.png" width="100%" height="100%">

This flow takes the data set as an input, analyses the data and also creates a custom machine learning model.
We will need to update few nodes before we run the flow. 

First node, **Data Assets**, selects the data file from our project to work in the Modeler. Double clik on the node you will be able to select the data set from your project. Click on _Change DataSet_ and select the refined data set we created in the first phase of this lab. Click _OK_ and then _Save_.

<img src="/images/Modeler4.png" width="30%" height="30%">

In this flow we have the following nodes:

Second node, **Type**, specifies field metadata and properties. In this node we configured our target variable and confirmed the type of the inputs. You can specify a measurement level (continuous, nominal, ordinal, or flag) for each field, set options for handling missing values and system nulls, set the role of a field for modeling purposes, specify field and value labels, and specify values for a field.

Double clik in the Type node and click on _Configure Types_ to see what are the types of the inputs and which is our target. 

<img src="/images/Modeler5.png" width="30%" height="30%">

_Clear all values_ then click on _Read values_. Mark "punctuality" as the target in the role column and change the measure in the month value to Categorical. Click _OK_.

<img src="/images/Modeler12.png" width="50%" height="50%">

**Statistics** node gives you basic summary information about numeric fields. You can get summary statistics for individual fields and correlations between fields.
In this case we created statistics for the whole dataset and for the winter period, using the **Select** node. You can use Select nodes to select or discard a subset of records from the data stream based on a specific condition.

**Filter** node creates filter fields that are not used by rules in the rule set. The filtering (dropping) of fields and the renaming of fields are implemented by using separate tabs. In this case we are using it to create a new dataset with reduced columns for our model. 

**Data Asset** output node will create a data set with our filtered data called **MLInputData.csv** which we will use for themodel. 

**Partition** node. Partition nodes are used to generate a partition field that splits the data into separate subsets or samples for the training, testing, and validation stages of model building. In this case we split the data 80/20- 80% for trainig and 20% for testing. 

Double click on the Partition node to check the configuration. 

<img src="/images/Modeler6.png" width="30%" height="30%">

For this simple model we used **Linear Regression**. Linear regression models predict a continuous target based on linear relationships between the target and one or more predictors. If you double click on the green linear regression node you will see the target and inputs of the model. 

<img src="/images/Modeler7.png" width="50%" height="50%">

The orange node is the model node created in the first run. Since this is a flow created from a file it is already there. 

Let's see some information about the model with the **Analysis** node. The Analysis node evaluates predictive models' ability to generate accurate predictions. Analysis nodes perform various comparisons between predicted values and actual values for one or more model nuggets. They can also compare predictive models to each other.

There are many other nodes in the modeler. Check them by opening the palette, from the Flow Editor toolbar, click the Open/Close Palette icon.

<img src="/images/Modeler8.png" width="30%" height="30%">

More information about the nodes: https://dataplatform.cloud.ibm.com/docs/content/analyze-data/ml-canvas-spss.html 

### Step 6: Run the flow

Once you have explored the flow click on the _Run_ icon on the tool bar. 

<img src="/images/Modeler9.png" width="30%" height="30%">

After few minutes your flow will show the ouputs of the Statistics, Table and Analysis nodes on the right.
<img src="/images/Modeler10.png" width="30%" height="30%">

Double click in the Statistcs to see how our data behaves. 

If you hover your mouse on the **Table** node three dots will appear in the right side of the box. Click in the dots and then _View Model_. Here you will see your model accuracy. 

<img src="/images/Modeler13.png" width="25%" height="25%">
<img src="/images/Modeler14.png" width="30%" height="30%">

Before we deploy our model we need to create a machine learning service. 
When you are ready to move to the next step go back to the project view by clicking in the name of your project.

<img src="/images/Modeler15.png" width="30%" height="30%">

# PHASE 3
## Deploy ML model using Watson Machine Learning

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

Let's go back to our Modeler flow. 
In the project dashboard, _Asset_ tab, under Modeler Flows you will see the flow created in the previous step. 
Click on the flow to open it again. 

Hover with your cursor in the green regression node and click on the three dots to open the menu. Click on _Save Branch as a model_.

<img src="/images/Model7.png" width="30%" height="30%">

We need to deploy our model using Watson Machine Learning service. Give your model a name and select the machine learning service from your project. Click _Save_. The model will be saved to your project. You can access your
model and create deployments from the Models section under Assets.

<img src="/images/Model8.png" width="70%" height="70%">

A message will be prompted when the model is saved. You can close this window. You will be directed back to the modeler flow, but we don't need to do any more changes here. 

Go back to the dashboard of your projec and under Watson Machine Learning Models you will see the saved model already trained. It is not deployed yet, so click on the model's name to open it. 

<img src="/images/Model9.png" width="70%" height="70%">

Click on _Deployments_ tab and then click on _Add Deployment_

<img src="/images/Model10.png" width="70%" height="70%">

Give your deployment a name and click _Save_.

<img src="/images/Model11.png" width="70%" height="70%">

You will see your deployment in process for few minutes. 

<img src="/images/Model12.png" width="70%" height="70%">

### Step 9: Test the ML model

Once your model's staus says Deployment success click on the deployment name to access the model. 

<img src="/images/Model13.png" width="70%" height="70%">

If you click on the _Test_ tab you will be able to input the parameters to send to the model and see a prediction. 

Write the following code and click _Predict_.

```{"fields":["month","acregs","snowchangemorelimit"],"values":[[3,71,1]]} ```
          
You can change the values. In this example call to the model we used, March (3), 71 planes and days with lots of snow 1.

<img src="/images/Model14.png" width="70%" height="70%">

We will use this model in Lab 2. 


# PHASE 4
## OPTIONAL - Data science with Jupyter Notebooks in Python, R or Scala
A Jupyter notebook is a web-based environment for interactive computing. You can run small pieces of code that process your data, and you can immediately view the results of your computation. Notebooks include all of the building blocks you need to work with data:

   - The data
   - The code computations that process the data
   - Visualizations of the results
   - Text and rich media to enhance understanding
   

After you set up a project and configured the environment, you can create a notebook file, copy a sample notebook from the Community, or add a notebook from a catalog. 

To create a notebook click on _New Notebook_ in your project view 

<img src="/images/Notebook1.png" width="80%" height="80%">

In this lab we are going to import a Jupyter notebook that analyses the sample data with Python. Select _From File_ tab and browse from your computer the downloaded notebook from the BOX folder. **Jupyter notebook name**
Select the runtime free runtime: _Default Python 3.5 (1 vCPU and 4GB RAM) and click on _Create Notebook_.

<img src="/images/Notebook2.png" width="80%" height="80%">

You will need to edit the credentials in the first box of the notebook. After that you can run the notebook by clicking on the run (PLAY) icon.

