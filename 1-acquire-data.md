SafeGraph provides data for a fee; however, academics can [apply for free data access](https://www.safegraph.com/academics).  A .edu email address is required.

Retrieving your data from SafeGraph can seem complicated at first, but do not be intimidated!  It is very doable.  Joel McCune of Esri has written an [excellent blog post](https://joelmccune.com/get-safegraph-places-by-poi-id-using-an-aws-ec2-instance-to/) on the beginning part of the process.  I recommend following his instructions.

At the end of these instructions, you will find yourself in Jupyter Notebooks.  Open Notebook 2.

This notebook will lead you through the process of acquiring and downloading the data.  A few notes:

In cell 2, you may need to add a colon at the end of the if statement:

```
if not dir_raw.exists():
  dir_raw.mkdir(parents=True)
```

In cell 3, you will need to replace the POI ID for White Pass with the SafeGraph place ID for your point of interest.  You can find this ID with SafeGraph’s “Match” function (see README).

In cell 4, I have had to insert my actual AWS keys in order to avoid errors.  For example:

```
sg = SafegraphClient(access_key="xxxx", secret_key="xxxxxx")
```

However, you may want to try to find a way to keep your access key and secret key out of the notebook, particularly if you plan to share the notebook with others.

The rest of the notebook should run without problems.  In cell 6, make sure to include in the code the years and months that you are interested in.  In my experience, it took about one hour to retrieve a full year’s worth of data, so don’t be alarmed if cell 6 takes quite a while to run.

Cell 7 creates a CSV with your data.  You can find the CSV under data/raw/, and right-click it to download it.

If your data acquisition was successful, you should have (at least) one row for each month of data that you requested.  If a month that you requested is missing from the csv, that likely means that SafeGraph does not have data for that month available.  It also seems that you cannot request monthly patterns data for anything within the most recent three full months, as this time period is covered by the weekly patterns.
