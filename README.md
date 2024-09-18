
# Recommender Systems 2023/24 Challenge Polimi on Kaggle

This repo contains the code, data and the resulted models used in the  [RecSys Challenge 2023/24 A. Y.](https://www.kaggle.com/competitions/recommender-system-2023-challenge-polimi/overview) at PoliMi that was hold at kaggle.
The goal of the competition was to biuld a recommender system model for books recommendations providing Top-10 ranking for each user. The ratings in the train data are implicit only URM was given. 

# Results

Private MAP@10 - 0.13765

Public MAP@10 - 0.13731

# Competition setting 

The application domain is book recommendation. The datasets provided contains interactions of users with books, in particular, if the user attributed to the book a rating of at least 4. The main goal of the competition is to discover which items (books) a user will interact with.

The datasets includes around 600k interactions, 13k users, 22k items (books).
The training-test split is done via random holdout, 80% training, 20% test.
The goal is to recommend a list of 10 potentially relevant items for each user. MAP@10 is used for evaluation. 

# Methods

- Item-based recommdation models
- ML recommedation models
- Variational autoencoder recommender system
- 5-fold cross-validation
- Bayesian search
- User-wise rankings
- Hybridisation
- XGboost reranking

# Path to our Best model 

Our best recommender is a hybrid. The following steps led us to our best score:

1. SLIM elasticnet + hyperparameters search with 5-fold CV - standalone public MAP@10 0.13484

2. Merge of item-item similarity matrices of SLIM elasticnet&Item-based CF - public MAP@10 0.13614

3. Similarity matrix merge of model from point 2 with EASER optimized by Bayesian search - public MAP@10 0.13636

4. XGboost reranking of model rankings form point 3. XGboost features are SLIMelasticnet, RP3Beta, Item-based CF and EASER scores, item and user profile lengts - public MAP@10 0.13641

5. User-wise recommdations of the model from point 3 with user-division into 20 groups according to their profile length - private MAP@10 0.13765

# Team 

[Me](https://github.com/LucaBrembilla) and [Max](https://github.com/BigDataSeeker)

# Credits

The repo is based on the codes from [the repo of Maurizio Dacrema](https://github.com/MaurizioFD/RecSys_Course_AT_PoliMi)
