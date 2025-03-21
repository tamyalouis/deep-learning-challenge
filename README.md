# Neural Network Optimization Report

##  Data Preprocessing

###  Target Variable
- The target for the model is the `IS_SUCCESSFUL` column, which indicates whether the applicant successfully used the donated funds.

###  Feature Variables
The features used to train the model include:
- `NAME`
- `APPLICATION_TYPE`
- `AFFILIATION`
- `CLASSIFICATION`
- `USE_CASE`
- `ORGANIZATION`
- `INCOME_AMT`
- `SPECIAL_CONSIDERATIONS`
- `STATUS`
- `ASK_AMT`

These features were encoded using one-hot encoding and scaled using `StandardScaler`.

###  Removed Variables
- `EIN` was removed because it’s simply an identifier and doesn’t provide predictive power.
- `STATUS` was removed because all values were the same (1), making it redundant.
- `SPECIAL_CONSIDERATIONS` was considered for removal since the vast majority of entries had the same value, limiting its impact on prediction.

---

##  Model Architecture

###  Final Neural Network Configuration
- **Input Layer:** Dense layer with 80 neurons, `ReLU` activation
- **Hidden Layer 1:** 30 neurons, `Sigmoid` activation
- **Hidden Layer 2:** (in later variations) 20 neurons, `Sigmoid` activation
- **Output Layer:** 1 neuron, `Sigmoid` activation (for binary classification)
- **Loss Function:** `binary_crossentropy`
- **Optimizer:** `adam`
- **Epochs:** 100–150 (tested different values)

---

##  Model Performance

###  Achieved Accuracy
- The final neural network model achieved an accuracy of **78.9%**, surpassing the target of 75%.
- A **Random Forest classifier** was also tested and reached an accuracy of **77.6%**, making it a strong alternative.

---

##  Optimization Techniques

To improve model performance:
- The `NAME` column was converted to categories and binned to reduce noise.
- Rare values in `APPLICATION_TYPE` and `CLASSIFICATION` were grouped into `"Other"`.
- Multiple model variations were tested, including:
  - Adding a third hidden layer
  - Using `sigmoid` activation in deeper layers
  - Tuning the number of neurons in each layer
  - Increasing epochs from 100 to 150
- A Random Forest classifier was also trained as a comparison model.

---

##  Key Insights

Applicants had a higher likelihood of success if:
- Their `NAME` appeared more than five times (indicating experience or repeat applications)
- Their `APPLICATION_TYPE` was one of the following: `T3`, `T4`, `T5`, `T6`, `T7`, `T8`, `T10`, `T19`
- Their `CLASSIFICATION` fell under: `C1000`, `C2000`, `C3000`, `C1200`, or `C2100`

---

##  Conclusion

Through careful preprocessing, model tuning, and evaluation, we successfully improved model accuracy to nearly **79%**, exceeding the benchmark of 75%. The neural network proved effective, and the Random Forest model is recommended as a strong alternative for classification tasks involving structured tabular data.
