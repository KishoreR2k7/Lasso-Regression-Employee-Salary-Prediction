# Salary Prediction using Lasso Regression  

## 📌 Project Overview  
This project demonstrates how **Lasso Regression** can be applied for **feature selection** in predicting salaries.  
We use **LassoCV (Lasso with Cross-Validation)** to automatically shrink unnecessary features to zero and compare the results with a standard **Linear Regression model**.  

---

## 📂 Dataset  
The dataset `salary_lasso.csv` contains the following features:  

- `experience`  
- `education_level`  
- `certifications`  
- `skills_score`  
- `projects_handled`  
- `leadership_score`  
- `communication_score`  
- `location_index`  
- `department_index`  
- **Target:** `salary_k` (salary in thousands)  

---

## ⚙️ Steps Performed  

1. **Data Preparation**  
   - Features (`X`) = Employee attributes  
   - Target (`y`) = `salary_k`  
   - Train-test split (80% training, 20% testing)  

2. **Modeling**  
   - Fit a **LassoCV** model with 5-fold cross-validation  
   - Identify non-zero coefficients (selected features)  
   - Fit a **Linear Regression** model using all features  

3. **Comparison**  
   - Compare coefficients from both models  
   - Evaluate R² scores on training and testing sets  

---

## 📊 Results  

### 🔹 Selected Features by Lasso (non-zero coefficients)  
experience 2.94
education_level 0.89
certifications 0.01
skills_score 0.99
projects_handled 0.28
leadership_score 1.80
communication_score -0.18
location_index 2.76
department_index 0.00 (removed)

yaml
Copy
Edit

---

### 🔹 Model Coefficients Comparison  

**With Unnecessary Features (Linear Regression):**
experience 2.95
education_level 1.14
certifications 0.28
skills_score 1.09
projects_handled 0.28
leadership_score 1.95
communication_score -0.29
location_index 3.26
department_index -0.27

java
Copy
Edit

**Without Unnecessary Features (Lasso Regression):**
experience 2.94
education_level 0.89
certifications 0.01
skills_score 0.99
projects_handled 0.28
leadership_score 1.80
communication_score -0.18
location_index 2.76
department_index 0.00

yaml
Copy
Edit

---

### 🔹 R² Score Comparison  

| Model                                    | Train R² | Test R² |
|------------------------------------------|----------|---------|
| Linear Regression (all features)         | 0.82     | 0.86    |
| Lasso Regression (selected features)     | 0.82     | 0.86    |

---

## ✅ Conclusion  
- **Lasso Regression successfully removed the unnecessary feature** (`department_index`) without reducing accuracy.  
- Both models achieved an **R² score of ~0.86 on test data**, showing that **simpler models with fewer features can perform equally well**.  
