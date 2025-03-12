
# Transaction Category Classification with DistilBERT

##  Project Overview

This project fine-tunes a DistilBERT uncased model to classify transaction descriptions into predefined categories. The model is trained on a dataset containing transaction descriptions and their respective categories. It is then deployed using FastAPI for real-time inference.
## Folder Structure

The project is organized into the following directories:

app/                 # Application-related files (if any)  
data/                # Dataset storage  
  ├── transaction_dataset/  
  │   ├── label_to_category.json  # Mapping of labels to categories  
  │   ├── transactions.csv        # Transaction dataset  
models/              # Trained model storage  
script/              # Training and preprocessing scripts  
  ├── preprocess.py  # Data preprocessing  
  ├── train_model.py # Model training  
.env                 # Environment variables (if applicable)  
.gitignore           # Git ignore file  
config.json          # Configuration settings  
requirements.txt     # Required dependencies  

## Key Achievements

- Fine-tuned DistilBERT on transaction descriptions and categories.
- Preprocessed the dataset for optimal training efficiency.
- Deployed a FastAPI endpoint for real-time category predictions.
- Locally downloaded model for faster and cost-effective training.
## Setup

1. Install Dependencies
Ensure you have Python installed, then run:

```bash
pip install -r requirements.txt
```

2. Dataset
Place your transaction dataset (transactions.csv) inside data/transaction_dataset/. The dataset should have the following format:


| Description |	Category |
| :---------: | :--------: | 
|"Grocery shopping at Walmart" |	"Food"|
|"Monthly rent payment" |	"Housing" |

A label_to_category.json file should be present to map category labels to their names.

3. Model Training
Run the preprocessing and training scripts:

```bash
python script/preprocess.py
python script/train_model.py
```

This will:

- Preprocess the dataset (tokenization, text cleaning).
- Load DistilBERT uncased model from a local Hugging Face cache.
- Fine-tune the model on transaction descriptions and categories.
- Save the trained model in the models/ directory.

4. Deployment with FastAPI
Start the FastAPI server with:

```bash
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

5. API Endpoints
Once running, you can interact with the API:

- Classify a transaction description
```bash
curl -X 'POST' \
  'http://127.0.0.1:8000/predict' \
  -H 'Content-Type: application/json' \
  -d '{"description": "Bought coffee at Starbucks"}'
```

Response:

```json
{
  "category": "Food & Beverage"
}
```

Future Improvements
- Enhance dataset with more diverse transactions.
- Deploy using Docker & Azure for scalability.
- Improve classification performance using hyperparameter tuning.

## Conclusion

This project successfully fine-tunes a DistilBERT uncased model for transaction category classification using transaction descriptions as input. The model is trained on a labeled dataset and deployed via FastAPI for real-time predictions.

By leveraging Hugging Face Transformers, the project benefits from state-of-the-art NLP capabilities while ensuring efficient inference through DistilBERT's lightweight architecture. The API integration allows seamless interaction, making it suitable for financial applications, expense tracking, and automated categorization systems.
## Folder Structure

The project is organized into the following directories:

app/                 # Application-related files (if any)  
data/                # Dataset storage  
  ├── transaction_dataset/  
  │   ├── label_to_category.json  # Mapping of labels to categories  
  │   ├── transactions.csv        # Transaction dataset  
models/              # Trained model storage  
script/              # Training and preprocessing scripts  
  ├── preprocess.py  # Data preprocessing  
  ├── train_model.py # Model training  
.env                 # Environment variables (if applicable)  
.gitignore           # Git ignore file  
config.json          # Configuration settings  
requirements.txt     # Required dependencies  
