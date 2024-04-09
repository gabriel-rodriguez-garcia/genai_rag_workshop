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
