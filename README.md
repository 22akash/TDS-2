# LLM-Based Assignment Answering API

## Overview

This project is an LLM-based application designed to simplify the process of answering graded assignment questions. The application exposes an API that accepts questions related to five specific graded assignments and responds with the appropriate answers. The API can also handle optional file attachments, allowing users to submit relevant documents alongside their questions.

## API Endpoint

The API is hosted at the following endpoint:

```
POST http://127.0.0.1:5000/api
```

### Request Format

The API accepts a POST request with the following parameters:

- **question**: A string containing the assignment question.
- **file**: An optional file attachment in multipart/form-data format.

### Example Request

Here’s an example of how to make a request using `curl`:

```bash
curl -X POST "http://127.0.0.1:5000/api/" \
  -H "Content-Type: multipart/form-data" \
  -F "question=Download and unzip file abcd.zip which has a single extract.csv file inside. What is the value in the 'answer' column of the CSV file?" \
  -F "file=@abcd.zip"
```

### Response Format

The API responds with a JSON object containing the answer:

```json
{
  "answer": "1234567890"
}
```

## Project Structure

The project consists of the following files:

- `main.py`: The main application file containing the API logic.
- `requirements.txt`: A file listing the required Python packages for the project.

## Environment Variables

To run the application, you need to create a `.env` file in the root directory of the project. This file should contain the following values:

```
API_KEY=""  #API KEY of the LLM that you wanted to use
G_TOKEN=""
GITHUB_USERNAME=""
GITHUB_REPO_NAME="tds-2"
tinify_api_key=""  # Tinify API key for image compression
model=""            # Model to be used from your LLM (e.g., gpt-4o for Openai)
base_url=""        # Model fetching URL
```

Make sure to replace the empty strings with your actual API keys and configuration values.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/22akash/TDS-2.git
   cd TDS-2
   ```

2. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required packages:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file and populate it with the necessary environment variables.

5. Run the application:

   ```bash
   python main.py
   ```

## Usage

Once the application is running, you can make POST requests to the API endpoint with your questions and optional file attachments as described above.

## Contributing

Contributions are welcome! If you have suggestions for improvements or new features, please open an issue or submit a pull request.
