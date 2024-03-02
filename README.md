# MULTIVARIATE NON-LINEAR EQUATION MACHINE LEARNING LIMIT TESTING

# ► What the project does

Firstly, this project examines the capability of Polynomial Regression, Random Forest Regression, and Ridge Regression to predict a target variable that is generated via a precise equation (multivariate and non-linear). Variants of the formula are examined in order to evaluate the sensitivity of each model to the different parts of the equation. Modelization is performed on both a clean and a noisy version of the data. These equations are:
- $y_0 = 0.45 \cdot x_1 + 5$<br>
- $y_1 = -0.35 \cdot x_2 + 5$<br>
- $y_2 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 5$<br>
- $y_3 = 0.7 \cdot x_3^2 + 5$<br>
- $y_4 = - x_4^{-1} + 5$<br>
- $y_5 = |x_5| + 5$<br>
- $y_6 = 2 \cdot x_6 \cdot x_7 + 5$<br>
- $y_7 = 1.2 \cdot x_8^{3.5} + 5$<br>
- $y_8 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 0.7 \cdot x_3^2 - x_4^{-1} + |x_5| + 2 \cdot  x_6 \cdot x_7 + 1.2 \cdot x_8^{3.5} + 5$
- Note: a final noise variable is added in some simulations. This is an " $x_9$ " external to the equations.

Secondly, this project examines whether polynomial features (of degree 2) can be used successfully with a Random Forest Regression with equation $y_6$. This is performed via recursive feature elimination (RFE), manually selected polynomial features, and finally the precise features used in the equations (excluding the coefficients, eg. 0.45, -0.35, 0.7, etc.).

# ► The interest of the project

The ability to understand the limits of Polynomial Regression, Random Forest Regression, and Ridge Regression is essential to selecting the proper model in any machine learning project involving continuous data. Nonlinear behavior is particularly difficult to take into account.

**Global analysis:**
- Random Forest Regression is excellent at making predictions for non-linear, multivariate systems but it suffers when a system involves too many features, though the score is still quite good. Adding polynomial features improves overall performance, but not on individual features.
- Polynomial Regression can struggle with certain features that do not fall into the traditional polynomial structure, but can perform better than Random Forest Regression when the system involves many features.
- Ridge Regression struggles with non-linear and multivariate systems until polynomial features are added, which puts its performance at a level similar to polynomial Regression.
- Augmenting polynomial features to degree 3 and 4 do not result in significantly improved results and likely overfit the data.
- A single feature containing only random noise may not always have a big impact. In this project it has a < 1% negative result.
- The best model for the full equation $y_8$ is a tie between Polynomial Regression and Ridge Regression with polynomial features. 

**Analysis of individual features:**
- $x_1$ and $x_2$ linear features are predicted well by all models, though the combination of the two strangely has better results than each individual feature.
- $x_3^2$ squared feature is predicted well by all models.
- $x_4^{-1}$ inverse feature is predicted well by Random Forest, ok by Polynomial Regression, poorly by Ridge and ok by Ridge with polynomial features. A combination of polynomial features manages to approximate this inverse feature.
- $|x_5|$ absolute value feature is predicted well by Random Forest and Polynomial Regression and Ridge with polynomial features. Standard Ridge is totally unable to predict it. Random Forest is best. In the range of -1 to 1, $|x_5|$ is successfully modelled with $x_5^2$.
- $x_6 \cdot x_7$ is predicted well by Random Forest, Polynomial Regression and Ridge Regression with polynomial features. Standard Ridge only performs ok.
- $x_8^{3.5}$ non-integer polynomial is predicted well by Random Forest, Polynomial Regression, and Ridge Regression with polynomial features. Standard Ridge only performs ok.

**Analysis of Recursive Feature Elimination on noisy data**
- As applied to a light Random Forest (10 estimators) selecting polynomial features of degree 2 and then verified with a Random Forest (100 estimators), performance is increased from and R2-score of 0.892 to 0.927. This appears to be overfitting since the automatically selected features are quite different from the actual features. A manual selection of the polynomial features yields a lower R2-score of 0.913, while a selection of precise features (applying all the proper powers to each feature) yields 0.911. Replacing the $x_5$ feature with $x_5^2$ improves the R2-score to 0.923. This may not be overfitting as we know that this transformation of $x_5$ is a reasonable approximation.
- Trying Linear Regression with the same manual selection of the precise features (applying all the proper powers to each feature), the result is poorer: R2-score of 0.805. By adjusting the $x_5$ feature to $x_5^2$, the performance is significantly improved to 0.952. This could be considered to be the baseline best model with the least overfitting.
- Ridge Regression behaves in the exact same manner as Linear Regression.

# ► How to Install and Run the Project

## Installation

### *Prerequisites:*
1.	Python 3.10.13 environment
2.	Jupyter Notebook (version 7.0.6 is installed via requirements.txt)
3.	Anaconda
   
### *Files:*
1.	Multivariate_NonLinear_Equation_Machine_Learning_Limit_Testing.ipynb : Jupyter notebook document containing all the project code
2.	requirements.txt : packages to be installed via "conda install" in Conda
     -	use the following code in Anaconda Terminal: *for /f %i in (requirements.txt) do conda install --yes %i*

## Making the code functional:
The code should be immediately functional after installation of the requirements. If this code is run in an IDE, then some extra Jupyter Notebook files may need to be installed.

# ► Credit
This project is created and maintained by Andrew Wieber.
