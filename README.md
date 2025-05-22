# Conversational SQL Query Chatbot with LangChain and Streamlit

This repository contains a conversational SQL query chatbot built with Streamlit and LangChain, powered by Groq's Llama3-8b-8192 model. Users can interact with a SQLite or MySQL database using natural language queries, with support for a pre-populated `student.db` SQLite database or a user-specified MySQL database.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [File Structure](#file-structure)
- [Setup Instructions](#setup-instructions)
- [Requirements](#requirements)
- [Usage](#usage)
- [License](#license)

## Overview
The project implements a web-based chatbot that allows users to query a database (SQLite or MySQL) using natural language. It leverages LangChain's SQL agent and Groq's Llama3-8b-8192 model to translate user queries into SQL commands and retrieve results. The `student.db` SQLite database, populated with sample student data, is included for local testing, while MySQL connectivity is supported for custom databases. The Streamlit interface maintains chat history and provides real-time query feedback.

## Features
- Streamlit-based chat interface for natural language database queries.
- Supports two database options:
  - SQLite (`student.db`) with pre-populated student data (Name, Class, Section, Marks).
  - MySQL for user-specified databases.
- Powered by Groq's Llama3-8b-8192 model for natural language to SQL translation.
- LangChain SQL agent for query execution and result retrieval.
- Chat history support for seamless user interactions.
- Real-time feedback with StreamlitCallbackHandler for query processing.

## File Structure
```
├── .gitignore              # Git ignore file for excluding unnecessary files
├── LICENSE                 # License file (MIT)
├── README.md               # Project documentation
├── app.py                  # Main application with conversational SQL chatbot
├── sqlite.py               # Script to create and populate student.db SQLite database
├── student.db              # SQLite database with sample student data
└── requirements.txt         # Python dependencies
```

## Setup Instructions
1. **Clone the Repository**
   ```bash
   git clone https://github.com/Monish-Nallagondalla/LLM_Text_To_SQL.git
   cd LLM_Text_To_SQL
   ```

2. **Install Dependencies**
   Ensure you have Python 3.8+ installed. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set Up Environment Variables**
   - Create a `.env` file in the project root:
     ```bash
     touch .env
     ```
   - Add the Groq API key:
     ```plaintext
     GROQ_API_KEY=your_groq_api_key
     ```
   - Obtain the Groq API key from [console.groq.com](https://console.groq.com).

4. **Set Up the SQLite Database**
   - The `student.db` file is included with sample data. To recreate it, run:
     ```bash
     python sqlite.py
     ```
   - This creates a `STUDENT` table with columns (NAME, CLASS, SECTION, MARKS) and inserts sample records.

5. **Set Up MySQL (Optional)**
   - If using MySQL, provide the host, user, password, and database name in the Streamlit sidebar when prompted.

6. **Run the Application**
   ```bash
   streamlit run app.py
   ```

## Requirements
The dependencies are listed in `requirements.txt`. Key packages include:
```
streamlit
langchain
langchain-groq
langchain-community
sqlalchemy
mysql-connector-python
python-dotenv
```

## Usage
1. Launch the Streamlit app using the instructions above.
2. In the sidebar, select either the SQLite (`student.db`) or MySQL database option.
   - For SQLite, no additional setup is needed (uses `student.db`).
   - For MySQL, enter the host, user, password, and database name.
3. Enter your Groq API key in the sidebar's password-protected text input.
4. Type a natural language query in the chat input field (e.g., "Who are the students in Data Science class with marks above 80?").
5. View the chatbot's response, which executes the SQL query and returns the results.
6. Use the "Clear message history" button to reset the conversation if needed.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
