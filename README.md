# Reccomendation_Engine_Evaluations

The objective of this report is to identify the best recommendation algorithm for the bigMovieLense and Groceries Dataset. In the case of bigMovieLense, the aim of the algorithm is to recommend users movies they haven’t seen but would like to see. While for Groceries, the algorithm aims to recommend users the the most relevant products that they would likely to buy. The core metrics that we adopt to evaluate the algorithm are: Accuracy, Precision and Mean Squared Error.

 - Accuracy measures how often the algorithm is correct out of all predictions
 - Root mean square estimation is an estimate for the average difference between the predicted value and the actual value. We aim at an algorithm with the lowest RMSE.
- Precision: Out of all the recommended items, how many did the user actually like. The higher the precision the better the algorithm.

## MovieLense Analysis 
This section explores the different algorithms and different parameters of each algorithm for the dataset bigMovieLense. There is 6,040 users and 3,449 movies making 999,714 ratings.

## MovieLense Discussion 

<img width="650" alt="Screen Shot 2019-04-04 at 15 22 04" src="https://user-images.githubusercontent.com/44138106/55559911-731d8e00-56ef-11e9-87c0-333f1d3912a9.png">

From our above comparison of the three models, we can see that, with our best parameter set, the UBCF model performs better on our test data set than the IBCF and ALS. The UBCF shows better results in both the ROC curve and the precision recall curves. Additionally, UBCF has a higher accuracy score compared to the other 2 models.

An explanation for the better performance of the UBCF could be that in the current dataset, there is still a low number of users. For movie recommendation engines of companies like Netflix and Amazon, IBCF is likely to outperform since the number of users is significantly larger than the number of movies. From a business perspective, a good movie recommendation system is a combination of content-based filtering and collaborative filtering which potentially takes advantage of both the representation of the content as well as the similarities among users. This task could be done with extra information about the content of the movie.

Our final selected model is **UBCF with parameter of 100 nearest neighbors and Jaccard similarity and normalise by center.**

## Groceries Analysis 
There are 9835 transactions with 169 categories. The labels mentioned above which are then grouped into 55 levels of 2 categories which are then groupped into 10 levels of 1 category.

## Groceries Discussion 

<img width="675" alt="Screen Shot 2019-04-04 at 15 33 34" src="https://user-images.githubusercontent.com/44138106/55559912-73b62480-56ef-11e9-885c-6b91b15412d3.png">

Having to choose 1 model, we find that the best fit one is the **IBCF**. The reason behind our choice is as follow:

AR has the highest accuracy rate, however it is only based on specific set of rules. Most of the rules will recommend a similar item. For example, out of the 125 rule,s most of them will recommend Whole milk and other Vegetables. What about the other items which are on our item list? The selection of recommendation in this case is very limited and not so personalised. AR doesn’t take into account the order of items; it simply tries to get the best rules. Therefore it’s understandable to get “unintuitive” rules like recommending the items that the user has already bought because maybe it correlates with other items that he has bought. We believe this would be a good model to use for the placement of the items in the store, rather than to target a specific clients to add items in their basket.

Popularity model, not the best accuracy, and a biased recommender. This model will be recommending to all the clients the same item (can be a good model for the check out counter for example). The model doesn’t tailor-make the recommendations to the clients and also, same issue as the AR model, doesn’t go through all the items available in our store.

UBCF is a good model however its accuracy rate was below the IBCF one and that is the reason it wasn’t selected. Therefore, our final selected model is IBCF with parameter of 10 nearest items and Cosine similarity.
