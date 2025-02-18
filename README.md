# Rossmann drug time series forecast

Rossmann is a European drug distributor which operates over 3,000 drug stores across seven European countries. Since a
lot of drugs come with a short shelf life, that is, they do not have a long expiry date, it becomes imperative for
Rossmann to accurately forecast sales at their individual stores. Currently, the forecasting is taken care of by the
store managers who are tasked with forecasting daily sales for the next six weeks.

As expected, store sales are influenced by many factors, including promotional campaigns, competition, state holidays,
seasonality, and locality.

With thousands of individual managers predicting sales based on their unique circumstances and intuitions, the accuracy
of the forecasts is quite varied. To overcome this problem, the company has hired you as a data scientist to work on the
forecasting problem. As part of your job role, you are tasked with building a forecasting model to forecast the daily
sales for the next six weeks. To help you with the same, you have been provided with historical sales data for 1,115
Rossmann stores.

# Data definition

[Data file](./Dataset)

The data is provided in two tables, stores and train. The store table contains the metadata for every single store
including the following:

<b>Store</b> - an Id that represents the store

<b>StoreType</b> - differentiates between 4 different store models: a, b, c, d

<b>Assortment</b> - describes an assortment level: a = basic, b = extra, c = extended

<b>CompetitionDistance</b> - describes thedistance in meters to the nearest competitor store

<b>CompetitionOpenSince[Month/Year]</b> - gives the approximate year and month of the time the nearest competitor was
opened

<b>Promo2</b> - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 =
store is participating

<b>Promo2Since[Year/Week]</b> - describes the year and calendar week when the store started participating in Promo2

<b>PromoInterval</b> - describes the consecutive intervals Promo2 is started, naming the months the promotion is started
anew. E.g. "Feb, May, Aug, Nov" means each round starts in February, May, August, November of any given year for that
store

<b>The train table contains the sales data for individual stores at a daily level along with the details about the
day</b>

<b>Store</b> - a unique Id for each store

<b>DayOfWeek</b> - Describes the day of the week (1 - Monday till 7 - Sunday)

<b>Date</b> - Describes the date on the day

<b>Sales</b> - the turnover for any given day (this is what you are forecasting)

<b>Customers</b> - the number of customers on a given day

<b>Open</b> - an indicator for whether the store was open: 0 = closed, 1 = open

<b>StateHoliday</b> - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays.
Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas,
0 = None

<b>SchoolHoliday</b> - indicates if the (Store, Date) was affected by the closure of public schools

Since the company is just embarking on this project, the scope has been kept to nine key stores across Europe. The
stores are key for the company keeping in mind the revenue and historical prestige associated with them. These stores
are numbered - 1,3,8,9,13,25,29,31 and 46.

While attempting to forecast sales, it is advisable to keep the following question in mind.

- Is the sales data non-stationary? If so, how do you find it and correct it?

- Is the data cointegrated? Which variables are cointegrated and how do you find them?

- What is the impact of the number of customers on sales?

- What is the impact of promo and promo2 variables on sales? How do you measure it?

- Forecast sales for the next 6 weeks? Report the accuracy of the model using MAPE.

While you are solving the problem, the following steps can be used as a reference. Please note that you can take a
different approach as well.

- Find outliers at the 99th percentile and remove them.

- Standardize the sales and number of customers variables before modelling.

- Determine if the data is stationary

- If stationary then apply Vector Autoregression Model.

- If non-stationary then specify the model in differences

- Make sales, promo2 and any other variables you think of as dependent variables.

- Check for cointegration using the Johansen test.

- Predict sales for the next 6 weeks.