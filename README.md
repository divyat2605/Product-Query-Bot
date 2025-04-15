# Product-Query-Bot
# 🧠 Product Query Bot using Semantic Search 

This project is a smart chatbot that helps users get product recommendations from a dataset using meaningful search (semantic search), rather than keyword matching. It processes a list of products, understands user questions, and fetches relevant information using AI.

---

## 🚀 Features

- Understands product-related questions, even if keywords don't match exactly.
- Fetches and returns the best-matched products with IDs.
- Uses a local machine learning model to understand meaning of text.
- Fast and efficient — no cloud databases or extra libraries used.
- Built using FastAPI for easy integration and testing.

---
2. Install Dependencies
Make sure Python 3.8 or above is installed. Then run:

pip install -r requirements.txt

Required packages include:

fastapi

uvicorn

google-generativeai

faiss-cpu

sentence-transformers

pyngrok

You can also install them manually:
pip install fastapi uvicorn google-generativeai faiss-cpu sentence-transformers pyngrok

3. Get Your Gemini API Key
Go to Google AI Studio

Sign in and generate your API key.

Then, set it in your code (main.py) like this:

python

GOOGLE_API_KEY = "your-api-key-here"
🧪 How to Run the App
Step 1: Start the Server

python main.py
This will:

Load the product data.

Prepare it for search.

Start a local server at http://127.0.0.1:8000

Step 2: Test the API
You can use Postman, cURL, or any tool to test.

Example API call:


POST http://127.0.0.1:8000/query
Content-Type: application/json

{
  "query": "Show me phones with great cameras"  ##Query is subjective to the product details provided
}
Sample Response:


{
  "answer": "Based on the information, the products that match your query are product IDs: 0, 1",
  "product_ids": [0, 1]
}
🧩 Design Decisions 
1. Chunking Strategy
We break long text into small pieces (chunks) of 200 characters with an overlap of 30 characters. This helps preserve meaning when we cut the data and ensures we don’t lose context between chunks.

Think of it like reading a paragraph in parts — by repeating a few lines between chunks, you don’t lose the flow.

2. Understanding Text (Embeddings)
We use a tool called SentenceTransformer which turns chunks of text into number lists that represent the meaning. These are stored and compared later.

It's like converting every sentence into a special fingerprint that captures its meaning.

3. Fast Searching (FAISS)
FAISS is a tool that helps us quickly find the most similar text chunks to a user’s question. It compares the "meaning fingerprints" and tells us which ones are closest.

Like asking a friend to pick the 3 most similar meanings from a pile of notes.

4. Answering the Question (LLM)
We give the matching chunks and the user's question to Google's Gemini Pro, and it crafts a proper human-like answer using only the provided info.

It doesn’t guess — it answers only based on what it’s told, just like answering from a textbook.

5. API Design
We used FastAPI because it’s:

Easy to set up.

Fast.

Clean for creating web-based APIs.
🌐 Optional: Make It Public (Ngrok)
To share your project with someone over the internet:

ngrok http 8000
This gives you a public link like:

https://abc123.ngrok.io/query

👋 Author
Divya Tripathi

2nd Year B.Tech CSE Student @ SRM University

Passionate about AI, Machine Learning, and solving real-world problems with code ❤️

📝 License
This project is for educational and internship evaluation purposes.
