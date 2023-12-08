# Forecasting volatility with a GARCH model

This analysis looked at how volatility can be modeled and forecasted using a GARCH(1,1) model. The data consisted of the S&P 500 index from January 4, 2010, to November 27, 2023.

This analysis was motivated by the need to understand, model, and forecast volatility for risk management purposes. It is an important metric for business and individuals to understand - increased volatility and potential losses can cause stress to investors both on a small and large scale.

GARCH is a common method for modeling volatility. Volatility tends to be conditional heteroskedastic, meaning the variance is non-constant and depends on the previous day. Other models such as ARIMA and exponential smoothing do not account for this non-constant variance. GARCH(1,1) has shown to be particularly effective model. Hansen and Lunde (2004) compared 330 different ARCH type models and found no evidence that any of these models beat a GARCH(1,1) in accuracy. Due to the decreased variables and simplicity of this model, we decided to use a GARCH(1,1) for our analysis.

We performed modeling in R utilizing the rugarch package to fit the data. Daily returns were calulcated by taking the log difference between days. The last 29 days of the S&P 500 data was excluded for forecasting testing. Coefficient p-values were found to be significant with more emphasis weighted on the lagged squared volatility as compared to the lagged squared residuals (.80 versus .17). Residual diagnostics failed a normality check which is an assumption of GARCH. Additionally, the forecast test errors were not randomly distributed - our forecast consistently over estimated the actual data. 

Our conclusion was that a GARCH(1,1) model does not appear to be the best fit for the S&P 500 data. Other more flexible methods may prove more robust than the GARCH model used. Additionally, the increase volatility post covid may be a factor effecting the reliability of this model.