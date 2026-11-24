# Workbook guide

The original workbook uses one worksheet named `Sheet1`. This guide refers to its existing cell locations.

## Where to look

| Range | Purpose |
| --- | --- |
| `B1:B2` | Start and end dates |
| `B3:F3` | Stock tickers |
| `A5:F48` | Dates and 44 closing-price observations |
| `H6:L48` | 43 daily returns |
| `N6:R48` | Mean-centered returns |
| `F1:F2` | Annual and daily risk-free assumptions |
| `V3:Z7` | Asset-level statistics |
| `V12:Z16` | Covariance matrix |
| `V21:Z25` | Displayed correlation matrix |
| `V29:Z29` | Equal weights |
| `V35:Z35` | Stored minimum-variance weights |
| `V41:Z41` | Stored maximum-Sharpe weights |
| `V47:Z51` | Random-weight generator and portfolio metrics |
| `AC3:AE100002` | Trial numbers, portfolio standard deviations, and expected returns for 100,000 simulations |


## Solver setup

Enable Solver in desktop Excel. On Windows, use File > Options > Add-ins > Manage: Excel Add-ins > Go > Solver Add-in. The Solver command then appears on the Data tab.

### Minimum variance

| Setting | Value |
| --- | --- |
| Objective cell | `V37` (portfolio standard deviation) |
| Objective | Minimize |
| Changing cells | `V35:Z35` |
| Fully invested constraint | `AA35 = 1` |
| Long-only constraint | `V35:Z35 >= 0` |
| Solving method | GRG Nonlinear |

Minimizing standard deviation is equivalent to minimizing variance because the square-root function is increasing over nonnegative values.

### Maximum Sharpe

| Setting | Value |
| --- | --- |
| Objective cell | `V44` (daily Sharpe ratio) |
| Objective | Maximize |
| Changing cells | `V41:Z41` |
| Fully invested constraint | `AA41 = 1` |
| Long-only constraint | `V41:Z41 >= 0` |
| Solving method | GRG Nonlinear |

The workbook's saved Solver names point to this maximum-Sharpe setup. Enter the minimum-variance setup separately when solving that objective.

## Supporting documentation

- [Load the Solver add-in](https://support.microsoft.com/en-us/excel/load-the-solver-add-in-in-excel)
- [Define and solve a problem using Solver](https://support.microsoft.com/en-us/excel/define-and-solve-a-problem-by-using-solver)
- [STOCKHISTORY function](https://support.microsoft.com/en-us/excel/functions/stockhistory-function)
