# POLYNOMIAL MACHINE LEARNING LIMIT TESTING

# ► What the project does

Firstly, this project examines the capability of Polynomial Regression, Random Forest Regression, and Ridge to predict a target variable that is generated via a precise equation. Variants of the formula are examined in order to evaluate the sensitivity of each model to the different parts of the equation. Modelization is perforemed on both a clean and a noisy version of the data. These equations are:
- y1 = 0.45∙(x1) - 0.35∙(x2) + 0.7∙(x3)^2 - (x4)^-1 + 5
- y2 = 0.45∙(x1) - 0.35∙(x2) + 0.7∙(x3)^2 - (x4)^-1 + |x5| + 5
- y3 = 0.45∙(x1) - 0.35∙(x2) + 0.7∙(x3)^2 - (x4)^-1 + 2∙(x6)∙(x7) + 5
- y4 = 0.45∙(x1) - 0.35∙(x2) + 0.7∙(x3)^2 - (x4)^-1 + |x5| + 2∙(x6)∙(x7) + 5
- y5 = 0.45∙(x1) - 0.35∙(x2) + 0.7∙(x3)^2 - (x4)^-1 + |x5| + 2∙(x6)∙(x7) + 1.2*x8^(3.5) + 5
- Note: a final noise variable is added in some simulations. This is an "x9" external to the equations.

Secondly, this project examines whether polynomial features (of degree 2) can be used successfully with a Random Forest Regression with equation y5. This is performed via an RFE, manually selected polynomial features, and finally the precise features used in the equations.

# ► The interest of the project

The ability to understand the limits of both polynomial regression and Random Forest Regression is essential to selecting the proper model in any machine learning project involving continuous data. Nonlinear behavior is particularly difficult to take into account. The following conclusions can be taken from this project:
- Polynomial regression must approximate |x5| by x**2 to achieve good results (at least in the case where there are equal negative and positive values of x). As a result, Random Forest Regression is better at predicting results from the x5 feature.
- Polynomial regression is better than Random Forest Regression at predicting the interaction x6*x7, however.
- Random Forest Regression is poorer at predicting the x8^3.5 feature.

With regards to transforming the base features (x1, x2, x3, etc.) into polynomial features, it is demonstrated that Random Forest Regression results can be improved. These features must be selected carefully, however. Using an RFE leads to overfitting as can be seen by its selection of features not in alignment with the real equations used to generate the data. Overfitting is of course a concern with polynomial regression as well.

# ► How to Install and Run the Project

## Installation

### *Prerequisites:*
1.	Python 3.10.13 environment
2.	Jupyter Notebook (last tested on version 7.0.6)
3.	Anaconda
   
### *Files:*
1.	Polynomial_Machine_Learning_Limit_Testing.ipynb : Jupyter notebook document containing all the project code
2.	requirements.txt : packages to be installed via "conda install" in Conda
     -	use the following code in Anaconda Terminal: "for /f %i in (requirements.txt) do conda install --yes %i"

## Making the code functional:
The code should be immediately functional after installation of the requirements. If this code is run in an IDE, then Jupyter Notebook may need to be installed.

# ► Credit
This project is created and maintained by Andrew Wieber.
