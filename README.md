# MechaCar_Statistical_Analysis
# overview
AutosRUs is a car manufacturing company which is suffering from production troubles that are blocking the manufacturing teamÕs progress. AutosRUsÕ upper management has called on the data analytics team to review the production data for insights that may help the manufacturing team.
In this challenge, we will be helping Jeremy and the data analytics team do the following:
* Perform multiple linear regression analysis to identify which variables in the dataset predict the mpg of MechaCar prototypes
* Collect summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots
* Run t-tests to determine if the manufacturing lots are statistically different from the mean population
* Design a statistical study to compare vehicle performance of the MechaCar vehicles against vehicles from other manufacturers. 
This new assignment consists of three technical analysis deliverables and a proposal for further statistical study.
1. Deliverable 1:Linear Regression to Predict MPG
2. Deliverable 2:Summary Statistics on Suspension Coils
3. Deliverable 3:T-Test on Suspension Coils
4. Deliverable 4:Design a Study Comparing the MechaCar to the Competition
## Resources
* Data Source:MechaCar_mpg.csv and Suspension_Coil.csv
* Data Tools:tidyverse,dplyr,ggplot2 and MechaCarChallenge.RScript.
* Software:RStudio and R
## Deliverable 1
1- The MechaCar_mpg.csv file is imported and read into a dataframe

![mechaCar_table](https://user-images.githubusercontent.com/103543959/197386166-f3eed4b3-097e-432d-8338-6cca6f288f67.png)

2- An RScript is written for a linear regression model to be performed on all six variables
3- An RScript is written to create the statistical summary of the linear regression model with the intended p-values
### Statistical Summary 
From the above output we can see that:
1. The vehicle length, and vehicle ground clearance are statistically likely to provide non-random amounts of variance to the model. That is to say, the vehicle length and vehicle ground clearance have a significant impact on miles per gallon on the MechaCar prototype. Conversely, thevehicle weight,spoiler angle, and All Wheel Drive(AWD) have p-Values that indicate a random amount of variance with the dataset.
2. The p-Value for this model,p-Value: 5.35e-11, is much smaller than the assumed significance level of 0.05%. This indicates there is sufficient evidence to reject our null hypothesis, which further indcates that the slope of this linear model is not zero.

![summary_table](https://user-images.githubusercontent.com/103543959/197386187-0807a7b9-d718-4e7c-bb3a-8cdb3bf577f9.png)

3. This linear model has an r-squared value of 0.7149, which means that approximately 71% of all mpg predictions will be determined by this model. Relatively speaking, his multiple regression model does predict mpg of MechaCar prototypes effectively.

![linear_table](https://user-images.githubusercontent.com/103543959/197386325-89e47e6a-120d-4983-a2d2-151759483e0f.png)


If we remove the less impactful independent variables (vehicle weight, spoiler angle, and All Wheel Drive), the predictability does decrease, but not drastically: the r-squared value falls from 0.7149 to 0.674.

 ## Deliverable 2 
1. Download the Suspension_Coil.csv file, and place it in the active directory for your R session.
2. In your MechaCarChallenge.RScript, import and read in the Suspension_Coil.csv file as a table.
3. Write an RScript that creates a total_summary dataframe using the summarize() function to get the mean, median, variance, and standard deviation of the suspension coilÕs PSI column.
4. Write an RScript that creates a lot_summary dataframe using the group_by() and the summarize() functions to group each manufacturing lot by the mean, median, variance, and standard deviation of the suspension coilÕs PSI column.
### Summary Statistical 
With the understanding that the design specifications for the MechaCar suspension coils mandate that the variance of the suspension coils cannot exceed 100 pounds per square inch (PSI).
When looking at the entire population of the production lot, the variance of the coils is 62.29 PSI, which is well within the 100 PSI variance requirement.

![total_summary](https://user-images.githubusercontent.com/103543959/197386364-8a5508a1-3ff5-431c-9b94-be813da5f716.png)

![lot_summary](https://user-images.githubusercontent.com/103543959/197386374-f7f8d03b-e23c-4ab8-a6d9-fd48495508a2.png)


Similarly, but significantly more consistent, Lot 1 and Lot 2 are well within the 100 PSI variance requirement: with variances of 0.98 and 7.47 respectively. However, it is Lot 3 that is showing much larger variance in performance and consistency, with a variance of 170.29. It is Lot 3 that is disproportionately causing the variance at the full lot level.
This very simple boxplot illustrates the differences between the lots:

## Deliverable 3
1. We wrote an RScript using the t.test() function to determine if the PSI across all manufacturing lots is statistically different from the population mean of 1,500 pounds per square inch.
2. Then, we wrote three more RScripts in your MechaCarChallenge.RScript using the t.test() function and its subset() argument to determine if the PSI for each manufacturing lot is statistically different from the population mean of 1,500 pounds per square inch.
* An RScript is written for t-test that compares all manufacturing lots against mean PSI of the population
* An RScript is written for three t-tests that compare each manufacturing lot against mean PSI of the population
The next step is to conduct a t-test on the suspension coil data to determine whether there is a statistical difference between the mean of this provided sample dataset and a hypothesized, potential population dataset. Using the presumed population mean of 1500, we find the following:

![plt2](https://user-images.githubusercontent.com/103543959/197386484-1a1f73f8-32b7-4755-a7f8-9ccc4823ab80.png)

![plt1](https://user-images.githubusercontent.com/103543959/197386489-6f4d7405-128a-4d4f-a6f4-8f09c334cb00.png)


From here we can see the true mean of the sample is 1498.78, which we also saw in the summary statistics above. With a p-Value of 0.06, which is higher than the common significance level of 0.05, there is NOT enough evidence to support rejecting the null hypothesis. That is to say, the mean of all three of these manufacturing lots is statistically similar to the presumed population mean of 1500.


Next looking at each individual lots:
1. Lot 1 sample actually has the true sample mean of 1500, again as we saw in the summary statistics above. With a p-Value of 1, clearly we cannot reject (i.e. accept) the null hypothesis that there is no statistical difference between the observed sample mean and the presumed population mean (1500).

![lot1](https://user-images.githubusercontent.com/103543959/197386432-f3ca8fcf-a0f3-406e-9bf0-e8412ffb7e81.png)

2. Lot 2 has essentially the same outcome with a sample mean of 1500.02, a p-Value of 0.61; the null hypothesis cannot be rejected, and the sample mean and the population mean of 1500 are statistically similar.

![lot2](https://user-images.githubusercontent.com/103543959/197386439-c6308865-9e8e-45b9-807d-ade47773f4b3.png)

3. However, Lot 3, not surprisingly is a different scenario. Here the sample mean is 1496.14 and the p-Value is 0.04, which is lower than the common significance level of 0.05. All indicating to reject the null hypothesis that this sample mean and the presumed population mean are not statistically different.

![lot3](https://user-images.githubusercontent.com/103543959/197386446-8e3f097c-c962-4c62-a6ba-2fe26792e106.png)





