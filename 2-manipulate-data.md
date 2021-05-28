When you acquire your data from SafeGraph, you will find that some of the variables are in a challenging format.  For instance, the home census block groups of visitors are listed in this format--

{"360610112021": 603, "460610112021": 243, "560610112021": 106, "660610112021": 87, "660610112021": 51}

-- with all of that information packed into one cell.  To analyze this data, you will probably want each census block group and each visitor count into one cell of a spreadsheet or csv.  However, because there can be hundreds of census block groups, reconfiguring this data by hand would be SUPER time-consuming!

Here is the method that we used to reconfigure our data.  Someone with more programming background could certainly find a more efficient and elegant way to do this, but this way will get the job done.

In a Python environment of your choice (we used Python Notebooks in ArcGIS Pro), import pandas.  This will give you the functions that you need.

```
import pandas as pd
```

Next, you will create a dataframe with whatever data you want to work with.  I worked with just one cell at a time, i.e. one variable for one month, to keep it simple and within my programming abilities.  The code format you will use is:

```
dataframe_name = pd.DataFrame({“item1”:numberofvisitors, “item2”:numberofvisitors, “item3”:numberofvisitors}.items(), columns=[“variablename”, “visitors”])
```

For instance:

```
nov2020popbyday = pd.DataFrame({"Monday":32,"Tuesday":24,"Wednesday":31,"Thursday":29,"Friday":45,"Saturday":46,"Sunday":61}.items(), columns=["day", "visitors"])
```

If the data that you’re working with includes only a list of numbers of visitors (e.g. as with “visits_by_day”), the format you will use is:

```
dataframe_name = pd.DataFrame([number1,number2,number3], columns=[“visitors”])
```

For instance:

```
nov2020date = pd.DataFrame([17,13,7,5,6,10,12,14,1,3,15,4,7,8,5,2,7,5,10,9,18,7,12,7,6,9,19,8,18,4], columns=["visitors"])
```

Next, you will export your dataframe to a csv.

```
dataframe_name.to_csv(r’FilePath\FileName.csv’)
```

Now, you can access your data in Excel, and in a more usable format.  If you’re analyzing data for multiple months, copy and paste all of it into one spreadsheet, making sure to add a column for month.  Consider for each variable whether you want to analyze total visits/visitors, or a derived value, such as proportion or percent change.  Use a pivot table to reconfigure the data into a more workable format.
