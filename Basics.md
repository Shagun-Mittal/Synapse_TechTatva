# Dialogflow ES Basics

[Dialogflow](https://cloud.google.com/dialogflow/es/docs/basics) (ES) is a versatile conversational interface platform developed by Google. It simplifies the creation of chatbots, virtual assistants, and other conversational applications to provide a more natural and interactive user experience. It's an excellent tool for beginners looking to enter the world of conversational AI.

## Agents


A Dialogflow agent is a virtual agent designed to handle user conversations, understanding human language nuances and translating them into structured data. It's similar to a call center agent, trained to handle expected conversations with minimal explicit training.

## Intents

Intents categorize an end-user's intention in a conversation turn. They match user expressions to the best intent in your agent, allowing you to extract useful information and generate responses. Basic intents include training phrases, actions, parameters, and responses.

## Entities

Entities dictate how data from user expressions is extracted. Dialogflow offers system entities for common data types and allows you to create custom entities for unique data matching needs.

## Contexts

Contexts help Dialogflow understand the flow of a conversation. They enable more accurate intent matching by maintaining context between user inputs and agent responses.

## Follow-up Intents

Follow-up intents are automatically linked to parent intents, allowing for context-based conversations. They're useful for handling common user responses like "yes" or "no."

## Dialogflow Console

Dialogflow provides a web interface called the Dialogflow Console for agent creation, building, and testing. It's distinct from the Google Cloud Platform (GCP) Console, which handles GCP-specific settings.

## User Interactions with Integrations

Dialogflow seamlessly integrates with popular platforms like Google Assistant, Slack, and Facebook Messenger, making it easier to build agents for these platforms.

## Fulfillment for Integrations

Fulfillment enables dynamic responses by calling a defined service when an intent is matched, making it suitable for actions beyond the static responses.

## User Interactions with the API

If you're not using integrations, you can interact with Dialogflow's API to directly manage user interactions, sending expressions and receiving intent matches.

[Learn more about Dialogflow ES](https://cloud.google.com/dialogflow/es/docs/basics)
