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

## 🔬 Methodology

1. Load each model using Hugging Face Transformers.  
2. Use the same input prompt for all models.  
3. Generate 50 tokens and measure:
   - Latency  
   - Throughput (tokens/sec)  
   - Perplexity  
4. Collect model size and parameter count from metadata.  
5. Apply TOPSIS:
   - Normalize data  
   - Apply weights  
   - Compute ideal best and worst  
   - Calculate TOPSIS score  
   - Rank models based on score  

**TOPSIS Formula:**
Score = S_worst / (S_best + S_worst)

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

**[ Insert Graph Here ]**

(Bar chart comparing tokens per second for each model)

### 🔹 Graph 2: Overall TOPSIS Ranking

**[ Insert Graph Here ]**

(Bar chart showing TOPSIS score for each model, sorted by rank)

## 💡 Conclusion

This analysis shows that no single model is best in all aspects. The **TOPSIS method** combines multiple criteria into a single score, helping to select the most balanced model for practical use.

---

**Assignment submitted for UCS654** ✅

