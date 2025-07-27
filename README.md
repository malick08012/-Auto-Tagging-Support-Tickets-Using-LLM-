# Auto-Tagging Customer Support Tickets with Large Language Models (LLMs)

Automated Support Ticket Tagging with LLMs! 🚀 Explore Zero-shot, Few-shot, and Fine-tuning techniques for efficient text classification and better customer service insights.

## Objective:

The primary goal of this project was to **automatically categorize free-text customer support tickets into predefined categories (tags) using advanced Large Language Models (LLMs)**. This aims to streamline customer support operations by enhancing efficiency in ticket routing and providing quicker insights into common customer issues.

## Methodology / Approach:

This project explored three distinct LLM-based approaches for text classification, building a comprehensive pipeline from data preparation to model evaluation:

1.  **Data Preparation:**
    * Loaded and preprocessed the `customer_support_tickets.csv` dataset, including handling missing values and standardizing column names.
    * Split the dataset into training, validation, and test sets to ensure robust model development and unbiased evaluation.
    * Set up the necessary tokenizer (`distilbert-base-uncased`) and created label-to-ID mappings for efficient LLM processing.
    * Formatted the data into tokenized `Hugging Face Datasets` objects, ready for model input.

2.  **Zero-Shot Learning:**
    * Utilized a pre-trained general-purpose LLM (`facebook/bart-large-mnli`) to classify support tickets **without any specific training** on our dataset. This approach leverages the model's vast pre-existing knowledge for immediate application.

3.  **Few-Shot Learning:**
    * Employed a generative LLM (`google/flan-t5-small`) and **prompt engineering** techniques. A small number of example ticket-tag pairs were included directly within the prompt to guide the model in classifying new, unseen tickets.

4.  **Fine-Tuning:**
    * The most specialized approach involved **fine-tuning** a smaller, task-specific LLM (`distilbert-base-uncased`) directly on our labeled training data. This allowed the model to adapt its internal representations specifically to the language and patterns present in our support tickets. Training was optimized for speed (e.g., 1 epoch, mixed precision).

5.  **Performance Evaluation & Comparison:**
    * The Top-1 accuracy of each implemented methodology (Zero-Shot, Few-Shot, and Fine-Tuning) was evaluated on a subset of the test dataset.
    * The results were then compared to understand the strengths and weaknesses of each approach for this specific auto-tagging task.


## Key Results & Observations:

After implementing and evaluating all three methodologies on a subset of the test data (50 samples for Zero-Shot and Few-Shot), the following Top-1 accuracies were observed:

* **Zero-Shot Learning:** ~6.00% Accuracy
* **Few-Shot Learning:** ~6.00% Accuracy
* **Fine-tuned Model:** ~6.45% Accuracy

**Insights:**:

* **Initial Low Performance:** All three approaches yielded relatively low accuracies (around 6%), which is close to random guessing for 16 unique categories (approx. 6.25%). This indicates that the task may be challenging due to nuances in the ticket descriptions, or that the models required more extensive training.
* **Fine-Tuning's Edge:** Despite the overall low scores, the fine-tuned model performed marginally better. This underscores the general principle that fine-tuning is typically the most effective method for domain-specific text classification, as it allows the LLM to learn the unique patterns of the target dataset.
* **Prompt Engineering Limitations:** While valuable for quick baselines, Zero-Shot and simple Few-Shot prompt engineering may struggle with highly specialized or ambiguous text data without more sophisticated prompting strategies or larger, more context-aware generative models.
* **Need for Iteration:** Achieving higher performance would require further iterative development, including:
    * Increasing the number of fine-tuning epochs.
    * Potentially experimenting with larger base models.
    * Thorough hyperparameter tuning.
    * A deeper dive into data quality, class balance, and potential ambiguities in the labels.

This project successfully demonstrates the foundational steps and methodologies for LLM-based auto-tagging, providing a solid starting point for building more robust and accurate solutions.


**Dataset**:

**LINK**:https://www.kaggle.com/datasets/suraj520/customer-support-ticket-dataset
