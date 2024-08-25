BankerBot - A Chatbot using Amazon Lex and AWS Lambda

Overview
BankerBot is a conversational AI chatbot built using Amazon Lex and AWS Lambda. It helps users interact with banking services such as checking account balances, transferring funds, and more.

Services used:
AWS Lex
AWS Lambda
AWS CloudFormation

Setup Instructions

Step 1: Set up Your Lex Chatbot
Log in to your AWS account and navigate to Amazon Lex.
Create a new bot named BankerBot.
Configure basic settings, including IAM permissions and COPPA compliance.
Set the intent classification confidence score to 0.40 and finish the setup.
![bot1](https://github.com/user-attachments/assets/be36ac71-2096-4414-9798-1ae3f53c4f43)

Step 2: Create Your First Intent
Name your first intent WelcomeIntent.
Add sample utterances like "Hi", "Hello", "I need help".
Set the closing response to greet users with "Hi! I'm BB, the Banking Bot. How can I help you today?"
![bot2](https://github.com/user-attachments/assets/d920fa81-4342-47ee-bbe4-bd4f42cf8830)
![botest](https://github.com/user-attachments/assets/41303cca-901c-4f5f-adad-760fe2fcc568)

Step 3: Manage FallbackIntent
Customize the fallback message to handle unrecognized inputs.
Save and build the bot.
![bot if](https://github.com/user-attachments/assets/2dcd8f32-6838-415f-978e-32779a6d7e6b)

Step 4: Create a Custom Slot for Account Types
Create a custom slot type named accountType.
Add values such as Checking, Savings, and Credit with relevant synonyms.
![bot4](https://github.com/user-attachments/assets/106c7fb3-2d76-430e-a4b0-2af5c02ddfa2)
![bot5](https://github.com/user-attachments/assets/2ecfcab1-3192-4cda-aedf-a7af32b41d41)


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
![bot6](https://github.com/user-attachments/assets/9c2d2293-a99c-4f5a-8cf5-56bd9d716cd0)

Step 8: Connect CheckBalance Intent with Lambda
Enable Lambda function fulfillment for the CheckBalance intent.
Save, build, and test the bot.

Step 9: Create Output Contexts
Create an output context contextCheckBalance for the CheckBalance intent.
Create a FollowupCheckBalance intent to handle follow-up questions.
Implement context carryover for slot values.

![bot8](https://github.com/user-attachments/assets/c0b44105-59d3-41c2-8f0e-6a714e053fed)

Step 10: Create the TransferFunds Intent
Create an intent named TransferFunds for transferring funds between accounts.
Add relevant slots and set up confirmation prompts.
Save, build, and test the bot.

Features in Amazon Lex
(1)Conversation flow: It shows every step in a conversation in a logical, chronological order.
  Scroll to the very top of this intent's page.
  Head to the Conversation flow panel.
![botcon1](https://github.com/user-attachments/assets/b89e4df7-773b-46f7-8067-5dac84229ce2)
![botcon2](https://github.com/user-attachments/assets/993a2d7d-235b-414c-91c5-c1f2489df636)

(2)Visual Builder:This is a visual representation of the intent you have just built.
![botvisual](https://github.com/user-attachments/assets/d96d12b7-4e83-4630-902c-052e0830cacf)

Final Step: Clean Up Resources
Delete the BankerBot from Amazon Lex and associated Lambda functions.
Remove log files from CloudWatch.

Deployment Using AWS CloudFormation
Use the provided Banker-bot.yaml template to automate the deployment of the chatbot.
Complete the setup and connect the bot to your Lambda function for testing.
![botcloud1](https://github.com/user-attachments/assets/e8e8a0bd-e71d-4b42-9ce2-57cd9e5764a3)

Special thanks to Nextwork for their guidance in creating this project.
https://learn.nextwork.org/projects/aws-ai-lex5?track=high
