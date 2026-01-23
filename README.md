# CONNECT Write From Databricks Notebook
**Version:** 1.0.0

The sample code in this project demonstrates how to write data back to CONNECT data services (Cds) from Databricks. In order to run this sample, you need to have a Databricks environment.

Developed against Python 3.10.12

## About the sample

This sample is intended to show you how you can write time-series data to CONNECT data services from a Databricks notebook. This may be useful after performing analytics or modelling in Databricks to bring those insights back to the CONNECT platform (and then perhaps back to an on-prem system). There are two sample notebooks in this repository. 

1. **Write Single Stream to CONNECT using API Notebook.ipynb**
uses the CONNECT data services Sequential Data Store (SDS) REST API to write values to a stream. It also makes use of the [Python sample library](https://github.com/AVEVA/sample-adh-sample_libraries-python) to keep the code simple. This method is straightforward and is more suited to sending minimal data to one or a few streams
3. **Write Multiple Streams to CONNECT using OMF Notebook.ipynb** 
uses CONNECT data services OMF messages to write a large amount of data to one or many streams. This is recommended method of sending a large amount of data to CONNECT data services. For more information on OMF, see [Open Message Format (OMF)](https://docs.aveva.com/category/omf)

## Getting started

1. Clone the GitHub repository or download the .ipnyb files
2. Import the notebook(s) into your Databricks environment. Follow the instructions at [Import and export Databricks notebooks](https://docs.databricks.com/aws/en/notebooks/notebook-export-import)
3. Follow the instructions in the notebook an run each code block in order.

### Creating the secret scope

This sample makes use of secret scopes in Databricks to securely store the credentials to CONNECT data services. To set up the secret scope, first create a client-credentials client in CONNECT data services. For this sample, the client-credentials client needs to be given a role that has read and write access to a CONNECT data services namespace. For instructions, see: [Add a client-credentials client](https://docs.aveva.com/bundle/connect-data-services/page/1263324.html) 

You can then create the secret scope with one of two options. 

1. **Use the Databricks CLI**
by following [Create a secret](https://docs.databricks.com/aws/en/security/secrets#create-a-secret). Create two secrets within that secret scope called `cdsclientid` and `cdsclientsecret` containing the client id and secret generated from CONNECT data services.

2. **Create a secret scope using the Databricks SDK for Python**
using the included sample code to create the secret scope and secrets.

_Note: Option 2 requires temporarily entering your client credentials into the notebook as plain text. It's recommended to delete these credentials after the block is run._

### Running the notebook

To run the Notebook(s), you first need to attach it to a compute resource (cluster or SQL warehouse). Once attached, you can run cells individually, run all cells, or schedule the notebook as a job.

### Test the notebook

The last cell in the notebooks are for running tests so that you can test to make sure the whole notebook is working as expected. Because it tests the methods defined earlier in the notebook, you need to run the previous cells of the notebook before trying to run the tests. You will know the tests pass when the block succeeds without any exceptions.

---

For the main CONNECT data services samples page [ReadMe](https://github.com/AVEVA/AVEVA-Samples-CloudOperations)  
For the main AVEVA samples page [ReadMe](https://github.com/AVEVA/AVEVA-Samples)
