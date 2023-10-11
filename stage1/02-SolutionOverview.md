# Solution Overview
As outlined in the README, we're going to build a serverless application that will generate YouTube videos for us based on a prompt we give it... similar to the way [Midjourney](https://www.midjourney.com/) can generate us an image based on a description. 

To keep things simple, we'll have the application only generate small 30-60 second videos in the YouTube Shorts/TickTok style... They will be simple videos that will have a voiceOver describes the topic we've specified (for example, "An Introduction to DevOps") while a series of images are displayed that relate to the content being discussed.

## Breaking down the solution
Based on our desired functionality, we're going to need several things to make all of this work, including:
* A script for the Video
* A Narrator that reads the script
* A series of images that will be displayed inline with the VoiceOver
* A way to stich all of these together to make a video
* An orchestration layer to co-ordinate all these actions

### A Script for the Video
We can use Amazon Bedrock for this. we can leverage the AI21 Labs model's to generate a Video script based on a description we can provide and have it returned as a text file. In fact, if we craft the prompt correctly, we can even have it suggest the images that should be displayed as well.

### A Narrator that reads the Script
Once we've got our script in the form of a text file, we can pass that into Amazon Polly and have it perform some Text to Speech magic and produce us an MP3 recording that we can use as our VoiceOver.

### A Series of Images that will be displayed inline with the VoiceOver
If we've gotten Bedrock to suggest which images should go with our script, we already have a list of what images we should use... we get need to get them. Much like the script, we can use Bedrock to generate these for us. By using Stability AI's Stable Diffusion Foundational Model through Bedrock we can get back png files rather than text, giving us whatever images we need to populate our video

### A way to stich all of these together to make a video
FFMPEG is a free open-source tool that provides a wide variety of functions when it comes to video files. Once thing it can do is stich a series of images together to make a video and even overlay an MP3 recording over the top. We can leverage Lambda and image a layer with FFMPEG pre-compiled and use that to combine all our assets and generate the finished video which we'll then save to an S3 bucket ready for use.

### An orchestration layer to co-ordinate all these actions
A number of these tasks have dependencies while others can run in parallel, reducing the total amount of time it would take to generate our finished product. To help manage all of this, we can use AWS Step Functions as a workflow engine and have it tie all the steps together.

## Next Steps
Now that we have a clearer understanding as to "What" we are going to build, we can move onto the "How" we can build it. Click [here](../stage2/01-GettingStarted.md) to get starting building the solution.