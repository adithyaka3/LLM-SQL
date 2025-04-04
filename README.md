# Query Classification for Rupay/UPI Database

## Goal:
The objective of this project is to classify queries as **Relevant** or **Non-Relevant** based on their relationship with the Rupay/UPI database. Relevant queries are specific to Rupay/UPI, while non-relevant queries are unrelated.

## Implementation:
In this project, a **Transformer model** has been trained on approximately **400 queries** related to the Rupay/UPI database. The model is then tested on a few **handcrafted queries** to evaluate its performance in distinguishing relevant and non-relevant queries.

### Libraries:
To run the code, the following library must be installed using pip:

```bash
pip install sentence-transformers
```

The following models were tested:

### 1. `all-roberta-large-v1`:
- **Description**: Despite being trained only on relevant queries, this model was able to perform very well on the `simple.csv`, `medium.csv`, and `hard.csv` test cases.
- **Pros**:
  - **High Accuracy**: This model offers very high accuracy due to its large size and extensive pretraining, making it effective for tasks requiring deep semantic understanding.
- **Cons**:
  - **Large Size**: `all-roberta-large-v1` is a **large model**, which demands significant computational resources for both training and inference.
  - **Slow Testing Speed**: Due to the model's size, the testing process can take considerable time, making it less efficient for real-time applications or scenarios requiring fast predictions.

### 2. `all-MiniLM-L12-v2`:
- **Description**: `all-MiniLM-L12-v2` is a smaller and more efficient model. It gave similar results compared to the above model with only slightly worser results. The advantage however is that it trains very fast and provides quick results.
- **Pros**:
  - **Fast Inference**: `all-MiniLM-L12-v2` is optimized for fast predictions, making it suitable for real-time applications or environments with limited resources.
  - **Good Accuracy**: While not as high-performing as larger models like `all-roberta-large-v1`, it still provides good results, especially on negative query classifications.
  - **Resource Efficient**: The smaller size of the model allows for faster loading and lower memory usage compared to larger transformer models.
- **Cons**:
  - **Slightly Lower Performance**: On certain test cases (e.g., `simple.csv`, `medium.csv`, and `hard.csv`), `all-MiniLM-L12-v2` performs slightly worse than `all-roberta-large-v1`. However, the difference is not drastic, and the performance can be comparable, especially when tested with a larger dataset.
  - **Limited Fine-Tuning Potential**: While the model works well out of the box, it may require more fine-tuning with a larger dataset to achieve optimal performance for specific tasks.

### Further Considerations:

With a larger dataset, consider using RoBERTa or DeBERTa for better accuracy. Both models have shown strong performance in NLP tasks.

Additionally, applying **PEFT** or **LoRA** hyperparameter fine-tuning could enhance the model's efficiency and results, especially for large transformer models like RoBERTa and DeBERTa.


