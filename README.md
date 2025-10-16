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

