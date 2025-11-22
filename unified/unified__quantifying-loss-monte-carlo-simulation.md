# Quantifying Loss With Monte Carlo Simulation
Source: https://help.zscaler.com/unified/quantifying-loss-monte-carlo-simulation
PDF: https://help.zscaler.com/pdf/com/en/1533794.pdf

The Monte Carlo Simulation is a renowned method to determine the probability of an outcome from a range of outcomes with a random set of variables as the source of uncertainty. This simulation helps organizations quantify various risk-related parameters.
The Risk360 service runs the Monte Carlo simulations 1,000 times. In each simulation iteration, the service measures the financial loss based on a randomized cyber breach event and a randomized financial loss within a predefined confidence interval defined by the lower and upper bounds of a loss when a breach occurs. The result of the simulations is used to estimate the yearly average loss and the loss exceedance curve (i.e., the curve that shows the probability that a loss exceeds a certain amount). The process is repeated 4 times to calculate the yearly average loss and the loss exceedance curve under the following 4 distinct scenarios:
- **Inherent Risk**: The current risk score of the organization.
- **Residual Risk**: The risk score of an organization after mitigating the top 10 risk factors.
- **Last 30 Days Average Risk**: The average risk score of an organization in the last 30 days.
- **Industry Peer Risk**: The average risk score of peer organizations.
Analyzing the Monte Carlo Simulation
The Monte Carlo Simulation page (Analytics > Risk360 > Financial Risk > Monte Carlo Simulation) consists of the following metrics to help you analyze the simulated results:
Loss Exceedance
This graph shows the probability of exceeding loss values (in percentage) in millions of dollars. The graph shows the simulation across 4 risk parameters:
- **Inherent Risk (Current Risk Score)**: This simulation is based on your current organization's risk score. This shows the probability of loss based on your overall organization risk score.
- **Residual Risk (Risk score after addressing top 10 factors)**: The residual risk is the risk score obtained after rectifying the 10 [Risk360 Factors](/unified/viewing-risk-factors). This simulation helps you see the financial impact of addressing the top 10 [Risk360 Factors](/unified/viewing-risk-factors).
- **Last 30 Days Average Risk**: This simulation is based on the average risk of the last 30 days. This helps you see the impact of changes in risk score for the last 30 days.
- **Industry Peer Risk**: This simulation is based on the industry peer risk score. This helps you in comparing loss probability to your industry peers.
Hover over a risk parameter curve in the graph to view the probability of exceeding loss for a certain amount (in millions of dollars).
![Monte Carlo Simulation Graph](/downloads/risk360/dashboard-analytics/quantifying-loss-monte-carlo-simulation/Risk360-Risk-graph.png)
Average Yearly Exposure
This bar graph shows the average yearly loss in millions of dollars for each of the risk parameters.
![Yearly Average Loss Graph in Monte Carlo Simulation Page](/downloads/risk360/dashboard-analytics/quantifying-loss-monte-carlo-simulation/Risk360-yearly-loss-bar-graph.png)
Breach Probability (%)
This section shows the breach probability percentage calculated based on your organization's inherent risks, last 30 days average risk, residual risk, and industry peer risk. The breach probability is also an input parameter for your organization's financial exposure calculation. The value of Zscaler-computed breach probability is continuously updated and determined based on the industry vertical, annual revenue range, and the organization's risk score.
You can enable the **Simulate **toggle to edit the probability for the desired risk parameter. After you click **Apply**, your organization's financial exposure is reevaluated based on your input. Disable the toggle to restore the Zscaler-computed probabilities.
![Breach Probability in Monte Carlo Simulation](/downloads/risk360/dashboard-analytics/quantifying-loss-monte-carlo-simulation/Risk360-Breach-Probability_1.png)
Simulation Results
Click **View All Iterations** to open the Simulation Results drawer. The drawer consists of 4 tabs for each risk parameter. Each tab shows the results for all the 1,000 iterations run by the Monte Carlo Simulation.
![Drawer view in Monte Carlo Simulation](/downloads/risk360/dashboard-analytics/quantifying-loss-monte-carlo-simulation/Risk360-Monte-Carlo-drawer.png)