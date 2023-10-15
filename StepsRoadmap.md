# Dialogflow Chatbot Setup Guide

Dialogflow is a platform for creating conversational user interfaces. One of its features allows you to build a question-and-answer system using a knowledge connector.

## How It Works

Each time a user enters a query into the chatbot, Dialogflow sends the query to a local server via a webhook and Ngrok. The local server's model selects the closest matching response from the knowledge base and returns the most likely response to the query. In this guide, we illustrate the process using an HR domain example, but it's applicable to other domains as well.

![Overview](https://user-images.githubusercontent.com/85472923/121799695-166b7580-cc60-11eb-92dc-770bac62cc84.jpg)

## Step 1: Set up in Dialogflow

1. Sign up for a Dialogflow account on [Dialogflow's official website](https://cloud.google.com/dialogflow/docs/).
2. Create a project and an agent in Dialogflow following the steps in [Google's developer documentation](https://developers.google.com/assistant/conversational/df-asdk/dialogflow/project-agent). If you have multiple intents in the agent, you may add training phrases to the HR_FAQ intent. However, there's no need to add responses as they will be generated from the model in the local server.

## Step 2: Develop Model in Python using Flask

We use a pre-trained DistilRoBERTa model to extract sentence embeddings due to the small number of question-answer pairs in the knowledge base. Other pre-trained models can also be used, as long as the response time is reasonable. In this guide, we favor DistilRoBERTa over RoBERTa due to its quicker response time.

Based on the sentence embeddings, we calculate cosine similarity between the query and questions to identify the most similar question. The model then uses a retrieval approach to find the corresponding answer that matches the most similar question.

![Model](https://user-images.githubusercontent.com/85472923/121800851-b75d2f00-cc66-11eb-9fbd-c93931475941.jpg)

## Step 3: Deploy Model & Integrate with Dialogflow using Webhook & Ngrok

1. Download Ngrok from [here](https://ngrok.com/download) and install it on your computer. Ngrok is a popular tunneling tool for exposing your application to the internet and receiving webhooks from Dialogflow.
2. Start Ngrok.
3. Assuming your Flask application is running locally on port 5000, type `ngrok http 5000` into Ngrok.
4. Copy the HTTPS forwarding address provided by Ngrok to integrate with Dialogflow.
5. In the Dialogflow Fulfillment tab, paste the HTTPS URL and add "/webhook" to the end of the URL. The final URL format will look like `https://your-ngrok-address.io/webhook`. For more information, refer to the ["Enable and manage fulfillment" section](https://cloud.google.com/dialogflow/es/docs/fulfillment-webhook).
6. To enable fulfillment, go to the HR_FAQ intent and turn on "enable webhook call for this intent." Then, click save.

## Step 4: Test the Chatbot

Enter a test query in the test console of Dialogflow to ensure that the chatbot is working correctly.
