# GenAI RAG Workshop

This hands-on workshop aimed at developers and solution builders, introduces how to leverage foundation models (FMs) through [Amazon Bedrock](https://aws.amazon.com/bedrock/).

Amazon Bedrock is a fully managed service that provides access to FMs from third-party providers and Amazon; available via an API. With Bedrock, you can choose from a variety of models to find the one that’s best suited for your use case.

Within this series of labs, you'll explore some of the most common usage patterns we are seeing with our customers for Generative AI. We will show techniques for generating text and images, creating value for organizations by improving productivity. This is achieved by leveraging foundation models to help in composing emails, summarizing text, answering questions, building chatbots, and creating images. You will gain hands-on experience implementing these patterns via Bedrock APIs and SDKs, as well as open-source software like [LangChain](https://python.langchain.com/docs/get_started/introduction) and [FAISS](https://faiss.ai/index.html).

Labs include:

- **RAG and KnowledgeBases** \[Estimated time to complete - 45 mins\]

<div align="center">

![imgs/11-overview](09_Guardrails/images/w_highlvl_guardrails_architecture.png)

</div>

The original Amazon Bedrock Workshop upon which this Workshop is based on can be found here [Original Amazon Bedrock Workshop](https://catalog.us-east-1.prod.workshops.aws/workshops/a4bdb007-5600-4368-81c5-ff5b4154f518/en-US).


## Getting started

In order to follow along in the workshop complete the following sequence of steps:

1. Access the AWS account using the link below and add the access code next to the equal sign. Use the access code provided by the workshop hosts.
   Link: https://catalog.us-east-1.prod.workshops.aws/join?access-code=
2. Follow the requested steps until you can access the AWS account.
3. Make sure the region on the top right corner of the AWS console says Oregon (same as us-west-2).
2. Type in "Bedrock" into the search bar and click on Bedrock to access the service console.
3. Click on "Model Access" on the bottom left corner and then click on "Manage model access" on the top right corner of the AWS Console.
4. Select all models from Amazon + all models from Anthropic and click on "save changes". Once the permissions have been approved (2-3 min) your screen should reflect the following state:

<div align="center">

![imgs/bedrock-enaled-models](09_Guardrails/images/bedrock-enabled-models.png)

</div>

5. Type in "SageMaker" into the search bar and click on SageMaker to access the service console.
6. Click on "Studio" on the top left and then "Open Studio" on the top right of the AWS console.
7. Click on "Studio Classic" and then click on "Open" to access the SageMaker Studio Environment where you can run your python notebooks. This step can take a few minutes until your instances have been provisioned.
8. Type in "IAM" into the search bar and then search for the role which starts with "AmazonSageMaker-ExecutionRole-". Click on it and attach an Admin Policy.
9. Go back to SageMaker and open the SageMaker Studio.
10. Click on the version control icon on the top left and select "Clone a repository". Insert the GitHub repository (https://github.com/gabriel-rodriguez-garcia/genai_guardrails_deep_dive_days.git) and click on clone. Alternatively you can open a terminal and clone the repo using standard git comands.
11. You are all set and ready to apply some GenAI guardrails !

### Choose a notebook environment

This workshop is presented as a series of **Python notebooks**, which you can run from the environment of your choice:

- For a fully-managed environment with rich AI/ML features, we'd recommend using [SageMaker Studio](https://aws.amazon.com/sagemaker/studio/). To get started quickly, you can refer to the [instructions for domain quick setup](https://docs.aws.amazon.com/sagemaker/latest/dg/onboard-quick-start.html).
- For a fully-managed but more basic experience, you could instead [create a SageMaker Notebook Instance](https://docs.aws.amazon.com/sagemaker/latest/dg/howitworks-create-ws.html).
- If you prefer to use your existing (local or other) notebook environment, make sure it has [credentials for calling AWS](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html).


### Enable AWS IAM permissions for Bedrock

The AWS identity you assume from your notebook environment (which is the [*Studio/notebook Execution Role*](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html) from SageMaker, or could be a role or IAM User for self-managed notebooks), must have sufficient [AWS IAM permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) to call the Amazon Bedrock service.

To grant Bedrock access to your identity, you can:

- Open the [AWS IAM Console](https://us-east-1.console.aws.amazon.com/iam/home?#)
- Find your [Role](https://us-east-1.console.aws.amazon.com/iamv2/home?#/roles) (if using SageMaker or otherwise assuming an IAM Role), or else [User](https://us-east-1.console.aws.amazon.com/iamv2/home?#/users)
- Select *Add Permissions > Create Inline Policy* to attach new inline permissions, open the *JSON* editor and paste in the below example policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "BedrockFullAccess",
            "Effect": "Allow",
            "Action": ["bedrock:*"],
            "Resource": "*"
        }
    ]
}
```

> ⚠️ **Note:** With Amazon SageMaker, your notebook execution role will typically be *separate* from the user or role that you log in to the AWS Console with. If you'd like to explore the AWS Console for Amazon Bedrock, you'll need to grant permissions to your Console user/role too.

For more information on the fine-grained action and resource permissions in Bedrock, check out the Bedrock Developer Guide.


### Clone and use the notebooks

> ℹ️ **Note:** In SageMaker Studio, you can open a "System Terminal" to run these commands by clicking *File > New > Terminal*

Once your notebook environment is set up, clone this workshop repository into it.

```sh
sudo yum install -y unzip
git clone https://github.com/aws-samples/amazon-bedrock-workshop.git
cd amazon-bedrock-workshop
```


You're now ready to explore the lab notebooks! Start with [00_Intro/bedrock_boto3_setup.ipynb](00_Intro/bedrock_boto3_setup.ipynb) for details on how to install the Bedrock SDKs, create a client, and start calling the APIs from Python.


## Content

This repository contains notebook examples for the Bedrock Architecture Patterns workshop. The notebooks are organised by module as follows:

### Intro

- [Simple Bedrock Usage](./00_Intro/bedrock_boto3_setup.ipynb): This notebook shows setting up the boto3 client and some basic usage of bedrock.

### Chatbot and LLMs Guardrails

- [LLM & NeMo Guardrails](./09_Guardrails/00_llm_guardrails_w_bedrock_nemo.ipynb): Explores the implementation of guardrails for Language Model (LLM) generated responses using Amazon Bedrock and NVIDIA's NeMo. It highlights the utility of guardrails in ensuring responses adhere to desired parameters, providing a more advanced mechanism over standard system prompts. This notebook demonstrates the integration and configuration of guardrails with NeMo and Bedrock, showcasing various guardrail configurations like Jailbreaking Rail, Topical Rail, Moderation Rail and Fact Checking for safer and more reliable AI interactions.

   - **Further Reading:**
     - Familiarize yourself with the basic concepts of guardrails and their implementation in NeMo by exploring the [NeMo-Guardrails documentation](https://github.com/NVIDIA/NeMo). This section helps in understanding how guardrails contribute to the safety, reliability, and ethical handling of LLMs.
