<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Chat With Your Bot in the Terminal

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-rag-cloudshell)

**Author:** siddharthpk nextwork  
**Email:** siddharthpknextwork@gmail.com

---

## Interacting With My RAG Chatbot in the Terminal

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-cloudshell_1i2j3k4l)

---

## Introducing Today's Project!

In this project, I will build a RAG chatbot that can answer questions about my documents directly from the terminal using AWS CLI commands. I'm doing this project to learn how to interact with Amazon Bedrock, Amazon S3, and AWS IAM through the command line, which will help me develop skills for roles like Backend Developer and DevOps Engineer.

### Tools and concepts

The services I used were AWS, Amazon Bedrock, Amazon S3, AWS CLI, AWS CloudShell, and OpenSearch. The key concepts I learnt included Retrieval Augmented Generation (RAG), Knowledge Bases, AI Models (specifically Titan Text Embeddings V2 and Llama 3.3 70B Instruct), embeddings, vector stores, chunking, custom prompts, and the advantages of using AWS CLI commands for automation and granular control over Knowledge Base management and direct AI model interaction.

### Project reflection

This project took me approximately a few hours of focused effort over a day. The most challenging part was finding the correct Knowledge Base ID and Model ARN to successfully run the bedrock-agent-runtime retrieve-and-generate command. It was most rewarding to successfully validate the Knowledge Base update by asking a previously out-of-scope question and then optimizing the Bedrock CLI output to show only the chatbot's response.

I chose to do this project today because I wanted to deepen my understanding of RAG and specifically learn how to interact with AWS services like Amazon Bedrock, S3, and IAM directly through the AWS CLI. I value the faster interaction, automation, and granular control that the CLI offers for managing chatbot configurations, especially when switching between multiple AI models and Knowledge Bases without relying on the console. Something that would make learning with NextWork even better is providing more advanced challenges or 'Extra for Experts' sections that encourage deeper exploration and customization beyond the core project objectives, perhaps with less hand-holding for experienced users.

---

## Setting Up The Knowledge Base

To set up my Knowledge Base, I used S3 to store my chatbot's training materials. The documents I uploaded contain information that my chatbot will learn from to answer questions.

I also created a Knowledge Base in Bedrock to help my chatbot understand and process the information I stored in S3.

My chatbot also needs access to two AI models, which were Titan Text Embeddings V2 and Llama 3.1 8B Instruct. I then synchronized my data from S3 to my Knowledge Base to ensure the chatbot has the most up-to-date information.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-cloudshell_1u2v3w4x)

---

## Running CLI Commands in CloudShell

AWS CLI (Command Line Interface) is a software that lets me create, delete, and update AWS resources with commands instead of clicking through the console. To start testing CLI commands, I first opened CloudShell, which is a shell in my AWS Management Console that allows me to run code and already has AWS CLI pre-installed.

When I first ran a Bedrock command, I ran into an error because I needed to provide values for my Knowledge Base ID and Model ARN.

While finding the parameters takes extra time, the advantage of using the CLI is that it allows for faster interaction, automation of tasks, and more control over the chatbot's configuration. It's also powerful for switching between multiple models and Knowledge Bases by simply swapping out placeholder values.

While finding the parameters takes extra time, the advantage of using the CLI is that it allows for faster interaction, automation of tasks, and more control over the chatbot's configuration. It's also powerful for switching between multiple models and Knowledge Bases by simply swapping out placeholder values, rather than clicking back and forth between different pages in the console.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-cloudshell_sdrgsert)

---

## Running Bedrock Commands

To find the required values, I had to find my Knowledge Base ID from the console and run a CloudShell command to get my Model ARN. The Bedrock command ran successfully and showed me the chatbot's response in the terminal.

The retrieve-and-generate command typically also outputs a Retrieved Responses section with lots of text. To tidy up the terminal response, I added the --query 'output.text' --output text parameter to only show the chatbot's response.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-cloudshell_1i2j3k4l)

---

## Extending Your Knowledge Base

In a project extension, I asked my Knowledge Base about "Why did the coffee go to the police?". I noticed that the chatbot's response, filtered by the --query 'output.text' --output text parameters, indicated it could not answer the question as it was outside the scope of its Knowledge Base.

To add new information to my Knowledge Base, I ran commands to add new data to my S3 bucket and sync it to my Knowledge Base. Compared to using the console, this process was faster, more flexible, and offered greater control, especially for automation and switching between multiple models and Knowledge Bases.Here are the commands you would typically use:Upload new data to your S3 bucket:

```bash
aws s3 cp /path/to/your/new/data s3://your-s3-bucket-name/ --recursive
```

 Replace /path/to/your/new/data with the local path to your new data files and your-s3-bucket-name with the name of your S3 bucket.Sync your Knowledge Base with the new data:

```bash
aws bedrock-agent sync-knowledge-base --knowledge-base-id your_knowledge_base_id
```

 Replace your_knowledge_base_id with the actual ID of your Knowledge Base.These commands allow you to manage your Knowledge Base updates directly from the terminal, offering more control and flexibility compared to using the console.

To validate the update worked, I ran the aws bedrock-agent-runtime retrieve-and-generate command with the input "Why did the coffee go to the police?". The Knowledge Base successfully responded with "The coffee went to the police because it got mugged.", demonstrating that it could answer questions based on the newly added information.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-cloudshell_sm789ghi)

---

## Interacting with AI Models Directly

On top of chatting with my chatbot, I also interacted directly with an AI model via the terminal by running the aws bedrock-runtime invoke-model command with a prompt to "Write a short poem about cats". This allowed me to bypass the Knowledge Base and directly leverage the AI model's creative capabilities, which then generated a poem about cats.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/ai-rag-cloudshell_gregerg)

---

---
