Fast.Ai - Machine Learning
---

# Lesson 1 - Random Forest

> %load_ext autoreload
Reload modules automatically before entering the execution of code. (Useful if you modified a class and it reloads the change automatically.)
Source: https://ipython.org/ipython-doc/3/config/extensions/autoreload.html

> %autoreload 2
Reload all modules (except those excluded by %aimport) every time before executing the Python code typed.
Source: https://ipython.org/ipython-doc/3/config/extensions/autoreload.html

> %matplotlib inline
The output of plotting commands is displayed inline within frontends like the Jupyter notebook, directly below the code cell that produced it. The resulting plots will then also be stored in the notebook document.
Source: https://ipython.readthedocs.io/en/stable/interactive/plotting.html

> Shift + Enter
Tells where the function/class is from

> ?function
Shows the documentation of the function/class

> ??function
Shows the source code of the function/class

> !ls {PATH}
Execute shell commands in Jupyter Notebook. Use {} brackets to use Python variables

## Evaluation
Take a look at the "Evaluation" of the Kaggle competition and find out how the model is going to be evaluated. For prices it is mostly log error, as the ratio is important than the total value. (10€ could be 0,1% or 10%)

## Random Forest
A good starting point for most machine learning models, as it is easy to build, can evaluate with the same data set, and don't use statistical assumption, like normal distribution.

## Regressor
Prediction of continues values on a scale, like prize.

## Classification
Prediction of values of categories, like car model.

> Shift + Tab
Shows the short doc of selected function, class or variable.

> Shift + Tab + Tab
Shows extensive documentation of selected function, class or variable.

> Shift + Tab + Tab + Tab
Shows in a separate window the extensive documentation of selected function, class or variable.

## Random Forest Input
A random forest expects that all inputs are numeric (float, boolean). If the data contains categories (like gender) and dates, than they need to be converted into numbers or boolean. FastAI has the function "train_cats()" to convert the dataframe into right format.

## Date
The date itself contains a lot of information that can be useful:
Year, month, day, hour, minute, second, weekday, holiday, weather, events, ...
FastAI has the function "add_datepart()" to add more columns with date information, that can be used for training.

## More Columns is always better
Adding more information is (almost) always better to train the model.

> pd.read_csv('train.csv', parse_dates=["date_column"])
When loading csv file, tell it which columns are dates, so they will be loaded in the right format instead of string.

> fastai.train_cats(df)
Converts any column of type string into a column of categorical value.

## Ordering Categories
After the columns are turned into categorical values, take a look at the order of them. If the order is not correct (High, Low, Medium), than it is not to bad. But if you order them, it can improve the performance of the model, as the splitting by categories than makes more sense.
> df_raw.UsageBand.cat.set_categories(['High', 'Medium', 'Low'], ordered=True, inplace=True)

## Nominal vs. Ordinal Categories
Nominal are dummy variables are not order to each other like (a > b > c) and example would be cities.
Ordinal variables have a relationship among each other like (a > b > c) and example would be intensity (High, Medium, Low).
Source: https://stackoverflow.com/a/41875178/3388671

## Feather Format
The Feather format is one of the fastest way to save data to disk and load up again. It will be stored on the drive as it was stored in the memory. So no more conversion into right format, like it is needed for CSV.
