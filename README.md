# E-commerce Product Recommendation System

The Product Recommendation System, powered by machine learning, is a project designed to offer personalized product suggestions to users based on their browsing and purchase history. Employing collaborative filtering algorithms, the system analyzes user behavior to generate relevant recommendations. The primary goal is to enhance the overall shopping experience for users and boost sales for e-commerce businesses.

## Data Source

The project utilizes an Amazon dataset that captures user ratings for electronic products. To mitigate biases, unique identifiers are assigned to each product and user instead of using names or potentially biased information.

* Access the [dataset](https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation/download?datasetVersionNumber=1) here: [Amazon Electronics Rating Dataset](https://www.kaggle.com/datasets/vibivij/amazon-electronics-rating-datasetrecommendation/download?datasetVersionNumber=1)

## Methodology

### **1) Rank-Based Product Recommendation**
**Objective:**
* Identify and recommend products with the highest number of ratings.
* Target new customers with popular products.
* Address the Cold Start Problem.

**Outputs:**
* Recommend the top 50 products with a minimum of 50/100 ratings/interactions.

**Approach:**
* Calculate the average rating for each product.
* Determine the total number of ratings for each product.
* Create a DataFrame using these values and sort it by average rating.
* Develop a function to retrieve the top 'n' products with a specified minimum number of interactions.

### **2) Similarity-Based Collaborative Filtering**
**Objective:**
* Offer personalized and relevant recommendations to users.

**Outputs:**
* Recommend the top 50 products based on interactions of similar users.

**Approach:**
* Convert user_id to integer values for convenience.
* Develop a function to find similar users:
  1. Compute the cosine similarity score between the desired user and each user in the interaction matrix.
  2. Extract and return similar users and their similarity scores.
* Develop a function to recommend products:
  1. Utilize the similar users function to identify users similar to the desired user_id.
  2. Find products the original user has interacted with (observed_interactions).
  3. For each similar user, identify 'n' products they have interacted with but the original user has not.
  4. Return the specified number of products.

### **3) Model-Based Collaborative Filtering**
**Objective:**
* Provide personalized recommendations based on user behavior and preferences, addressing challenges of sparsity and scalability.

**Outputs:**
* Recommend the top 50 products for a specific user.

**Approach:**
* Convert the matrix of product ratings to a compressed sparse row (CSR) matrix for efficiency.
* Apply singular value decomposition (SVD) on the CSR matrix to reduce dimensionality to 50 latent features.
* Calculate predicted ratings for all users using SVD.
* Store predicted ratings in a DataFrame and develop a function to recommend products based on rating predictions.
* Evaluate the model by calculating the Root Mean Squared Error (RMSE) between actual and predicted ratings.
