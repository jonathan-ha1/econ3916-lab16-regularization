# Regularization: Buying Bias to Sell Variance

## Objective
I tested whether LASSO and Ridge, with penalties chosen by cross-validation, predict better than OLS when there are more predictors than training rows and only a few of them matter.

## Methodology
- I built a simulated dataset with 200 predictors, only 5 of them real, and 105 training rows, then fitted OLS, LASSO and Ridge to it.
- I traced the LASSO path to see when the true predictors and the noise variables entered as the penalty got smaller.
- I chose the LASSO penalty by 5-fold cross-validation, with the scaler fitted inside every fold.
- I scored LASSO's selected variables against the known truth.
- I gave LASSO and Ridge two near-duplicate predictors that both matter and compared how each one handled them.
- I wrote my own prompt asking an AI for the cross-validation loop and checked its results against mine over 2 rounds.

## Key Findings
- OLS had a test MSE of 12.9587, Ridge 10.1128 and LASSO 1.4219, so LASSO did far better because only 5 of the 200 predictors were real.
- On the LASSO path, all five true predictors were in from step 6, and the first noise variable didn't enter until step 17.
- Cross-validation chose a lambda of 0.1995 with a CV MSE of 1.5502.
- LASSO found all 5 true predictors but also kept 11 false positives.
- With the near-duplicate predictors, LASSO put 4.462 on one and zero on the other, while Ridge split the weight into 1.618 and 1.609.
- The AI's loop matched mine exactly in both rounds, 0% apart, with lambda 0.1995 and CV MSE 1.5502 on all 21 penalties and lambda 0.1585 and CV MSE 1.5810 on every second penalty.
