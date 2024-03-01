# MULTIVARIATE NON-LINEAR EQUATION MACHINE LEARNING LIMIT TESTING

# ► What the project does

Firstly, this project examines the capability of Polynomial Regression, Random Forest Regression, and Ridge to predict a target variable that is generated via a precise equation (multivariate and non-linear). Variants of the formula are examined in order to evaluate the sensitivity of each model to the different parts of the equation. Modelization is performed on both a clean and a noisy version of the data. These equations are:
- $y_0 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 5$<br>
- $y_1 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 0.7 \cdot x_3^2 + 5$<br>
- $y_2 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 0.7 \cdot x_3^2 - x_4^{-1} + 5$<br>
- $y_3 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 0.7 \cdot x_3^2 - x_4^{-1} + |x5| + 5$<br>
- $y_4 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 0.7 \cdot x_3^2 - x_4^{-1} + 2 \cdot x_6 \cdot x_7 + 5$<br>
- $y_5 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 0.7 \cdot x_3^2 - x_4^{-1} + |x5| + 2 \cdot  x_6 \cdot x_7 + 5$<br>
- $y_6 = 0.45 \cdot x_1 - 0.35 \cdot x_2 + 0.7 \cdot x_3^2 - x_4^{-1} + |x5| + 2 \cdot  x_6 \cdot x_7 + 1.2 \cdot x_8^{3.5} + 5$
- Note: a final noise variable is added in some simulations. This is an " $x_9$ " external to the equations.

Secondly, this project examines whether polynomial features (of degree 2) can be used successfully with a Random Forest Regression with equation $y_6$. This is performed via recursive feature elimination (RFE), manually selected polynomial features, and finally the precise features used in the equations (excluding the coefficients, eg. 0.45, -0.35, 0.7, etc.).

# ► The interest of the project

The ability to understand the limits of both polynomial regression and Random Forest Regression is essential to selecting the proper model in any machine learning project involving continuous data. Nonlinear behavior is particularly difficult to take into account. The following conclusions can be taken from this project:
- Polynomial regression must approximate $|x_5|$ by $x^2$ to achieve good results (at least in the case where there are equal negative and positive values of $x$). As a result, Random Forest Regression is better at predicting results from the $x_5$ feature.
- Polynomial regression is better than Random Forest Regression at predicting the interaction $x_6 \cdot x_7$.
- Random Forest Regression is poorer at predicting the $x_8^{3.5}$ feature.
- Random Forest regression predicts $x_4^{-1}$ better.
- A single feature containing only random noise may not always have a big impact. In this project it has a < 1% negative result.
- Ridge Regression does not do well with $|x_5|$ or $x_4^{-1}$.

With regards to transforming the base features ($x_1$, $x_2$, $x_3$, etc.) into polynomial features, it is demonstrated that Random Forest Regression results can be improved. These features must be selected carefully, however. Using an RFE leads to overfitting as can be seen by its selection of features not in alignment with the real equations used to generate the data. Overfitting is of course a concern with polynomial regression as well.

# ► How to Install and Run the Project

## Installation

### *Prerequisites:*
1.	Python 3.10.13 environment
2.	Jupyter Notebook (version 7.0.6 is installed via requirements.txt)
3.	Anaconda
   
### *Files:*
1.	Polynomial_Machine_Learning_Limit_Testing.ipynb : Jupyter notebook document containing all the project code
2.	requirements.txt : packages to be installed via "conda install" in Conda
     -	use the following code in Anaconda Terminal: *for /f %i in (requirements.txt) do conda install --yes %i*

## Making the code functional:
The code should be immediately functional after installation of the requirements. If this code is run in an IDE, then some extra Jupyter Notebook files may need to be installed.

# ► Credit
This project is created and maintained by Andrew Wieber.
