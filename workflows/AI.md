# AI Projects Workflow

## 1. Planning
- Identify the **problem**: need to detect X using Y
- Find suitable **model, dataset, deploytment pipeline** (using AI or reddit)

---

## 2. Datasets
- Collect -> Explore -> Clean -> Augment -> Split (Use AI for public dataset recommendations)

---

## 3. Selecting Models
- Requirements (e.g. real-time, <50 MB, high precision,...) -> Candidate models -> Compare these models -> Decide the model used for the project.

---

## 4. Training (no AI agent can do this)
**- Although no AI can train model for you. AI agents might help:**
+ Explain hyperparameters (epochs, batch, lr, weight_decay,...)
+ Interpret logs (Training log:... What is that?)
+ Suggest improvements while training (Validation loss increases. Why?)
+ Error Analysis (Model often misses small objects. Why?)

---

## 5. Evaluation
- Interpret (Confusion Matrix, Precision Recall Curve,...)
- Explain (Why recall is low?,...)
- Suggest Improvements

---

## 6. Deployment
- Save the model -> Inference API (AI could help generating FastAPI wrapper) -> Frontend (AI could help generating Streamlit/Gradio demo) -> Deploy

---

## 7. Finishing with Tech Reports/README on github

