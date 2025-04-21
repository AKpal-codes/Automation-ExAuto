# ExAuto - Automated Use Case Extractor

**ExAuto.py** is a Python script that automates the extraction of structured *Use Cases* from business documents using a large language model (LLM) hosted on Hugging Face. The results are compiled into a `.docx` document and emailed to a list of recipients.

---

## Features

- Accepts input documents in `.pdf`, `.docx`, or `.txt` formats  
- Uses `HuggingFaceH4/zephyr-7b-beta` for extracting structured use cases  
- Generates a clean, professional `.docx` file  
- Sends the generated document to specified recipients via email  
- Secure credentials using `.env` file  

---

## Installation

1. **Clone the repository:**

   git clone https://github.com/Akpal-codes/ExAuto.git
   cd Automation-ExAuto

Install dependencies:
    - pip install -r requirements.txt

Create a .env file:

HUGGINGFACE_TOKEN=your_huggingface_token
SMTP_SERVER=smtp.example.com
SMTP_PORT=your_port
EMAIL_USERNAME=you@example.com
EMAIL_PASSWORD=your_email_password

## Dependencies
pdfplumber
python-docx
huggingface_hub
tqdm
python-dotenv

Install them via:
    - pip install pdfplumber python-docx huggingface_hub tqdm python-dotenv

## How It Works
1. Read the document
Supports .pdf, .docx, and .txt.

2. Smartly split into chunks
Keeps input size within token limits for the LLM.

3. Extract Use Cases
Uses a predefined prompt to extract the following:

Use Case Title

Actor(s)

Preconditions

Trigger

Main Flow

Alternative Flows

Postconditions

Notes

4. Email the result
Creates a .docx file and sends it to the given recipients.

## Usage

python ExAuto.py --input path/to/your/document.pdf --recipients path/to/recipients.txt

Example:

    python ExAuto.py --input sample_business_doc.docx --recipients recipients.txt

## Output
A file named Extracted_Use_Cases.docx is created in-memory and sent via email.

The format is clean and well-structured for easy reading.

## Notes
Make sure to use app-specific passwords or enable less secure apps if you're using Gmail or similar services.

Ensure your Hugging Face token has access to the HuggingFaceH4/zephyr-7b-beta model.

Invalid email addresses in the recipients file will be automatically ignored with a warning.