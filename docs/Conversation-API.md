# User Chat Conversation API

This endpoint handles the conversation and natural language processing from the front-end, Watson Assitant is used here to understand and classify the question user ask. The raw question acquired from front-end speech to text would be passed into Watson, Watson would then return the response type or response text back after processing, the backend would then process the information from Watson again to add user profile and finally send back to the client.

