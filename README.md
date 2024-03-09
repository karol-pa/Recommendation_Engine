# A Recommendation engine for recommending product bundles

## Introduction

In this notebook, I develop a recommendation engine for an online shop and evaluate the results. 
The original dataset is taken from [Kaggle](https://www.kaggle.com/datasets/carrie1/ecommerce-data). 

## Goal

The goal of this project is to recommend products that might be interesting for customers to buy in bundles. 

The dataset contains two main types of information that can be leveraged for a recommendation system.
1. Product `Description`s: Each product is described in words. 
2. `CustomerID` information: Each purchase is associated with the respective customer
3. Information about items, their quantity and price that were bought together

Number 1 enables us to segment products into classes of products.\
Number 2 allows us then to (a) identify customers with similar interests, and (b) associate products and classes of products with those customers.

By combining 1 and 2, one can, for each customer A
- identify another customer B that has the most similar interests to customer A
- identify the product classes associated with customer A's purchased items
- recommend products from these classes to customer B 

For the product segmentation, I create word embeddings from the `Describtion` column and apply an Agglomerative Clustering algorithm to group the products into classes.\
The customer similarity is quantified using the concept of cosine similarity to find each customer's "next neighbor".

For the final recommendation, I test two methods:
1. I identify the TOP 5 product-classes (i.e. the product classes from which the most purchases were made) of the "next neighbor" and recommend one product from each category.
2. I identify the single TOP product-class of the "next neighbor" and recommend 5 products from this class.

The methods are also tested against a "dummy" model, whis is: 5 products are drawn from a random product-class.



## Project Structure

- **data/**: The directory containing the dataset files (original input from Kaggle as `*.csv` and cleaned data as `*.pkl`).
- **EDA_and_cleaning.ipynb**: This notebook contains the preparation of the data.
- **Recommender.ipynb**: This notebook contains the recommendation engine.
- **Price_prediction.ipynb**: This notebook contains a regression model for `UnitPrice` predictions.





## Installation

1. **Clone this repository:**

   ```bash
   git clone https://github.com/karol-pa/Recommendation_Engine.git
   ```

2. **Set up your enviornment using the provided requirement file:**
   ```bash
   pyenv local 3.11.3
   python -m venv .venv
   source .venv/bin/activate
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

3. **Run the notebooks in Jupyter Lab or VSCode **

## **Contributions**

This project was conducted by Dr. Karol Palczynski.

