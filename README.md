# Chat with MySQL Database - Streamlit Web Application 
[![View the Web App](https://img.shields.io/badge/View%20App-Streamlit-blue)](https://sql-chatbot-bmyimjcrdn3nes8s9fdzzs.streamlit.app/)

This project is a web-based chatbot application that allows users to interact with a SQL database using natural language. It uses the OpenAI API to generate MySQL queries based on user questions and then converts the database results into a natural language response. The application is deployed on Streamlit Community Cloud and connects to a MySQL database hosted on Amazon Web Services(AWS) RDS.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [How It Works](#how-it-works)
- [Benefits](#benefits)
- [Deployment](#deployment)
  - [1. Prerequisites](#1-prerequisites)
  - [2. Setting Up AWS RDS and MySQL Database](#2-setting-up-aws-rds-and-mysql-database)
  - [3. Deploying the Application on Streamlit Community Cloud](#3-deploying-the-application-on-streamlit-community-cloud)
- [Configuration](#configuration)
- [Running Locally](#running-locally)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This application allows users to interact with a SQL database using natural language questions. By utilizing OpenAI's language model capabilities and LangChain's utility libraries, the application converts natural language input into MySQL queries, retrieves data from the database, and provides responses in natural language. The web interface is built using Streamlit, making it easy to deploy and run in a web browser.

## Features

- **Natural Language Interface**: Users can ask questions about the database in natural language.
- **Automatic SQL Query Generation**: The chatbot generates SQL queries based on user input.
- **Dynamic Database Connection**: The application connects to a MySQL database hosted on Amazon Web Services(AWS) RDS.
- **Streamlit Web Interface**: Simple and interactive user interface using Streamlit.
- **Conversation History**: Keeps track of conversation history for context-aware query generation.

## How It Works

1. **User Interaction**: The user inputs a natural language question about the database.
2. **SQL Query Generation**: The application generates a corresponding MySQL query based on the user's question using the OpenAI API.
3. **Database Query Execution**: The generated query is executed on the connected MySQL database hosted on AWS RDS.
4. **Natural Language Response**: The results from the database are processed and converted into a natural language response, which is displayed to the user.
5. **Conversation History Maintenance**: The conversation history is maintained to enable context-aware query generation.

## Benefits

- **User-Friendly Interface**: Enables users to interact with a database without needing to know SQL.
- **Time-Saving**: Quickly retrieves insights from a database using natural language queries.
- **Accessible Anywhere**: Hosted on Streamlit Community Cloud, allowing access from any device with a web browser.
- **Dynamic Configuration**: Allows easy switching between different database connections through the sidebar settings.

## Deployment

### 1. Prerequisites

- **OpenAI API Key**: Required for generating natural language responses.
- **MySQL Database**: Hosted on Amazon Web Services(AWS) for public access.
- **Streamlit Community Cloud Account**: For deploying the application.

### 2. Setting Up AWS RDS and MySQL Database

1. **Create a MySQL Database on AWS RDS**:
   - Go to the [AWS Management Console](https://aws.amazon.com/console/).
   - Create a new RDS instance with MySQL and configure your database.
   - Choose "Publicly accessible" during setup to allow external connections.

2. **Configure Database Access**:
   - Note down the AWS RDS endpoint, database name, user, and password.

3. **Configure Security Group**:
   - In your RDS instance's security group settings, add an inbound rule to allow MySQL/Aurora (port 3306) access from the IP range that your app (e.g., Streamlit) uses to connect to the RDS instance.

### 3. Deploying the Application on Streamlit Community Cloud

1. **Fork/Clone the Repository**:
   - Fork or clone this repository to your GitHub account.

2. **Add a `.streamlit/secrets.toml` File**:
   - In your project folder, add a file named `.streamlit/secrets.toml`.
   - Add your OpenAI API key and database credentials:
     ```toml
     [secrets]
     OPENAI_API_KEY = "your_openai_api_key"
     DB_USER = "your_database_username"
     DB_PASSWORD = "your_database_password"
     DB_HOST = "your_gcp_public_ip"
     DB_NAME = "your_database_name"
     ```

3. **Deploy on Streamlit Community Cloud**:
   - Go to [Streamlit Community Cloud](https://share.streamlit.io/).
   - Select the repository to deploy.
   - Configure the deployment by selecting `app.py` as the main file.
   - Add the environment secrets via the Streamlit settings.

## Configuration

The application relies on several environment variables to configure the connection to the database and the OpenAI API. These are stored in the `secrets.toml` file:

- **OPENAI_API_KEY**: Your OpenAI API key.
- **DB_USER**: Username for the MySQL database.
- **DB_PASSWORD**: Password for the MySQL database.
- **DB_HOST**: Public IP address of the MySQL instance hosted on AWS.
- **DB_NAME**: Name of the database you want to connect to.
- **DB_PORT** (optional): MySQL database port, default is 3306.

## Running Locally

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yomilshah/SQL-Chatbot.git
   cd SQL-Chatbot
   ```
2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Create a `.env` File**:
   ```bash
   OPENAI_API_KEY=your_openai_api_key
   DB_USER=your_database_username
   DB_PASSWORD=your_database_password
   DB_HOST=your_aws_rds_endpoint
   DB_NAME=your_database_name
   ```
4. **Run the Application**:
   ```bash
   streamlit run app.py
   ```
## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License
This project is licensed under the MIT License.
