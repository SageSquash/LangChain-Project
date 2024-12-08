# My LLM API

This project demonstrates a simple API for integrating a Language Learning Model (LLM) powered by **LangChain**, **FastAPI**, and **Google Generative AI (Gemini)**. The API allows users to interact with a chain that can process prompts and output results such as translations or other natural language tasks.

## Features

- **Prompt Templates**: Define customizable templates for user input.
- **Integration with Google Generative AI**: Utilize the power of Google's Gemini-1.5-flash model for processing prompts.
- **Output Parsing**: Parse and format responses effectively using `StrOutputParser`.
- **Extendable API**: Easily extendable for different LLM use cases.

---

## Installation

### Prerequisites

- Python 3.8 or higher
- `pip` package manager

### Steps

  1. Clone this repository

	2.	Install the required dependencies:

pip install -r requirements.txt


	3.	Ensure environment variables are set (e.g., API keys for Google Generative AI):
	•	Use a .env file to load sensitive credentials:

GOOGLE_API_KEY=your_api_key

Usage
	1.	Run the API locally:

uvicorn main:app --host localhost --port 8000


	2.	Access the API:
	•	Base URL: http://localhost:8000
	•	Endpoint: /chain
	3.	Example Request:
	•	Input JSON:

{
  "language": "french",
  "text": "It's a beautiful day"
}


	•	Expected Response:

{
  "result": "C'est une belle journée."
}

Code Structure

Key Components
	1.	Prompt Template:
	•	Created using ChatPromptTemplate.
	•	Allows customization of input and output formats.
Example:

system_template = "Translate the following into {language}:"
prompt_template = ChatPromptTemplate.from_messages([
    ('system', system_template),
    ('user', '{text}')
])


	2.	Model:
	•	Powered by ChatGoogleGenerativeAI:

model = ChatGoogleGenerativeAI(model="gemini-1.5-flash")


	3.	Parser:
	•	Converts model responses into a clean string format:

parser = StrOutputParser()


	4.	Chain:
	•	Combines prompt, model, and parser in a seamless flow:

chain = prompt_template | model | parser


	5.	API:
	•	Uses FastAPI to expose the chain as a RESTful endpoint.

Extending the API
	1.	Add New Tasks:
Update the system_template or create additional endpoints in main.py.
	2.	Integrate New Tools:
Use LangChain’s tools like search or memory for more complex workflows.
	3.	Experiment with Agents:
Combine multiple tools and chains using create_react_agent for advanced agent-based functionality.

Contributions

Contributions are welcome! Feel free to submit issues or pull requests for feature improvements or bug fixes.

License

This project is licensed under the MIT License. See the LICENSE file for details.

Replace placeholders like `yourusername` or `your_api_key` with actual values relevant to your project. This `README.md` provides a clear overview and ensures that others can quickly understand and use your project.
