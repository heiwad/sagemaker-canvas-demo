## SageMaker Canvas Demo



This is how to follow along or recreate the demo you'll be seeing today.



Note SageMaker canvas may create resources such as that require increasing your account quota for specific EC2 instance types. Also the pricing model for canvas is a bit different from that of the underlying services.



### Step 1: Get the data

Download the data from this repo. 

Training Data: [churn-train.csv](https://github.com/heiwad/sagemaker-canvas-demo/blob/main/churn-test.csv)

Test Data: [churn-test.csv](https://github.com/heiwad/sagemaker-canvas-demo/blob/main/churn-test.csv)



**Data Notes:**

The data set I'm using is from the XGBoost Customer Churn example in the amazon-sagemaker-examples repo. Mobile operators have historical records on which customers ultimately ended up churning and which continued using the service. We can use this historical information to construct an ML model of one mobile operator’s churn.

It's publicly available and was mentioned in the book [Discovering Knowledge in Data](https://www.amazon.com/dp/0470908742/) by Daniel T. La rose. It is attributed by the author to the University of California Irvine Repository of Machine Learning Datasets. 

Alternatively, you can bring your own tabular data. The training data must be CSV that uses commas as a separator and is less than 5GB in size. Reserve a portion of the data in a separate CSV so you can run inferences. 

### Step 2: Get a Sagemaker Studio Domain

1. Create a Sagemaker using the Quick Setup and allow Sagemaker to create the default execution role.

   You may create your domain in one of the following regions: US East (Ohio), US East (N. Virginia), US West (Oregon), Asia Pacific (Tokyo), Europe (Frankfurt), or Europe (Ireland).

2. Find the S3 bucket created for your SageMaker Studio domain and apply the following CORS policy to the bucket. 

   The bucket will follow the naming convention ``sagemaker-Region-your-account-id`

   Policy

   ```
   [
       {
           "AllowedHeaders": [
               "*"
           ],
           "AllowedMethods": [
               "POST"
           ],
           "AllowedOrigins": [
               "*"
           ],
           "ExposeHeaders": []
       }
   ]
      
   ```

   

3. Optional - To do time series forecasting, modify the IAM role created for your SageMaker domain to enable support for Amazon Forecast as outlined in the [SageMaker Canvas Getting Started guide](https://docs.aws.amazon.com/sagemaker/latest/dg/canvas-getting-started.html). We will not be using Forecast today and you can do this later. 



### Step 3: Showtime

Ok. Now that you have the CSV data and a SageMaker domain you are ready to follow along. 

