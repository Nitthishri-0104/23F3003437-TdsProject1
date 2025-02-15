# FastAPI Automation Agent

## Overview
This project is a FastAPI-based automation agent designed to execute predefined tasks based on natural language instructions. It supports various operations such as formatting files, querying databases, extracting text from images, running scripts, and more.

## Features
- Exposes API endpoints for executing automated tasks.
- Uses `gpt-4o-mini` for task classification.
- Supports file processing, text extraction, and database queries.
- Runs within a Docker container for portability.
- Implements CORS middleware for cross-origin requests.

## Requirements
- Python >= 3.13
- The following dependencies:
  ```bash
  fastapi
  uvicorn
  requests
  pandas
  openai
  Pillow
  pytesseract
  sentence-transformers
  ```

## Installation
### Clone the repository:
```bash
git clone <repository_url>
cd <repository_name>
```

### Install dependencies:
```bash
pip install -r requirements.txt
```

### Set environment variables:
```bash
export AIPROXY_TOKEN=<your_openai_api_key>
```

## Usage
### Start the API server
Run the FastAPI server using Uvicorn:
```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

## API Endpoints
### Home
**GET /**
#### Response:
```json
{"message": "Yay TDS Tuesday is awesome."}
```

### Read a File
**GET /read?path=<file_path>**
Retrieves the content of a specified file.

### Run a Task
**POST /run?task=<task_description>**
Executes a specified task based on classification.

#### Example Tasks
- Install `uv` and run `datagen.py`
- Format files using Prettier
- Count the number of Wednesdays in a dataset
- Sort contacts
- Extract email senders, credit card details, and H1 titles
- Compute total sales for gold tickets

## Running in Docker
### Build the Docker image:
```bash
docker build -t fastapi-agent .
```
Or use Podman:
```bash
podman build -t fastapi-agent .
```

### Run the container:
```bash
docker run -p 8000:8000 --env AIPROXY_TOKEN=<your_openai_api_key> fastapi-agent
```
Or use Podman:
```bash
podman run -p 8000:8000 --env AIPROXY_TOKEN=<your_openai_api_key> fastapi-agent
```

## Contributing
Pull requests are welcome. Please follow best practices and submit an issue before making significant changes.

## License
This project is licensed under the MIT License.
