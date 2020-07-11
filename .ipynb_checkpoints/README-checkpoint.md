# Financial Robo-Advisor 
![robo](images/robo.jpg)
### Background

Robo Advisor is an application that could be used by clients or potential new clients to get investment portfolio recommendations for retirement. Since machine learning and NLP are disrupting finance to improve customer experience. This would be a great way to reach and engage with young people.

Steps to accomplish the project:

1. **[Initial Robo Advisor Configuration:](#Initial-Robo-Advisor-Configuration)** Defined an Amazon Lex bot with a single intent that establishes a conversation about the requirements to suggest an investment portfolio for retirement.

2. **[Build and Test the Robo Advisor](#Build-and-Test-the-Robo-Advisor):** Tested the bot to make sure that the bot is working and responding accurately along with the conversation with the user, by building and testing it.

3. **[Enhance the Robo Advisor with an Amazon Lambda Function:](#Enhance-the-Robo-Advisor-with-an-Amazon-Lambda-Function)** Created an Amazon Lambda function that validates the user's input and returns the investment portfolio recommendation. This task includes testing the Amazon Lambda function and making the integration with the bot.


### BOT Information


* **Bot name:** RoboAdvisor
* **Output voice**: Salli
* **Session timeout:** 5 minutes
* **Sentiment analysis:** No
* **COPPA**: No

Created the `RecommendPortfolio` intent, and configured some sample utterances as follows:

* I want to save money for my retirement
* I'm ​`{age}​` and I would like to invest for my retirement
* I'm `​{age}​` and I want to invest for my retirement
* I want the best option to invest for my retirement
* I'm worried about my retirement
* I want to invest for my retirement
* I would like to invest for my retirement

This bot uses four slots, three using built-in types and one custom slot named `riskLevel`. Defined the three initial slots as follows:


| Name             | Slot Type            | Prompt                                                                    |
| ---------------- | -------------------- | ------------------------------------------------------------------------- |
| firstName        | AMAZON.US_FIRST_NAME | Thank you for trusting on me to help, could you please give me your name? |
| age              | AMAZON.NUMBER        | How old are you?                                                          |
| investmentAmount | AMAZON.NUMBER        | How much do you want to invest?                                           |

The `riskLevel` custom slot is used to retrieve the risk level the user is willing to take on the investment portfolio; created this custom slot as follows:

* **Name:** riskLevel
* **Prompt:** What level of investment risk would you like to take?
* **Maximum number of retries:** 2
* **Prompt response cards:** 4






#### Test the Robo Advisor


#### Enhanced the Robo Advisor with an Amazon Lambda Function

I created an Amazon Lambda function that will validate the data provided by the user on the Robo Advisor. 


##### User Input Validation

* The `age` should be greater than zero and less than 65.
* the `investment_amount` should be equal to or greater than 5000.

##### Investment Portfolio Recommendation

The bot response with an investment recommendation based on the selected risk level as follows:

* **none:** "100% bonds (AGG), 0% equities (SPY)"
* **very low:** "80% bonds (AGG), 20% equities (SPY)"
* **low:** "60% bonds (AGG), 40% equities (SPY)"
* **medium:** "40% bonds (AGG), 60% equities (SPY)"
* **high:** "20% bonds (AGG), 80% equities (SPY)"
* **very high:** "0% bonds (AGG), 100% equities (SPY)"

#### Test the Robo Advisor


[![Robo Advisor test with Lambda](amazon-bot.gif)]


# Built With
#### Python 3
#### Amazon Lambda
#### Amazon Lex
#### Amazon SageMaker
#### Amazon S3
