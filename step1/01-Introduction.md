# Introduction to Amazon BedRock

## What is Amazon BedRock
Amazon Bedrock is a fully managed service that offers a choice of high-performing foundation models (FMs) from leading AI companies like AI21 Labs, Anthropic, Cohere, Meta, Stability AI, and Amazon with a single API, along with a broad set of capabilities you need to build generative AI applications, simplifying development while maintaining privacy and security. 

With the comprehensive capabilities of Amazon Bedrock, you can easily experiment with a variety of top FMs, privately customize them with your data using techniques such as fine-tuning and retrieval augmented generation (RAG), and create managed agents that execute complex business tasks—from booking travel and processing insurance claims to creating ad campaigns and managing inventory—all without writing any code. 

Since Amazon Bedrock is serverless, you don't have to manage any infrastructure, and you can securely integrate and deploy generative AI capabilities into your applications using the AWS services you are already familiar with.

## Use Cases for BedRock
### Text Generation
Create new pieces of original content, such as blog posts, social media posts, and webpage copy.

### Virtual Assistants
Build assistants that understand user requests, automatically break down tasks, engage in dialogue to collect information, and take actions to fulfill the request.

### Search
Search, find, and synthesize relevant information to answer questions from a large corpus of data.

### Text Summarization
Get summaries of long documents such as articles, reports, and even books to quickly get the gist.

### Image Generation
Quickly create realistic and visually appealing images and animations for ad campaigns, websites, presentations, and more.

## Pricing
You can find the offical pricing available on the AWS website [here](https://aws.amazon.com/bedrock/pricing/). However, at a high level it's on-demand pricing where you only pay for the calls you make to the service (unlike SageMaker for example where additional running costs are required). For the most part... your talking roughly between $0.001 and $0.0125 per 1000 tokens for both input and output payloads. what's a token? A token is comprised of a few characters and refers to the basic unit that a model learns to understand user input and prompt to generate results. what this means is that for most interactions with Bedrock, your looking at less than $0.01.

## IMPORTANT NOTE
it's important to note that as of the time of writing this workshop, Amazon BedRock usage is **NOT** covered by traditional AWS credits and also does **NOT** come with a free tier. This means that any interactions with Bedrock will result in a bill.

## Next Steps
Click [here](02-SolutionOverview.md) to move onto the next step where we can take a look at what we'll be building as a part of this workshop.