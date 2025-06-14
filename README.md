# 🏦 Credit Risk Scoring Model

This project builds a predictive model to assess the risk of credit default using supervised machine learning techniques. It simulates a real-world use case in financial risk management, aligning with the core responsibilities of Global Risk Management teams in the banking sector.

## 📌 Objective

To predict whether a loan applicant is likely to default based on their financial and demographic attributes, and extract key risk factors to inform credit decision-making strategies.

## 📁 Dataset

- **Source**: [German Credit Dataset - UCI Repository](https://archive.ics.uci.edu/ml/datasets/statlog+(german+credit+data))  
- **Observations**: 1,000 loan applicants  
- **Features**: Credit history, loan purpose, employment length, savings account status, personal status, etc.  
- **Target**: Binary (1 = Good credit, 0 = Bad credit)

## ⚙️ Tools & Technologies

- Python 3.9  
- pandas, numpy, matplotlib, seaborn  
- scikit-learn for modeling  
- (Optional) Tableau or Power BI for dashboard visualization

## 🔍 Workflow

1. **Data Preprocessing**  
   - Cleaned missing values  
   - Encoded categorical variables  
   - Normalized numeric fields  

2. **Exploratory Data Analysis (EDA)**  
   - Analyzed default rates by credit history, employment, and loan purpose  
   - Visualized correlations and class imbalances  

3. **Feature Engineering**  
   - Created new financial ratios and risk indicators  
   - Selected top predictors using mutual information and feature importance  

4. **Modeling**  
   - Trained Logistic Regression and Random Forest classifiers  
   - Evaluated performance using ROC-AUC, F1-score, and confusion matrix  

5. **Business Insights**  
   - Identified top risk signals: poor credit history, high loan amount, low savings  
   - Recommended use of model for pre-screening high-risk applicants

## 📊 Results

- **Best model**: Logistic Regression with 78% ROC-AUC  
- **Insight**: Applicants with poor credit history and low savings were 3× more likely to default

## 📈 Future Improvements

- Test with larger, more diverse datasets (e.g., LendingClub)  
- Incorporate time-based features (e.g., payment delay trend)  
- Deploy as an interactive Streamlit or Flask app

## 🤝 Relevance to Risk Management

This project reflects the kind of quantitative and analytical work done in financial institutions to support:
- Credit risk modeling  
- Decision-making frameworks  
- Risk flagging systems  

## 📎 Author

Ngoc Lam|🧠 Computer Science & Data Science @ UVA  