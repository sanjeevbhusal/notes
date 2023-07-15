In order to perform data cleaning, we first need to identify the problems/impurity in the data. Some common problems include inconsistent value, irrelevant feature, wrong data type, inconsistent capitalization, low image quality etc. All these problems donot occur in all the data. Some occur in structured data and rest occur in unstructured data

Structured data includes tabular data such as excel sheet, relational database etc. Unstructured data includes music files, image files, web scrapping, videos etc. Depending upon the type of data, there are a number of steps you can take to clean the data.

## Problems in Structured data

There are some common problems that occur in structured data such as Irrelevant Feature, Parsing, Type Conversion, Inconsistent Capitalization, Mislabelled classes etc. 

- Irrevelant Feature: Some features in a dataset might be irrevalant. There are different factors that determine which feature might be irrelevant. For regression problem, if 2 independent features are closely correlated, then one of the feature is irrevlant and should be dropped.
- Parsing: Parsing refers to extracting information from existing data. We can extract a persons age based on their date of birth.
- Type Conversion: Type Conversion refers to converting a data from the current data type to a different target data type. 
- Structural Errors: Structural Errors refer to errors that are caused due to inconsistent structure of the data. 2 values that mean the same might have inconsistent capitalization(mercedes and MERCEDES) or 2 values that mean the same might be represented with different data types (1 and first)


## Problems in Unstructured data

We will look at problems that occur in some of the unstructured data like text and images. 

In case of Text, here are some of the issues.

- Mispelling
- Random white spaces between words
- HTML and XML tags
- special characters

In case of Images, here are some of the issues.

- Blur
- Missing pixels
- Over exposure
- Under exposure
- Noise

Images with these problems are referred as `Low quality Image`. Low quality Image is always a problem for computer vision project such as autonomous driving. The quality of image can be judged through `hosaka plot` and `histogram`. 
<br>
## More Readings

> [!info]
	For more information, read `Read_Data_Quality_Inspection_and_Data_Cleaning.ipynb` under `assets/extra notes/notebooks`