# Calculations and Assumptions
---

-Wokring Capital and Netdebt budget vs actual calcuation differs from others. Instead of marking it down by 12 months, we assume that the figure provided in budget is a cumulative figure which is live hence we should compare the december figure to the budget.
- Summary's selector: Created two sets of selectors (LTM and LastMonth, Cumulative and Monthly) to allow users to switch between view. using measures to calculate base on user's selection. This is assuming we do not want to cramp all information on one page.
-Variance % calculation: dividing monthly financial value by the monthly budget (Annual budget /12)
- Actuals vs budget calculation: for both absolute and variance I am assuming actuals refers to the financial monthly data and apply subtraction and division respectively.
- YTd calculation: I did not conduct additional analysis on this part. The assumption is we want a yearly view based user's date input on the navigation page, in which the matrix has already provided that information we drilling up to a yearly view.


# Key Modeling Choices
---

-Using the concat of Company_Year as the key to connect fact to dimension table for one to many relationship.
- Annual Budget was used as the fact table, whilst the other tables act as a dimensional table as they either holds dimensional data (company/ fund / investment etc) or they are monthly activities data (KPI / Financial).
-Actuals vs budget calcualtion: To facilitate the calcualtion, I looked up and move the budget figure into the financial_monthly table. This is to reduce complexity in DAX measure and ease of read also without overloading the data model with a new table.
- Calendar table is created form scratch with GENERATESERIES and is used to connect to the KPIs and financial monthly to allow us to apply time intellegence analysis.
- Created a measure table instead of saving measures in their respective table. This improves transparncy and readability.



# Limitations
---

- Technical issue: faced a challenge where whenever I tried to add a drill through for ease of use, PowerBI is asking me to sign in with an organisation account, and I failed to bypass this.
- Budget is shown as annualised figure and is more difficult to connect to other dimensional data.
- Annualised interest rate is missing from source data and require manual calculation



# Next Steps
---

- I will build a monthly budget table to provide easy access to budget data
- I will denormalise monthly activities data into one table to optimise loading and cost efficiency 
- I will ask users for feedback, and understand what result will this report achieve. Feedback mainly concerns about the report output, is there areas which we will want a chart (Powerpoint insertion) and others in a readable table  (Excel Download) and customise the dashboard accordingly
- More on feedback, what other financial metrics do user want to use to slice the data, such as only showing company/ funds that are under performing/ over performing. This elevate the report's efficiency by minimising user's effort to interrogate the data themselve when we can provide the answer up front.
- Assuming this will be a mixture of direct query for monthly data and import data for SCD, we need to understand the cost of running the report. Mainly concern is when more slicers are dropped into the dashboard in future we will face performance and cost issue when each selection refreshes the underlying data (Resolve by Apply All Slicer Button)
- I will push to combine comments and monthly data together. the current data does not alow us to do so as I can not assume Comment Date as the month the user is referring to, moreover when this is put to scale, we will not know which fund that person is referring to, hence will require more data collection point
- To tackle the abesent of annualised interest rate data, I will get to the source data and identify it before loading into PowerBI, to avoid reserve calculations.
-  I will work with engineering team to create surrogate key between the dimensional table and the fact table to improve efficiency /redundancy and reduce the use of manually created key in PowerBI

