# Amazon Alexa Workshop

## Demo Instructions
1. Create the skill on your Alexa account using this branch as the code you import
2. Fill in the API key in the code with your own API key
3. Open the skill and go to testing
4. For current weather, type "Ask Weather Demo what is the weather in Chicago?"
5. For future weather, type "Ask Weather Demo what will the weather be in Houston tomorrow?"
6. For historical weather, type "Ask weather demo what was the temperature in Denver on April 5 2021?" *Change that date to 2 days before the current date. Use the FULL current date, and make sure to capitalize the month.*

## What are we going to build?
An Amazon Alexa skill that answers a user's weather questions:

![](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Example%20Dialog.png?raw=true)

What technologies will we be using?
- [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask)
- Python
- [Weather API](https://weatherapi.com)


### Step 1: Account Setup
##### Amazon Alexa Console #####
Even if you already have an amazon/aws account you will need to follow these steps. Only if you already have an Amazon Alexa Developer account can you skip this section
1. Go to [Amazon Alexa Console](https://developer.amazon.com/alexa/console/ask) 
2. Click "Create your Amazon account" 
3. Fill out the required information (you can skip the phone number step)
4. When you are done, you should be able to navigate to this screen if you click the "alexa developer console" in the top left of the screen: ![](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Developer%20Console%20Home%20Screen.png?raw=true)
5. Keep this tab open

##### Amazon Alexa Console #####
In another tab do these steps:
1. Go to the [Sign Up](https://www.weatherapi.com/signup.aspx)
2. Fill our the required information (you will need to verify your account via the email)
3. When done, hit submit and go to the email you used and click on the Account Activation link
4. When you have verified your email, login to ensure 
5. Keep this tab open

### Step 2: Create & Import Skill
In this section we will walk through the process of setting up your first Alexa Skill!
1. If not already, login to the Alexa Developer Console and go to the homescreen by clicking the Alexa Developer Console logo in the top left. You should be here: ![](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Developer%20Console%20Home%20Screen.png?raw=true)
2. Click "Create Skill" Button
3. Name your skill `Weather Skill`
4. In the "Choose a model to add to your skill" section, select `Custom` tile 
![](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Custom%20Skill.png?raw=true)
5. In the "Choose a method to host your skill's backen resources" section, select `Alexa-Hosted (Python)` tile
![](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Python%20Skill.png?raw=true)
6. Click "Create skill" button
7. In "Choose a template to add to your skill" screen you'll want to click the "Import skill" button: ![](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Import%20Skill.png?raw=true)
8. For the Git reposity URL use:
`https://github.com/TechContentRepo/AlexaWeatherSkill.git`
9. Click import
10. You should get a loading screen that says it is creating your Alexa skill (It took a minute to create for me)
11. That's it! Your skill should be imported which means we'll be programming from here on out!
