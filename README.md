# UW-park-usage

## Data Source
Our methods center around data obtained from [SafeGraph](https://www.safegraph.com/), a company that provides human movement data.  SafeGraph’s data is aggregated cell phone movement data, meaning that while it does not identify individual mobile devices, it can tell you things such as how many people who live in a given area visited a specific location, how long people tend to stay at a specific location, and how many people visit at certain hours of the day or days of the week.  For a more detailed idea of what specific data SafeGraph provides, see SafeGraph’s [Places Schema page](https://docs.safegraph.com/v4.0/docs/places-schema#section-patterns).

SafeGraph provides weekly data for the most recent three months, and monthly data for January 2018 through three months ago.  We used monthly data for this project - what SafeGraph calls “Monthly Places Patterns.”

It is important to remember and acknowledge that SafeGraph data represents mobile devices, not people.  People will not be represented by this data if they do not carry a mobile device, or if their privacy settings prevent their data from being shared with data companies like SafeGraph.  SafeGraph’s data represents a small fraction of people and, as a result, may be biased and/or suffer from sampling error, particularly at the census block level and in other small scale studies.  The data also may not represent all demographics equally.

## Choosing a Study Area
In a perfect world, SafeGraph would be able to provide high-quality data about any park you would like to analyze.  However, we have found this not necessarily to be the case.

[SafeGraph’s “Match” function](https://shop.safegraph.com/match/) is one way to do a preliminary check on whether SafeGraph has data for a park of interest.  You will create a csv with information about your park or parks, including latitude and longitude, zip code, name, etc., and input the csv into Match.  If it returns your park, that is a good sign.  If it does not return anything, or it returns something similar to but not exactly your park (such as a nearby establishment that shares part of the park’s name), try adding or removing fields from your Match.  We found that most parks we explored did turn up in the Match, but for reasons unknown to us, a few did not.

If you succeed in finding your park of interest, take a note of the SafeGraph Place ID.  You will need this to acquire the data later on.

It is possible that, even if your park turns up in Match, SafeGraph will not have complete data for the time period you’re interested in.  This appears to be rare, but it did happen to us.  It’s difficult to ascertain whether this will happen without going through the data acquisition process and seeing if it produces data.  For this reason, we recommend having a backup park or two in mind for your study and staying flexible.
