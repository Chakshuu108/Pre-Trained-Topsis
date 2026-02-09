# 🤖 TOPSIS Model Evaluation for Text Generation

**Roll Number:** 102303931  
**Task:** Text Generation

## 📋 Overview

This project uses the **TOPSIS (Technique for Order of Preference by Similarity to Ideal Solution)** method to evaluate and rank different pre-trained language models for text generation. The goal is to identify the best overall model by considering multiple factors such as size, speed, and quality.

## 🎯 Models Evaluated

- GPT-2  
- DistilGPT-2  
- Facebook OPT-350M  
- EleutherAI GPT-Neo-125M  
- Facebook OPT-125M  

## ⚖️ Evaluation Criteria

- **Parameters** (Negative impact – fewer is better)  
- **Model Size (MB)** (Negative impact – smaller is better)  
- **Latency (s)** (Negative impact – lower is better)  
- **Tokens per Second** (Positive impact – higher is better)  
- **Perplexity** (Negative impact – lower is better)  

**Weights:** All criteria are equally weighted (0.2 each).

## 🧩 Code Pipeline (Workflow)

1. **Import Libraries**
   - Load PyTorch, Transformers, NumPy, Pandas, Matplotlib, etc.

2. **Define Models List**
   - Specify the names of all models to be evaluated.

3. **Load Model and Tokenizer**
   - Load each model using Hugging Face Transformers.
   - Move model to GPU if available, else CPU.

4. **Prepare Input Text**
   - Use the same fixed prompt for all models to ensure fair comparison.

5. **Warm-up Run**
   - Run one generation pass to stabilize performance (especially on GPU).

6. **Measure Performance**
   - Generate 50 tokens.
   - Measure:
     - Latency (time taken)
     - Tokens per second (throughput)
     - Perplexity (using loss)
   - Collect:
     - Model size (MB)
     - Number of parameters

7. **Create Decision Matrix**
   - Store all metrics for all models in a table (Pandas DataFrame).

8. **Apply TOPSIS**
   - Normalize the decision matrix.
   - Apply weights to each criterion.
   - Determine ideal best and ideal worst.
   - Compute distance from best and worst.
   - Calculate TOPSIS score:
     ```
     Score = S_worst / (S_best + S_worst)
     ```
   - Rank models based on the score.

9. **Save Results**
   - Export final table with scores and ranks to:
     ```
     topsis_text_generation_results.csv
     ```

10. **Generate Graphs**
    - Bar chart: Tokens per Second vs Models
    - Bar chart: TOPSIS Score vs Models (sorted by rank)

## 🔬 Methodology (Short)

1. Load each model using Hugging Face Transformers.  
2. Use the same input prompt for all models.  
3. Generate 50 tokens and measure:
   - Latency  
   - Throughput (tokens/sec)  
   - Perplexity  
4. Collect model size and parameter count.  
5. Apply TOPSIS to rank the models.

## 📊 Results

Results are saved in:

`topsis_text_generation_results.csv`

The file contains:
- Model name  
- Parameters  
- Model size (MB)  
- Latency (s)  
- Tokens per second  
- Perplexity  
- TOPSIS score  
- Rank  

## 📉 Visualizations

### 🔹 Graph 1: Generation Speed (Tokens per Second)

**<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/7dcfb929-cd70-47a6-b0fd-d243d61585ed" />
**

(Bar chart comparing tokens per second for each model)

### 🔹 Graph 2: Overall TOPSIS Ranking

**<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/a36a5753-efe1-4ff3-91c6-c26c9dd20a1a" />
**

(Bar chart showing TOPSIS score for each model, sorted by rank)

## 💡 Conclusion

This analysis shows that no single model is best in all aspects. The **TOPSIS method** combines multiple criteria into a single score, helping to select the most balanced model for practical use.

---

**Assignment submitted for UCS654** ✅
