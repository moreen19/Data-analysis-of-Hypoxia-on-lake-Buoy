# Data analysis of hypoxia in lake Buoy

This analysis project was done to determine all the days and corresponding time within 2018 where hypoxia was experienced in lake BOUY

The full project file is available within this repository.

## Analysis of the data

The data was cleaned and transformed before drawing the needed insights from it.Excerpts of the process are as shown below:

**Looking at the first five rows of the data to get an idea of what the data contains.**

buoy_data.head()

Date/Time m/d/y H:M	DO Sat% 2m	DO Conc. (mg/L) 2m	DO Sat% 5m	DO Conc. (mg/L) 5m	DO Sat% 8m	DO Conc. (mg/L) 8m	DO Sat% 11m	DO Conc. (mg/L) 11m

0	2011-05-16 18:00:00	88.9	9.00	87.9	9.01	84.5	8.69	83.5	8.61

1	2011-05-16 20:00:00	89.2	9.08	89.1	9.08	86.3	8.84	83.9	8.66

2	2011-05-16 22:00:00	89.6	9.14	89.0	9.07	87.1	8.89	83.2	8.58

3	2011-05-17 00:00:00	90.0	9.20	88.7	9.06	86.9	8.88	83.6	8.62

4	2011-05-17 02:00:00	89.7	9.17	88.2	9.02	86.6	8.86	82.8	8.53

**Replacing NaT values in datetime column with NaN to aid in removing rows with only NULL values**

buoy_data['Date/Time m/d/y H:M'] =  buoy_data['Date/Time m/d/y H:M'].astype(str)

buoy_data['Date/Time m/d/y H:M'] = buoy_data['Date/Time m/d/y H:M'].apply(lambda x : np.NaN if x=="NaT" else x) 

**removing rows that have only null values**

buoy_data.dropna(how='all')

## Final data set showing all days and the corresponding time within 2018 where hypoxia was esperienced i.e dissolved oxygen levels below 2mg/L

The table shows a total of 3986 entries

**converting the column shown below back to date time.**

buoy_data10['Date/Time m/d/y H:M'] =  pd.to_datetime(buoy_data10['Date/Time m/d/y H:M'])

buoy_data10

C:\Users\MAURINE\AppData\Local\Temp\ipykernel_1840\2018388295.py:2: SettingWithCopyWarning: 
A value is trying to be set on a copy of a slice from a DataFrame.
Try using .loc[row_indexer,col_indexer] = value instead

See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy

  buoy_data10['Date/Time m/d/y H:M'] =  pd.to_datetime(buoy_data10['Date/Time m/d/y H:M'])
  
Date/Time m/d/y H:M	DO Conc. (mg/L) 2m	DO Conc. (mg/L) 5m	DO Conc. (mg/L) 8m	DO Conc. (mg/L) 11m

119424	2018-07-16 16:00:00	10.38	6.65	2.29	0.65

119425	2018-07-16 16:15:00	10.81	6.69	1.82	0.98

119426	2018-07-16 16:30:00	10.74	6.64	1.65	1.22

119427	2018-07-16 16:45:00	10.68	6.52	1.74	1.23

119428	2018-07-16 17:15:00	10.47	6.17	1.50	1.28

...	...	...	...	...	...

124619	2018-09-19 08:45:00	10.04	5.76	1.94	NaN

124620	2018-09-19 09:00:00	9.98	8.88	1.94	NaN

124624	2018-09-19 10:00:00	9.39	7.94	1.94	NaN

124625	2018-09-19 10:15:00	9.32	6.61	1.87	NaN

124626	2018-09-19 10:30:00	9.20	8.28	1.97	NaN

3986 rows × 5 columns
