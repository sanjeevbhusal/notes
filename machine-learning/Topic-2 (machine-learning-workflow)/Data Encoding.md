We have few categorical features in the data set. for machines it is extremely hard to process categorical data since models are based on mathematical equations. So, we will convert/encode categorical data into numerical data.  There are 2 ways of encoding data.

- Label Encoding
- One hot encoding


# Label Encoding

There are some categorical data that has order associated with them. Such categorical data can be represented easily with numerical equivalent. 

Example: Lets say we have a dataset containing mothers education as one of the features. The values are 

- no education
- primary education
- secondary education
- higher education

If you notice, all these values are in a order. Primary Education has a higher order than no education, secondary education has higher order than primary education, higher education has higher order than secondary education.  If we want to represent this data with numerical equivalent, we will do it this way

- 0 (no education)
- 1 (primary education)
- 2 (secondary education)
- 3 (higher education)

This way of data encoding is called Label Encoding.But this method cant encode all kind of data. Thats why we have another method called One hot encoding.

---
# One Hot encoding

There are some categorical data that donot have any order associated with them. Such categorical data ca't be represented by assigning a numerical equivalent like label encoding.

Example: Lets say we have a data set containing mothers job as one of the features. The values are 

- teacher
- health care services
- engineer
- lawyer
- civil services 

This kind of data donot have any kind of hierarchy/order associated with them. So, we need to use a different approach to encode such data.

In this approach, we create a new column for every ctegory in a categorical column. As mothers_job column has 5 category, 5 new columns will be created.

- m_job_teacher
- m_job_health_care_services
- m_job_engineer
- m_job_lawyer
- m_job_civil_services

The originial column of mothers_job is removed.

If there were more columns like mothers job, we would do the same for all those columns. 

The value in all the new columns column would either be 0 or 1, denoting absence or presence of feature.  0 represents absence and 1 represents presence. So, if a student's mother is a lawyer, then all the m\_job_[profession] columns would have a value of 0 except m_job_lawyer with a value of 1. 



