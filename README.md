# Automated Machine Learning in Azure Marchine Learning 
1º projeto do curso de Azure.
## I. Create an Azure Machine Learning Workspace 
 1. Sign into the Azure portal at [Azure Portal](https://portal.azure.com/) using your Microsoft credentials.
 2. Select + Create a resource, search `Marchine Learning` and create a new Azure Machine Learning resource.
## II. Use Automated Machine Learning to Train a Model
1. In [Azure Machine Learning Studio]() view the **Automated ML** page (under **Authoring**).
2. Create a new Automated ML job with the following settings, using **Next** as required to progress through the user interface:
 
  **Basic settings**:
  
  Job name: mslearn-bike-automl
  New experiment name: mslearn-bike-rental
  Description: Automated machine learning for bike rental prediction
  Tags: none
  **Task type & data**:
  
  Select task type: Regression
  Select dataset: Create a new dataset with the following settings:
  Data type:
  Name: bike-rentals
  Description: Historic bike rental data
  Type: Tabular
  Data source:
  Select From web files
  Web URL:
  Web URL: https://aka.ms/bike-rentals
  Skip data validation: do not select
  Settings:
  File format: Delimited
  Delimiter: Comma
  Encoding: UTF-8
  Column headers: Only first file has headers
  Skip rows: None
  Dataset contains multi-line data: do not select
  Schema:
  Include all columns other than Path
  Review the automatically detected types
  Select Create. After the dataset is created, select the bike-rentals dataset to continue to submit the Automated ML job.
  
  **Task settings**:
  
  Task type: Regression
  Dataset: bike-rentals
  Target column: Rentals (integer)
  Additional configuration settings:
  Primary metric: Normalized root mean squared error
  Explain best model: Unselected
  Use all supported models: Unselected. You’ll restrict the job to try only a few specific algorithms.
  Allowed models: Select only RandomForest and LightGBM — normally you’d want to try as many as possible, but each model added increases the time it takes to run the job.
  Limits: Expand this section
  Max trials: 3
  Max concurrent trials: 3
  Max nodes: 3
  Metric score threshold: 0.085 (so that if a model achieves a normalized root mean squared error metric score of 0.085 or less, the job ends.)
  Timeout: 15
  Iteration timeout: 15
  Enable early termination: Selected
  
  **Validation and test**:
  Validation type: Train-validation split
  Percentage of validation data: 10
  Test dataset: None
  Compute:
  
  Select compute type: Serverless
  Virtual machine type: CPU
  Virtual machine tier: Dedicated
  Virtual machine size: Standard_DS3_V2*
  Number of instances: 1
  * If your subscription restricts the VM sizes available to you, choose any available size.

3.Submit the training job. It starts automatically.

4.Wait for the job to finish. It might take a while — now might be a good time for a coffee break!

## III. Review the Best Model
When the automated machine learning job has completed, you can review the best model it trained. 
1. On the **Overview** tab of the automated machine learning job, note the best model summary.
2. Select the text under **Algorithm name** for the best model to view its details.
   Select the Metrics tab and select the residuals and predicted_true charts if they are not already selected.
