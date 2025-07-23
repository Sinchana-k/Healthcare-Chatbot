# Healthcare-Chatbot
# Medical Chatbot Web Application

This is a Flask-based medical assistant web application that uses NLP and machine learning to identify user symptoms, predict diseases, suggest relevant drugs, and locate nearby hospitals. It also integrates Wikipedia to provide brief summaries of medical conditions.

## Features

- User registration and login system using MySQL
- Symptom extraction using spaCy (NLP)
- Disease prediction based on multiple symptoms using a machine learning model
- Drug suggestions for predicted or user-specified diseases
- Disease lookup based on user-provided drugs
- Wikipedia-based disease summary fetcher
- Hospital suggestion based on user pincode by parsing a government-issued PDF
- Maintains individual user history of predicted diseases

## Technologies Used

- Python 3
- Flask
- MySQL, Flask-MySQLdb
- spaCy (NLP)
- Pandas, PyPDF2, Regular Expressions
- Wikipedia API
- HTML/CSS (Jinja templates)
- CSV-based drug-disease mapping
- BeautifulSoup (used optionally for scraping)

## Project Structure

```
├── app.py                     # Main Flask application
├── medicines.csv              # Dataset mapping diseases to drugs
├── hospitals.pdf              # PDF file containing hospital information
├── symptom_extractor1.py      # Custom NLP-based symptom extraction module
├── disease_predictor1.py      # Disease prediction logic (ML model)
├── templates/
│   ├── login.html             # Login and registration page
│   └── chat1.html             # Main chatbot UI
├── static/                    # Static files (CSS, images, JS)
├── README.md                  # This documentation
```

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/medical-chatbot.git
cd medical-chatbot
```

### 2. Install Python Dependencies

Create a virtual environment (optional but recommended) and install dependencies:

```bash
pip install -r requirements.txt
```

If you don’t have a `requirements.txt`, install these manually:

```bash
pip install flask flask-mysqldb spacy pandas wikipedia-api PyPDF2 beautifulsoup4
python -m spacy download en_core_web_sm
```

### 3. Setup MySQL Database

1. Create a MySQL database named `database1`.
2. Create a user table:

```sql
CREATE TABLE user (
    userid INT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255),
    password VARCHAR(255)
);
```

The application will automatically create additional user-specific tables (e.g., `user_1`, `user_2`) upon registration.

### 4. Required Files

- `medicines.csv`: Contains `disease` and `drug` columns.
- `hospitals.pdf`: Contains hospital listings with pincodes.
- `symptom_extractor1.py`: Should define a function `extract_symptoms(text) -> List[str]`.
- `disease_predictor1.py`: Should define a function `predict_disease(symptoms: List[str]) -> str`.

Ensure these files are in the same directory as `app.py`.

### 5. Run the Application

```bash
python app.py
```

Visit `http://127.0.0.1:5000` in your browser to interact with the chatbot.

## Example Use Case

1. User logs in or registers.
2. Greets the bot: "Hello"
3. Bot replies: "How are you today?"
4. User says: "I'm feeling sick. I have vomiting, nausea, and stomach pain."
5. Bot predicts a disease, provides Wikipedia summary, lists drugs, and optionally suggests hospitals nearby.

## Notes

- This application is a prototype and not a replacement for professional medical advice.
- For production, add HTTPS, password hashing, input sanitization, and proper error handling.
- The session logic uses Flask's built-in secure cookie session.

## License

This project is provided for educational purposes only. Do not use this in production healthcare systems without appropriate validations, clinical input, and compliance with healthcare data standards (e.g., HIPAA, GDPR).
