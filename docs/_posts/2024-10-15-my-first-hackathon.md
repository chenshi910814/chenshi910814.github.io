---
title: "My first Hackathon Experience"
date: 2024-10-15
---

The past weekend, 

# Email Copilot

## Introduction/Inspiration

Have you ever been overwhelmed by a flood of emails and wished you didn't have to read them all? 

We are aiming to design an AI email plugin powered by the agentic RAG system using cutting-edge LLMs help improve user experience of email client.

- In this agentic RAG workflow, the input is a stream of emails that need to be processed and classified. The workflow begins with a classification step, where an LLM (using either rule-based methods or prompt-driven techniques) is used to categorize the emails based on their content. Once classified, the system accesses a database containing previous emails, searching for similar emails to retrieve relevant contextual information.

- After identifying similar emails from the database, the system generates a summary based on these prior communications. This step ensures that the response or action taken on the new email is informed by previous conversations, leading to a more consistent and contextually relevant output.

- In cases where the email contains a due date or other time-sensitive information, the system automatically manages the user’s calendar by scheduling reminders or events, enhancing productivity and ensuring timely responses. This autonomous behavior allows the workflow to adaptively handle both simple classification and more complex scheduling tasks, making it highly useful for managing large volumes of emails efficiently.


## Data and Workflow
### Dataset
[Enron Email Dataset](https://www.cs.cmu.edu/~enron/)

This dataset was collected and prepared by the CALO Project (A Cognitive Assistant that Learns and Organizes). It contains data from about 150 users, mostly senior management of Enron, organized into folders. The corpus contains a total of about 500,000 messages. This data was originally made public, and posted to the web, by the Federal Energy Regulatory Commission during its investigation. This project uses May 7, 2015 Version of dataset (about 1.7Gb, tarred and gzipped).

### What it Does 
This application helps users efficiently manage their email communications by automatically summarizing email threads when replying. Instead of having to read through lengthy or multiple emails, the system generates concise summaries of the key points, allowing users to quickly understand the context and main ideas. This saves time by distilling important information, helping users stay focused on essential details without needing to sift through entire email chains.

### Agentic RAG Pipeline

![5431728749857_ pic](https://github.com/user-attachments/assets/e43b283c-e312-443a-8c59-923ed20672ad)

## Demo
![9121728846416_ pic](https://github.com/user-attachments/assets/d3d1b6d0-51f4-4da8-bb93-9285e4211976)



## Challenges we ran into
-  The challenge is that it's difficult to ensure the summarization is both concise (e.g., 30 tokens for a short email; 100 tokens for a long email) and also using complete sentences at the same time. Simply setting a max token limit often results in incomplete sentences, making it hard to achieve both goals. In the end, we had to adjust the prompt to instruct the model to generate a summary under a certain word limit based on the email length, rather than strictly setting a max token limit.
-  `LlamaIndex` is a great library that wraps almost every functionalities evolved in the GenAI. However, the learning curve is steep as there are tons of documents for specific tasks and takes time to go through and to experiment. The provided notebook is definitely an inspiring starting point. However, it becomes really challenging once start to build app using it.
-  `Pinecone` is positioned as a great vector database and truly it is. However, there are hidden limits until you start to hit. For example, Upsert data has limits for max batch size based on the dimension and metadata. Without knowing it at the first place, it makes it difficult debugging this issue. Despite Pinecone provides solutions to go around those issues, it still requires a lot efforts to work through them.


## How we built it
Despite three of us are located in different time zones with three hour differences, we have successfully overcome the challenges. We used the `llama_index.embeddings`, `llama_index.vector_stores`，`llama_index.core`，`pinecone` and etc cutting edge tools with `bge-large-en-1.5` opensource embedding model to create embeddings and build out our vector database. We used `gpt-4o-mini` to enable the agentic rag workflow by 1) identifying whether the text is revelent and automatically rerouting to the pre-designed pipelines; 2) summarizing the retrieved relevant information to provide user with latest updates about the subject in the email system.


## Accomplishments that we're proud of
- We are proud to have developed this end-to-end product, taking it from concept to execution. It simulates integrating email summarization seamlessly into the user’s workflow, allowing for a more efficient email experience.

## What we learned
We gained a deeper understanding of integrating different AI tools and frameworks, particularly LlamaIndex, Pinecone, and Agentic Flow. Each of these tools has its strengths, but we learned that combining them into a cohesive workflow presents unique challenges.

When working with Agentic Flow, we discovered the intricacies of managing multi-step workflows that involve decision-making, context passing, and ensuring that the agents function collaboratively without conflicts

We also realized that integrating multiple systems requires careful design and testing to avoid bottlenecks, ensuring that the final product is both efficient and scalable.


## What's next for Email Copilot 
- We'd like to integrate this into an email client plugin so that it 
- If the email includes an attachment, the workflow also extracts and processes content from the attachment. This content is integrated with the email body to produce a more comprehensive summary, ensuring that key information from both the email and attachment is considered in the response.
  

