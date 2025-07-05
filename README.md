# AI-CHATBOT-WITH-


COMPANY: CODTECH IT SOLUTIONS

"NAME: KINGSTON

"INTERN ID: CTO4DG46

"DOMAIN: PYTHON PROGRAMMING

DURATION: 4 WEEEKS

MENTOR: NEELA SANTOSH


Description of the “Python & AI Chatbot” Colab Script (≈ 550 words)
This Google Colab notebook builds a lightweight rule‑and‑similarity chatbot focused on Python programming and artificial‑intelligence topics. With fewer than 80 lines of code it demonstrates how you can combine traditional natural‑language‑processing (NLP) techniques with a minimal rule set to deliver instant Q & A functionality inside an interactive shell.

1 . Environment Setup
The notebook begins by installing spaCy and scikit‑learn, two foundational NLP and machine‑learning libraries, and then downloads the small English language model en_core_web_sm. Although the model is loaded with spacy.load, it is not used for deep linguistic analysis here; its presence simply illustrates how you might extend the bot later with tokenization, part‑of‑speech tagging, or named‑entity recognition.

bash
Copy
Edit
pip install -q spacy scikit-learn
python -m spacy download en_core_web_sm
2 . Knowledge Base (Static Corpus)
At the heart of the system is a hard‑coded knowledge base—an array called corpus containing short declarative sentences about Python, NLP, and chatbots. Each element is phrased as a stand‑alone fact, making it suitable for retrieval via vector similarity. Because the content is domain‑specific, the chatbot can answer only within this narrow scope, which keeps the demo simple and predictable.

#### 3 . Vectorization & Similarity Search
To enable question matching, the script turns the corpus into a TF‑IDF matrix using TfidfVectorizer.

TF‑IDF (Term Frequency × Inverse Document Frequency) transforms each sentence into a high‑dimensional vector where common but uninformative words receive low weight, and rare, content‑rich terms receive high weight.

When a user types a question, the same vectorizer converts that query into a compatible vector.

Cosine similarity then measures how closely the query aligns with each corpus sentence, and the sentence with the highest similarity becomes the response.
A similarity threshold of 0.30 prevents irrelevant matches; if no sentence clears that bar, the bot produces a fallback message prompting the user to rephrase.

#### 4 . Rule‑Based Enhancements
The notebook sprinkles in a tiny rule layer to humanize interactions:

Greeting Detection – If the user’s input contains any token from a predefined tuple ("hello", "hi", "hey", "greetings", "yo"), the bot returns one of three cheerful greetings rather than running the similarity search.

Fallback Phrases – A list of three polite clarifiers—e.g., “I’m not sure about that. Can you ask in a different way?”—ensures the bot never stays silent when it lacks a good match.

Exit Commands – Any input equal to "bye", "exit", or "quit" cleanly ends the loop with a farewell.

These micro‑rules illustrate how hybrid chatbots combine deterministic intent recognition for common conversational rituals with data‑driven retrieval for knowledge delivery.

5 . Interactive Chat Loop
The chat() function provides the command‑line interface:

python
Copy
Edit
while True:
    user_input = input("You: ")
    ...
The loop continues indefinitely until an exit keyword is detected.

Each turn prints the chatbot’s response in the console, giving the user an immediate, low‑latency Q & A experience within Colab’s text cell.

Because the entire corpus resides in memory and TF‑IDF lookup is vectorized, response times remain essentially instantaneous even on Colab’s free tier.

#### 6 . Extensibility
Although intentionally minimal, the architecture is modular:

Expanding Knowledge – Append new domain sentences to corpus, call vectorizer.fit_transform again, and the bot can answer new topics without retraining a neural model.

Deeper NLP – Replace TF‑IDF with spaCy’s built‑in word vectors, Sentence‑BERT embeddings, or an external LLM API to raise answer quality.

GUI – Swap the console loop for a Streamlit or Gradio interface, turning the script into a shareable web app in minutes.

#### 7 . Use Cases & Educational Value
While not production‑grade, this notebook is perfect for:

Classroom demos on vector‑space retrieval and hybrid rule‑based systems.

Rapid prototyping of FAQ bots when data is scarce but domain boundaries are clear.

Self‑study exercises: students can tweak similarity thresholds, add intents, or experiment with alternative vectorizers.

