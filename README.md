# PixelRec Short-Video Recommendation System

## Overview

This project builds a personalized short-video recommendation system using the PixelRec dataset. The goal is to recommend videos that users are likely to interact with based on their past behavior and video information.

We compare several recommendation methods, from a simple popularity baseline to more personalized and hybrid models.

## Dataset

Dataset: PixelRec  
Link: https://github.com/westlake-repl/PixelRec

PixelRec is a short-video recommendation dataset. It contains user-video interactions, video metadata, text information, and video cover images.

In this project, we mainly use:

- User-item interactions
- Video/item IDs
- Video tags
- Numeric metadata
- Title and description text features

## Problem Statement

The task is a Top-N recommendation problem. Given a user's past interactions, the system recommends a ranked list of videos that the user may be interested in.

This is useful because short-video platforms need personalized recommendations instead of showing the same popular videos to every user.

## Assumptions

- Users with similar interaction histories may have similar interests.
- Videos interacted with by similar users may be related.
- Popular videos are a strong baseline.
- Hybrid models using interaction data and item features may perform better than interaction-only models.

## Methodology

The project follows this workflow:

1. Load and explore the PixelRec dataset.
2. Analyze user interactions, item popularity, sparsity, and missing values.
3. Split the data into training, validation, and test sets.
4. Build baseline and personalized recommendation models.
5. Evaluate models using ranking metrics.

## Models

We implemented and compared the following models:

1. Popularity Baseline  
   Recommends the most popular videos based on training interactions.

2. Item-Based Collaborative Filtering  
   Uses item-item similarity based on user interaction patterns.

3. Matrix Factorization, NMF  
   Learns latent user and item factors from the interaction matrix.

4. LightFM Hybrid Model  
   Combines user-item interactions with item features such as tags, metadata, and text.

5. DeepFM  
   Uses user IDs, item IDs, and metadata features to learn feature interactions.

## Evaluation Metrics

The models are evaluated using Top-K ranking metrics:

- Precision@K
- Recall@K
- NDCG@K

We mainly compare model performance at K = 10.

## Results

| Model | Main Features | Test NDCG@10 |
|---|---|---:|
| Popularity Baseline | Item popularity | 0.4252 |
| Item-Based CF | User-item interactions | 0.5095 |
| NMF | Latent factors | 0.4956 |
| DeepFM | IDs + metadata | 0.5146 |
| LightFM Hybrid | Interactions + tags + metadata + text | 0.6343 |

The LightFM hybrid model achieved the best performance. This suggests that combining user behavior with item-side features improves recommendation quality.

## Key Learnings

- Popularity is a strong baseline in short-video recommendation.
- Personalized models perform better than recommending the same videos to everyone.
- Interaction patterns are useful for learning user preferences.
- Adding item features such as tags, metadata, and text improves model performance.
- LightFM worked best in this project because it can combine collaborative filtering with item features.

## Future Work

- Add image embeddings from video cover images.
- Improve the DeepFM model with more tuning.
- Test full-catalog ranking for more users.
- Analyze cold-start users and cold-start videos.
- Build a simple demo that returns Top-N recommendations for a selected user.

## Conclusion

This project compares multiple recommendation methods on the PixelRec short-video dataset. The final LightFM hybrid model performs best because it uses both user interaction history and video content features.
