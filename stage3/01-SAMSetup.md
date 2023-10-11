# Setting up a New SAM Project
OK... Time to start developing a solution. 

We'll be using [AWS SAM](https://aws.amazon.com/serverless/sam/) (Serverless Application Model) as the framework to build out our application so let's start things off by creating a new project.

## New SAM Project
In your terminal, create a new project using the ```sam init``` command

![sam init](image1.png)

next, to keep things simple we can go ahead and create a new project based on an "AWS Quick Start Template" so go head and select choice 1.

![Choice 1](image2.png)

Next we need to select which type of QuickStart we want to use... Honestly, we don't actually want any of them we just want the skeleton so it's easier to just select Template 1 and we can change what we need to after the fact.

![Template 1](image3.png)

Yes to using the most popular runtime, which is **python** and **zip** files.

![python zip](image4.png)

No to using X-Ray. This is just to keep the workshop as simple as possible... X-Ray can be very helpful for these types of projects

![No Xray](image5.png)

and No to CloudWatch Application Insights for the same reason

![No Insights](image6.png)

Give your project a name.. Doesn't really matter what it is, but for the example we'll use **youtube-short-generator**

![SAM Name](image7.png)

And at this point, the SAM cli will start downloading and configuring the template for us which will take a couple of minutes.

![Download Template](image8.png)

After a few minutes you should see a set of commands you can now run on your new SAM application indicating a successful creation of your application.

![Template Ready](image9.png)

## Building and Deploying our template
OK, so it doesn't do anything yet... but as a way of testing that everything it setup correctly I always find it useful to deploy our new application into AWS as it:
* Confirms the application built correctly
* confirms AWS sam is working correctly
* Validates that my AWS CLI credentials are configured and pointing to the correct AWS account

So, with that in mind we can ```cd``` into our new project so we can start working on it.

![cd](image10.png)

Before we can **deploy** our new application (which only consists of a single "hello World" lambda function) we first need to **build** it which includes things like zipping up our lambdas so they are ready for upload. This, is a pretty simple process and can be achieved by running the ```sam build``` command

![sam build](image11.png)

Now we have the assets ready to deploy. Given however we've never actually deployed anything before we need to setup out toml configuration file. The easiest way to do this is to simply follow the instructions on the page and run the ```sam deploy --guided``` for the first time. In future deploys we can drop the ```--guided``` switch.

![sam deploy --guided](image12.png)

First we need to deside on the CloudFormation Stack name it will deploy to. For the purposes of the workshop we can stick with the default by simply hitting ```Enter```.

![Stack Name](image13.png)

Next is region. For the Demo we're using **us-east-1** but you can use any region that has Amazon Bedrock available.

![region](image14.png)

Next is wether we want to confirm changes before they are deployed. This is a great feature and should be used for production environment or those that get a lot of use... But as this is an application just for us and if we push a bad config it's not going to be too much of an issue, we can go ahead and choice ```N``` for this one.

![No Change approval](image15.png)

Next we want to allow SAM to create the required IAM roles for it to do it's job.

![IAM Role Creation](image16.png)

And No to disabling rollback for the same reasons... this isn't a critical production application.

![Rollback](image17.png)

Next, SAM is simply warning us that we have a function that doesn't have any authentication on it. This is fine as we'll be replacing it with our own functions soon enough. Enter ```y``` to continue.

![No Auth](image18.png)

Yes, we want to save these arguments to a config file.

![Config file](image19.png)

and we can accept the default path and name for this file.

![samconfig](image20.png)

Next comes SAM environment. You can configure multiple SAM environments (dev/test/prod) to help stage your application changes. We won't be using this feature for the workshop so we can go ahead and leave it as the default (which is default funny enough).

![Default](image21.png)

At this point, SAM will start to create the required resources to deploy the application successfully. This process can take a little while and a lot of text might fly by the screen, this is expected behavior.

![Creating Resources](image22.png)

After a little while, SAM will move onto deploying your application. Just continue to play the waiting game.

![Application Deployment](image23.png)

And finally, you should be presented with the output values of your application and a "Successfully created/Updated stack" message.

![Successfully created/updated stack](image24.png)

## Confirm successful deployment
If you log into your AWS account and take a look at **CloudFormation** in the specified region, you should see both a "Managed default" stack (responsible for giving SAM the permissions it needs to deploy) and a stack by the name you defined earlier. This second stack is the application we've created and the one we'll work on for the remainder of the workshop.

![CloudFormation Stacks](image25.png)