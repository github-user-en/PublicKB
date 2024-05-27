# What is `bootstrapped dataset`?
A bootstrapped dataset is a technique for training machine learning models using a small amount of data. It can be particularly useful when data is expensive or difficult to collect, such as in certain remote sensing applications.

It involves creating multiple copies of the original dataset by randomly sampling from it with replacement. **This means that each sample can appear more than once in the bootstrapped dataset, increasing its effective size.**

The main purpose of using bootstrapped datasets in machine learning is to improve the stability and accuracy of the trained model, especially when working with small or imbalanced datasets. 
```
Suppose the original dataset had N records. Now, the bootstrapped dataset will have  also have N records, only (N-n) unique records. 
Since there are 'n' suplicated records, exactly 'n' records would have been left out from the original dataset in the bootstrapped dataset. These 'n' leftout records can be used as test dataset to evaluate   the machine learning model.
```