# Types of Data

Data can be classified into 2 types.

1. Structured data
2. Unstructured data

---
# 1)Structured data

Those data which have some kind of valid structure fall under structured data.

Example:

1. A excel file will be classified as structured data. A excel file has data divided into rows and columns.

   A row will always have a certain value for a column. The value could be null but the column will exist.

   The point is, the data follows a structure.

2. A patients medical record will be classifed as structured data. There will be few columns such as weight, height, blood pressure, heart disease, sex etc.

   The point is, the data follows a structure.

# 2) Unstructured data

Unstructured data donot have a certain structure. Data such as music, images, natural languages,videos, audio files etc donot follow any kind of structure.

Example:

1. One image of a dog could look completely different from another image of a dog. One dog could be wearing some clothes, have a bigger head, could be of a differnt bread, have a different color etc.

2. Text you send to a friend have a different structure as compared to text you write to a co-worker.

The data that donot change over time are called static data. A patients medical record is a example of static data. these data are typically in the form of csv file.

The data that are constantly changing are called streaming data. If you want to know how does a news headline change stock prices, you are working with a streaming data. news headline change very fast and you need to identify how does that news change affects stock market.

You will generally start with static data for machine learning but might use streaming data when you move to production.
