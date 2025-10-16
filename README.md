# AI_Agent_Test
We will build our very first AI agent that predicts the weather.

# Helpful Resourses: 
    - https://labex.io/linuxjourney
    - https://www.w3schools.com/python/python_pip.asp
    - https://github.com/pyenv/pyenv
    Follow instructions to installing Pyenv for Windows, Homebrew on Mac in order to using Python versions

# Step 1
To build your very first AI model, you have to decide on what ADK or Agent Development Kit your going to use
To name a few you have:
- Google ADK
- Crew.ai
- And more!

For simplicity and concept learning we will be using Google ADK platform.
# Step 2: Set up your environment
Before coding your very first AI Agent, you have to set up your environment first to make it work in the first place!😅
## Requirements:
- If you are using Github Codespaces, follow the steps below and ignore the additional steps portion of this README.md file.
- If you are using your computers file storage (Finder on Mac/Folder on Windows), please do the additional steps before continuing here.

### Command 1: pip --version
Please enter the following command in your own Codespace terminal in order to check if pip is installed. If not, follow Additional Steps on installing pip.

#### What does this command do?
This command is just checking if a tool called pip is already downloaded in the codespace environment. For more information, you can access the following link: https://www.w3schools.com/python/python_pip.asp

### Command 2: python -m venv .venv
This sometimes might not work depending on where you are doing this. Sometimes you might have to use Python3 instead of Python. However, if you are doing it via codespaces, then it shouldn't be a problem. 

#### ONLY FOR PEOPLE NOT USING GITHUB CODESPACES
IF YOU ARE DOING THIS ON YOUR COMPUTER'S file system, please make a directory for the project you want to store your AI agent in. 
This step is MANDATORY before the initializing your environment. Once you navigate to the location where you want to store your AI_Agent (you can type cd), type the following command:
#### mkdir Directory_name
This command should make you a directory. Type: 
#### cd Directory_name
This should make the terminal be in your Directory. After that type the python ... 
#### What does this command do? 
This command initializes your coding environment. As you progress on building more and more projects, chances are that you will use a ton of libraries. Ideally, when you work professionally, this environment creation comes into play. It allows libraries necessary for your app to be used when you are building your app
#### Example
Let's take that you are building Application #1 and you have Application #2 in a different directory. Application #1 uses a lot more libraries compared to Application #2, most of which Application #2 doesn't need or require. Environments come to play by enhancing performance of your apps, allowing your apps to use and take the required libraries will not storing libraries that it doesn't need.

### Command 3: source .venv/bin/activate
The command before only created a virtual environment that we can use, however, we need to use it. That's why we follow-up with this command; so that we can actually code in the .venv.

At this point feel free to check out every file in the .venv so that you can understand what exactly is it.
To see all files in bash, type the following: 
#### ls

### Command 4: pip install google-adk
Btw, if you're in any file just exit and return to .venv, if you're in a directory type: cd .. to exit
At this point, we can now safely install Google ADK, so type or paste this command into your terminal. If you see a bunch of lines, don't worry, these are just the libraries that agents need to run.

This command installs google's Agent Development Kit, which we will use to build our own agent.

### Command 5: adk create my_agent
This command creates your AI agent called my_agent. At least here I called it that. Feel free to change the name to whatever your choosing.
When you press enter, make sure to click Google Gemini for both and not Vertex. Here we will be using Google.
Another parameter that is required is that you have to get your API key to access Gemini. I will not be covering this process as it is just logging into Google AI studio and getting an API key. 
**WARNING** You must use a 18+ account to get an API key, don't ask me why.

## Step 3: Building our AI Agent
You'll first start off with the basic template, so that gives a valid start point. Under your codespace repository make a .gitignore file and paste the same contents of that file located in this repository. This will help later when you have push changes to your repository.

In the file structure, you should see agent.py. Click on it to open the file. You will see root_agent. This agent is now our main agent. Here we have our basic LLM that does nothing. 

### Adding Google Search capabilities
If you're new, open a new tab and type in Google ADK documentation. Then click on API reference. On that screen, you will see a bunch of programming languages API References, click on Python API Reference.

On this page search for google_search, and click on the first link you see. It will take you to the **Source Code** of that tool. 

Now, return back to agent.py, once you are here, import the google_search_tool. This is the exact line you should import:
#### from google.adk.tools.google_search_tool import google_search
After importing this, at the end of the declaration of root_agent, add an array called tools. And type in google_search
#### tools = [google_search],
Once you add this line, you Agent should run! Wait, you don't know how to run your AI agent? Well that's simple! Open your terminal (if you don't have it open), and type in:
#### adk web
It should open a localhost:8000 url. It won't work, wait till you see a button that says open link on the bottom right hand side of the computer screen.
Once you open that link, you should be able to chat with your AI Agent! 

*Congrats!* You just made your very first AI agent! 🎉

## But wait... You can have sub Agents?

Yes, actually, why don't we do it right now? 
Here's the layout: 
root_agent -> science_agent: Solves Science concepts and problems
root_agent -> math_agent: Solves math concepts and problems
root_agent -> google_search_agent: Gets information using Google Search (*Special Case*)
### Step 1: Add folders for each sub agent
Create 3 folders with the names of each agent.
Inside each folder should be an agent.py file and __init__.py file.

### What's the __init__.py for? 
This file is used to make our agents available to use to any outside agents or services that may require a specific agent.

### Open __init__.py and paste the following code:

#### from .agent import math_agent
####
#### __all__ = ["math_agent"] # This is all I want to export from this math module; Make math_agent available for use

### Repeat the process for science_agent and google_search_agent
Make sure to change the names of the agents when you copy + paste, then only it will work.

### In math_agent, open agent.py
Copy paste the code you had in root_agent's agent.py file.
After this make sure to change the name from root_agent to math_agent.
Make sure to remove the tools array from this agent, this agent won't use any.
Open chatgpt and generate it's instructions in Markdown format. When you copy paste those instructions make sure to double-check the instructions and reformat it so that is tabbed properly, like in this repository.
After this, make sure you change the description of the AI agent so that it has a proper backstory, this can skew results. So it is very important that you are clear.

### Repeat the process for science.py and google_search_agent

### Go back to root_agent's agent.py file. 
When you load this file, you'll see that it's missing instructions too. Therefore, go to chatgpt and generate it's instructions. Another key aspect that you should know about root_agent is that it is an orchestrator agent, meaning it calls specialized agents to get their services.
When you finish formatting root_agent's instructions, import the following: 
#### from google.adk.agents.llm_agent import Agent
#### from google.adk.tools.google_search_tool import google_search # Google_Search is a built-in tool in adk; NOT a function
#### from my_agent.math_agent import math_agent
#### from my_agent.science_agent import science_agent
#### from my_agent.google_search_agent import google_search_agent_tool
After importing the following libraries, you'll notice a difference with one library. To fully understand that we have to go back to the google_search_agent, and change a few things.
### google_search_agent's agent.py file
As is the code will not run, it will throw off errors. That's because google_search in reality is just a tool, so we have to import the following library to the code: 
#### from google.adk.tools import agent_tool
This library allows us to declare the agent as a tool and use it as a tool.
Now, go to end of the file, there add the array tools and *google_search* inside it.
Afterwards, exit from the declaration of *google_search_agent* and paste the following code:
#### google_search_agent_tool = agent_tool.AgentTool(agent=google_search_agent)
This converts our agent to be used as a tool rather than an agent. This will be handy pretty soon, but we also have to change the __init__.py file. Make sure you apply the changes to that file too.

### Final steps:

After you return to root_agent's agent.py file, make sure you have the following import statements:

#### from google.adk.agents.llm_agent import Agent
#### from google.adk.tools.google_search_tool import google_search # Google_Search is a built-in tool in adk; NOT a function
#### from my_agent.math_agent import math_agent
#### from my_agent.science_agent import science_agent
#### from my_agent.google_search_agent import google_search_agent_tool
After that, add the tools array and add google_search_agent_tool to it (remember its now a tool).
Finally, add a new array called sub_agents = there, add references to all the agents you created. It should look something like this:
#### sub_agents=[
####    math_agent, 
####    science_agent,
#### ],
#### tools=[
####    google_search_agent_tool,
#### ]

After this, you've created your very first multi-agent System! 🎉

# Pushing Changes to Github Repository
If you're like me, you want to save your work, so assuming you have .gitignore copied to your repository code, follow the steps below
## Step 1: Check git status
Type *git status* to see the unsaved changes you have in your file. 
## Step 2: Add my_agent/ to the Github repository
Type *git add my_agent/* to add my-agent/ to github
## Step 3: Commit
Type *git commit -m "The change you did"* This command will allow you to save and sort of compile your code before you push changes.
## Step 4: The Final Step: Push
Type *git push* to push your final changes and update your repository for all to see.