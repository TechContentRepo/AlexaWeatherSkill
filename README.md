# Amazon Alexa Workshop

## What are we going to build?
An Amazon Alexa skill that answers a user's weather questions:

![Expected Result](./photos/Current%20Weather.png)

What technologies will we be using?
- [Alexa Developer Console](https://developer.amazon.com/alexa/console/ask)
- Python
- [Weather API](https://www.weatherapi.com/)


### Step 1: Account Setup
##### Amazon Alexa Console #####
Even if you already have an amazon/aws account you will need to follow these steps. Only if you already have an Amazon Alexa Developer account can you skip this section.

1. Go to [Amazon Alexa Console](https://developer.amazon.com/alexa/console/ask).
2. Click "Create your Amazon account".
3. Fill out the required information and click on the "Create your Amazon account" button (you may need to solve a small puzzle after that).

![Create Alexa Account](./photos/Create%20Alexa%20Account.png)

4. Verify your email address with the One Time Password (OTP) sent to said email.
5. Add and verify your mobile phone number (REQUIRED).
6. Click the "Alexa Skills Kit" if the signup asks for your interests:

![Alexa Skill Kit](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Alexa%20Skill%20Kit.png?raw=true)

7. When you are done, you should be able to navigate to this screen if you click the "alexa developer console" in the top left of the screen: 

![Developer Console Home Screen](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Developer%20Console%20Home%20Screen.png?raw=true)

8. **Keep this tab open**.

##### Weather API #####
In another tab do these steps:
1. Go to the [Sign Up](https://www.weatherapi.com/signup.aspx).
2. Fill our the required information (you will need to verify your account via the email).
3. When done, hit submit and go to the email you used and click on the Account Activation link.
4. When you have verified your email, login to ensure .
5. **Keep this tab open**.

### Step 2: Create & Import Skill
In this section, we will walk through the process of setting up your first Alexa Skill!
1. If not already, login to the Alexa Developer Console and go to the homescreen by clicking the Alexa Developer Console logo in the top left. You should be here: 

![Developer Console Home Screen](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Developer%20Console%20Home%20Screen.png?raw=true)

2. Click "Create Skill" Button.
3. Name your skill `Weather Skill` and choose `English (US)` as the primary locale. When done, click the `Next` button.

![Name, Locale](./photos/Name%20Locale.png)

4. Choose `Other` as a type of experience, `Custom` for the model type, `Alexa-hosted (Python)` as the hosting service, and keep the hosting region given by default. When done, click the `Next` button.

![Experience Model](./photos/Experience%20Model.png)
![Hosting Region](./photos/Hosting%20Region.png)

5. Click the "Import skill" button, paste the URL for this repo (`https://github.com/TechContentRepo/AlexaWeatherSkill.git`), and click on the `Import` button.

![Import Skill](./photos/Import%20Skill.png)

6. You should get a loading screen that says it is creating your Alexa skill (it took a minute to create for me).
7. That's it! Your skill should be imported, which means we'll be programming from here on out!


### About the Alexa Developer Console ###
There is a lot here and it's understandable that it'll be confusing, but we'll walk you through everything you need to use!

### Step 3: Invocation ###
The "Invocation" is what someone needs to say in order to interact with an Alexa Skill. 
1. On the left, click on the "Invocations" tab, and then click on the "Skill Invocation Name".

![Skill Invocation Tab](./photos/Skill%20Invocation%20Tab.png)

2. Use `weather service` as the Skill Invocation Name.

![Invocation Name](./photos/Invocation%20Name.png)

3. Click the "Build skill" button at the top:

![Save Model](./photos/Save%20Model.png)

### Step 4: Interaction Model ###
The Interaction Model is the logic that defines the voice interface that the user interacts with an Alexa Skill. Here is some verbiage that we will use throughout this portion:
- **Intent -** Represents an action that fulfills a user's spoken request. They can optionally have arguments called *slots*.
- **Sample Utterances  -** A set of likely spoken phrases that are mapped to a specific intent.
- **Slots -** a "variable" within an intent/utterance. There are some built-in amazon slots, but you are able to define your own if you'd like.
 
Now let's build our own Interaction Model!
1. On the left, Click "Interaction Model" and then click on the "Intents" sub-item.

![Interaction Model](./photos/Interaction%20Model.png)

2. Click on the "Add Intent" button:

![Add Intent](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Add%20Intent.png?raw=true)

3. Our intent is going to be called `CurrentWeatherIntent` because we want to have our skill tell the user what the current weather is.
4. Click "Create custom intent" button.
5. Now we need to add a Sample Utterance. Let's do one that looks like this `What is the weather in {place}`. Make sure to click the "+" button or it won't be added!

![Sample Utterance](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Sample%20Utterance.png?raw=true)

6. Now we need to create an Intent slot for `{place}`. To do this, go to the "Intent Slots" section at the bottom and create an intent that looks like this:

![Place Intent Slot](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Place%20Intent%20Slot.png?raw=true)

This treats `{place}` as a variable that can take different values depending on what the user says. Make sure to click the "+" button or it won't be added!

7. Click the "Build Skill" button at the top:

![Build Skill](./photos/Build%20Skill.png)

This will take a second, but just wait until you get a "Full Build Successful" notification at the bottom to ensure there were no issues. 

### Step 5: Lambda Function ###
Now that we've built our skill to accept inputs we need to write the code that takes those inputs and does what we want with them! 
1. On the top of the Alexa Developer Console click the "Code" tab. You will see an editor that has a file called `lambda_function.py`. This file already has most of the code that we need to build the weather app. 
2. On `line 25` paste your weather API key here. To do this, go back to your [WeatherAPI](https://www.weatherapi.com/login.aspx) dashboard and generate a free tier API key. 
3. Now scroll down to `line 64`. Here you will see our Intent Hander. This does exactly what you would expect, it handles the intent that is passed into it. Read through the `def handle(self, handler_input)` to understand what is going on.
4. You will notice that the `speak_output` on `line 80` is left blank and has an example for how to create an output. Feel free to create your own output or use the following:
```
speak_output = "The current temperature in " + str(api_response['location']['name']) + " is " + str(api_response['current']['temp_f']) + " degrees Fahrenheit"

```
5. Click the "Deploy" button and that's it!

![Deploy Button](https://github.com/TechContentRepo/AlexaWeatherSkill/blob/master/photos/Deploy%20Button.png?raw=true)


### Step 6: Use Our Skill ###
That's right, now we get to finally see our Alexa Skill in action!
1. Navigate to the "Test" tab on the top of the developer console.
2. Enable testing by clicking the dropdown `Skills testing is enabled in:` and selecting "Development".
3. Type into the input: `open weather service` - this opens our app using its *Invocation*.

![Open App](./photos/Open%20App.png)

4. Now you can ask our skill the weather using the *Sample Utterance* we outlined:
`What is the weather in Chicago`

![Current Weather](./photos/Current%20Weather.png)

Voila! Congratulations on creating your first Alexa Skill!


### Step 7: Add More Functionality ###
Now that you've implemented Current Weather, you can implement Future Weather or Historical Weather functionalities. The base code is already there,
and the intents are already created for you. Take a look at them, and use what you learned from current weather to enhance your Alexa skill. 
Some notes:
 - For simplicity, "tomorrow" is the only available date for FutureWeatherIntent.
 - Because of API free tier limitations, you will only be able to get historical data from the last 7 days. 


### Tips ###
- Make sure to click the "Build Model" button whenever you make changes to the Invocation/Interaction Model.
- Make sure to click the "Deploy" button whenever you make changes to the `lambda_function.py`.
- Use the https://www.weatherapi.com/docs/ to help craft your responses (API Explorer tab is helpful too for easily testing requests).
