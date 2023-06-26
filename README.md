# __spatial_domain.anomaly__.O_Seive

---
## class __O_seive__(data, column, tsf=1, bsf=1)
---

### ___O_Seive___ is an outlier detection algorithm that utilizes a 3D projection of data points. It calculates distances of data points from a centre point in the 3D space, based on the squared values of the target column. The algorithm then determines upper and lower distance thresholds using a median-based approach. Data points that fall outside these thresholds are considered outliers. This class also provides methods for visualizing the data in the 3D space. 
  

---
## Parameters:

- __data__: _dataframe_
    - The __data__ on which the algorithm should be applied.

- __column__: _str_
    - __Target column__, the filtering is done based on this column.

- __tsf__: _int or float, defaul-t=1_
    - __Top scaling factor__, the quantity with which the median distance must be multiplied above the centre plane.

- __bsf__ : _int or float, default=1_
    - __Bottom scaling factor__, the quantity with which the median distance must be multiplied below the centre plane.
---
## Installation
```pip install vcosmos```

## Usage
```python
import pandas as pd
from spatial_domain.anomaly import O_Seive
# Reading a dataset using pandas.
df=pd.read_csv('co2.csv')
print(df.head)

#   Make       Model Vehicle Class  Engine Size(L)  ...  Fuel Consumption Hwy (L/100 km) Fuel Consumption Comb (L/100 km) Fuel Consumption Comb (mpg)  CO2 Emissions(g/km)
# 0  ACURA         ILX       COMPACT             2.0  ...                              6.7                              8.5                          33                  196
# 1  ACURA         ILX       COMPACT             2.4  ...                              7.7                              9.6                          29                  221
# 2  ACURA  ILX HYBRID       COMPACT             1.5  ...                              5.8                              5.9                          48                  136
# 3  ACURA     MDX 4WD   SUV - SMALL             3.5  ...                              9.1                             11.1                          25                  255
# 4  ACURA     RDX AWD   SUV - SMALL             3.5  ...                              8.7                             10.6                          27                  244

# [5 rows x 12 columns]

seive= O_Seive(df,'CO2 Emissions(g/km)',tsf=4.5,bsf=2)
clean_data=seive.filtered_data()
plot=seive.hcps_plot()
print(clean_data.head())

# Filtering Initiated....
# Filtering Complete.
# Ouliers Removed: 11
#     Make       Model Vehicle Class  Engine Size(L)  ...  Fuel Consumption Hwy (L/100 km) Fuel Consumption Comb (L/100 km) Fuel Consumption Comb (mpg)  CO2 Emissions(g/km)
# 0  ACURA         ILX       COMPACT             2.0  ...                              6.7                              8.5                          33                  196
# 1  ACURA         ILX       COMPACT             2.4  ...                              7.7                              9.6                          29                  221
# 2  ACURA  ILX HYBRID       COMPACT             1.5  ...                              5.8                              5.9                          48                  136
# 3  ACURA     MDX 4WD   SUV - SMALL             3.5  ...                              9.1                             11.1                          25                  255
# 4  ACURA     RDX AWD   SUV - SMALL             3.5  ...                              8.7                             10.6                          27                  244

# [5 rows x 12 columns]
```
---

