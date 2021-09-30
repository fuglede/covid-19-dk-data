# Danish COVID-19 data

Every day, [SSI publishes new tracking data](https://covid19.ssi.dk/overvagningsdata/download-fil-med-overvaagningdata) on COVID-19 for Denmark. However, automatically finding the most recent data and using it is a bit awkward due to files being randomly named and zipped. The purpose of this repository is simply to automate the annoying parts, making the data as accessible as possible.

In particular, the most recent tracking data can be found on [https://fuglede.github.io/covid-19-dk-data/](https://fuglede.github.io/covid-19-dk-data/) with URLs that only change if SSI decides to change their filenames. See the [bundled readme](https://fuglede.github.io/covid-19-dk-data/0_read_me.txt) (Danish) for more information on what data is available.

The data available here is updated every day at 13:10 GMT.


## Example

The format of the bundled data makes it easy to get started doing analyses. Here, as an example, we use [pandas](https://pandas.pydata.org) to see how the [effective reproduction number](https://en.wikipedia.org/wiki/Basic_reproduction_number#Effective_reproduction_number) has changed this week:

```python
>>> import pandas as pd
>>> pd.read_csv("https://fuglede.github.io/covid-19-dk-data/Rt_cases.csv", sep=";", decimal=",").tail(7)
     SampleDate  estimate  uncertainty_lower  uncertainty_upper
535  2021-09-12       1.0                0.8                1.2
536  2021-09-13       1.0                0.9                1.2
537  2021-09-14       1.0                0.9                1.2
538  2021-09-15       1.0                0.9                1.2
539  2021-09-16       1.0                0.8                1.3
540  2021-09-17       1.1                0.8                1.3
541  2021-09-18       1.1                0.8                1.3
```
