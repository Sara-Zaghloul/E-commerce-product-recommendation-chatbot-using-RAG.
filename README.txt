The chatbot assists users in finding electronics products, such as laptops, based on preferences like rating. We utilize the "Amazon US Customer Reviews Dataset" from Kaggle, specifically the Electronics subset, to provide real-world product data and reviews. 
Built with Python, LangChain, FAISS, and Hugging Face transformers, this project demonstrates how AI can enhance online shopping experiences by delivering personalized, context-aware recommendations.

## 🧠 Project Workflow

1. **Dataset**
   - Automatically downloads the *Amazon US Customer Reviews* dataset from Kaggle.
   - Focuses on the **Electronics** subset only.
   - Selects relevant columns:  
     `product_id`, `product_title`, `star_rating`, and `review_body`.

2. **Exploratory Data Analysis (EDA)**
   - Visualizes star rating distribution.  
   - Shows the top 10 most-reviewed products.

3. **Preprocessing**
   - Combines product title, star rating, and review text into one descriptive field
   - Drops missing values and limits the dataset to 2,000 rows for faster experimentation.

4. **Document Creation & Chunking**
   - Converts each row into a LangChain `Document` object.
   - Splits long texts into manageable chunks using `RecursiveCharacterTextSplitter`.

5. **Embedding & Vector Store**
   - Generates dense embeddings using `sentence-transformers/all-MiniLM-L6-v2`.
   - Stores vectors in a **FAISS** vector database for efficient semantic retrieval.

6. **LLM Setup**
   - Uses a Hugging Face pipeline (`distilgpt2`) for text generation.
   - Configured through `HuggingFacePipeline` in LangChain.

7. **RetrievalQA Chain**
   - Retrieves top-2 relevant documents for each query.
   - Generates an answer combining retrieved reviews and model output.
