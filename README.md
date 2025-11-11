UTM Parking Chatbot Project

Overview:
This project implements a question-answering chatbot for the University of Toronto Mississauga (UTM) parking website. It uses semantic search and a local language model (Mistral via Ollama) to answer user questions based on retrieved context from UTM parking-related documents and web data.

Approach:
1. Data Ingestion:
   - Web-scraped parking content and parking rate information from a .txt file are cleaned and chunked using overlap-aware token-based splitting.
   - Chunks are embedded using a sentence transformer model and stored in a ChromaDB collection for semantic retrieval.
Additional Resources: 
    - RAG: https://www.youtube.com/watch?v=swvzKSOEluc 
    - ChromaDB: https://www.youtube.com/watch?v=qn738hVKJe4 

2. Question Answering:
   - User questions are embedded and matched against stored chunks using cosine similarity.
   - Top-ranked context chunks are used to construct a prompt for the Mistral model via the Ollama CLI.
   - The model answers strictly based on the retrieved context. If no relevant answer is found, a fallback message with a reference URL is returned.

3. Evaluation:
   - A set of test questions is processed with a progress bar.
   - Results are saved to JSON and CSV files.
   - Visualizations include a pie chart for fallback detection frequency and a bar chart for response time per question.

4. Final Outcome:
- A working chatbot interface served via Flask.
- Evaluation results saved in 'parking_test_results.json' and 'parking_test_results.csv'.
- Interactive charts saved as HTML files for fallback detection and response time analysis.

Reproduction Instructions:
1. Clone the repository and ensure the following structure:
   ├── templates/
   │   └── chat.html
   ├── static/
   │   └── (optional CSS)
   ├── data/
   │   ├── fallback_detection_pie.html
   |   |__ fallback_detection_pie.json
   |   |__ parking_test_questions.json   
   │   ├── parking_test_results.csv   
   │   ├── parking_test_results.json
   |   |__ response_time_bar.html
   |   |__ response_time_bar.json
   │   ├── utm_parking_data.csv
   │   └── utm_parking_rates.txt
   ├── src/
   │   └── chatbot_notebook.ipynb
   

2. Install dependencies:
   pip install flask sentence-transformers chromadb scikit-learn plotly tqdm

   Required packages include:   
   - sentence-transformers
   - chromadb
   - ollama (CLI tool): visit https://ollama.com/ to install, add to PATH and run ollama pull mistral
   - scikit-learn
   - plotly
   - tqdm
   - flask

3. Evaluate:
   - Run the notebook to process test questions and generate results.
   - View charts in the 'data/' directory. 

4. Run the chatbot:
   - Launch the Flask app from the notebook
   - Open http://127.0.0.1:5000 in your browser

5. Next steps:
- Explore RAG performance improvement strategies: https://www.datacamp.com/tutorial/how-to-improve-rag-performance-5-key-techniques-with-examples 
- Explore inference optimization techniques: https://bentoml.com/llm/inference-optimization 

6. Video presentation of the project can be viewed here: https://utoronto-my.sharepoint.com/:v:/g/personal/anna_mozharova_utoronto_ca/EcoRw1TWBd9PrF5Az8BkqVYBzbNO6ousageIj0Yb_x3pGw?e=9IeUOe 