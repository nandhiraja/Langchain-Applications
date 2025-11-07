# LangChain Application Experiments

A personal repository for exploring and building various Generative AI applications using the LangChain framework. This project serves as a learning sandbox to experiment with different components, chains, and agents.

##  Table of Contents

- [About This Repository](#about-this-repository)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Included Applications](#included-applications)
- [Goals for This Repo](#goals-for-this-repo)
- [License](#license)

## ❔ About This Repository

This repository is a collection of small projects and scripts built to learn and understand the capabilities of LangChain. The goal is to experiment with different concepts, including:

* Basic LLM and Chat Model interactions
* Prompt Templates
* Output Parsers
* Retrieval-Augmented Generation (RAG)
* Agents and Tools
* LangChain Expression Language (LCEL)

##  Getting Started

Follow these steps to get a local copy up and running on your machine.

### Prerequisites

* **Python 3.9+**


### Installation

1.  **Clone the repository:**
    ```sh
    git clone [https://github.com/](https://github.com/)[YOUR_USERNAME]/langchain-application.git
    cd langchain-application
    ```
    *(Remember to replace `[YOUR_USERNAME]` with your actual GitHub username.)*

2.  **Create and activate a virtual environment (recommended):**
    ```sh
    # On macOS/Linux
    python3 -m venv venv
    source venv/bin/activate
    
    # On Windows
    python -m venv venv
    venv\Scripts\activate
    ```

3.  **Install the required libraries:**
    A `requirements.txt` file will be in the repo.
    ```sh
    pip install -r requirements.txt
    ```
    *(You will need to create this file and add libraries like `langchain`, `langchain-openai`, `python-dotenv`, etc., as you use them.)*

4.  **Set up environment variables:**
    Create a file named `.env` in the root of the project. This file is listed in `.gitignore` and will not be uploaded to GitHub.
    
    Add your API keys to this file:
    ```
    OPENAI_API_KEY="sk-..."
    GOOGLE_API_KEY="AIza..."
    # Add any other keys you plan to use
    ```

##  Included Applications


-  Will added soon
     


##  Goals for This Repo

-  Build a basic RAG application from scratch.
-  Create a custom agent with its own tools.
-  Experiment with memory in chains.
-  Connect to different vector stores (e.g., Chroma, Pinecone).
-  Explore the LangGraph library for multi-agent workflows.
