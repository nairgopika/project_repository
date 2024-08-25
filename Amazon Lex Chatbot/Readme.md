BankerBot - A Chatbot using Amazon Lex and AWS Lambda
Overview
BankerBot is a conversational AI chatbot built using Amazon Lex and AWS Lambda. It helps users interact with banking services such as checking account balances, transferring funds, and more.

Setup Instructions
Step 1: Set up Your Lex Chatbot
Log in to your AWS account and navigate to Amazon Lex.
Create a new bot named BankerBot.
Configure basic settings, including IAM permissions and COPPA compliance.
Set the intent classification confidence score to 0.40 and finish the setup.
Step 2: Create Your First Intent
Name your first intent WelcomeIntent.
Add sample utterances like "Hi", "Hello", "I need help".
Set the closing response to greet users with "Hi! I'm BB, the Banking Bot. How can I help you today?"
Step 3: Manage FallbackIntent
Customize the fallback message to handle unrecognized inputs.
Save and build the bot.
Step 4: Create a Custom Slot for Account Types
Create a custom slot type named accountType.
Add values such as Checking, Savings, and Credit with relevant synonyms.
Step 5: Create the CheckBalance Intent
Create an intent named CheckBalance with sample utterances for balance inquiries.
Add slots for accountType and dateOfBirth with appropriate prompts.
Save, build, and test the bot.
Step 6: Create Your AWS Lambda Function
Create a Lambda function named BankingBotEnglish using Python 3.12.
Deploy the provided BankingBotEnglish.py code.
Step 7: Connect AWS Lambda with Amazon Lex
Link your BankerBot with the BankingBotEnglish Lambda function.
Save the configuration.
Step 8: Connect CheckBalance Intent with Lambda
Enable Lambda function fulfillment for the CheckBalance intent.
Save, build, and test the bot.
Step 9: Create Output Contexts
Create an output context contextCheckBalance for the CheckBalance intent.
Create a FollowupCheckBalance intent to handle follow-up questions.
Implement context carryover for slot values.
Step 10: Create the TransferFunds Intent
Create an intent named TransferFunds for transferring funds between accounts.
Add relevant slots and set up confirmation prompts.
Save, build, and test the bot.
Final Step: Clean Up Resources
Delete the BankerBot from Amazon Lex and associated Lambda functions.
Remove log files from CloudWatch.
Deployment Using AWS CloudFormation
Use the provided Banker-bot.yaml template to automate the deployment of the chatbot.
Complete the setup and connect the bot to your Lambda function for testing.
Special thanks to Nextwork for their guidance in creating this project.
