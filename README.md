# CS-412 Project Report

## Project Overview
At the beginning of the project, our goal was to take the example model provided to us, modify it with our own adjustments, and create an improved model to achieve better results.

## Regression Task - Round 1
To enhance the regression model, we made the following improvement: instead of calculating the **average like count across all posts** as in the example, we categorized posts based on their `media_type` and calculated a **separate average like count for each media_type**.

The model we created as a result was quite successful, achieving a **regression error score of 660.553606**, which placed us in **5th position**.

## Classification Task - Round 1
For the classification task:
- We **added the captions** of the posts into a corpus and vectorized each word to create features.
- These features were combined with the `category_name` parameter of the profiles to design the model.
- Additionally, we incorporated **annotations** that we created as training data to increase the sample size.

Although our model achieved a relatively high accuracy score of **0.73** in our own tests, it did not perform as well on the actual test data, resulting in an accuracy score of **0.570796**, placing us in **85th position**.

## Classification Task - Round 2
In the second round, we aimed to improve our classification performance by:
- Using the **biography field** as an additional feature.
- Processing biographies similarly to captions and including them as a parameter.

This improvement raised our accuracy score to **0.634361**, but despite the improvement, we placed **93rd**.

## Regression Task - Round 2
Since we performed well in the regression task during the first round, we continued using the same code. However, in this round:
- Our regression error increased to **761.794131**, causing us to drop to **41st position**.

## Final Round - Regression Enhancements
In the final round, we sought to enhance our regression task by incorporating:
- **Percentile features:** We focused on the **0.95 percentile** to account for rare posts that receive significantly higher likes, which could distort averages.
- **Timestamp features:** Including timestamps helped mitigate the effect of very old posts, which might inaccurately influence the `like_count`.

## Final Round - Classification Challenges
Unfortunately, we tried various approaches in the final round, such as:
- Adding **entities feature**,
- Using **random forest** as the classifier,
- Testing **5–10 different BERT models**.

However, none of these approaches yielded better results. When comparing our predictions to the (presumably) expected results, we were unable to achieve significant improvements. As a result, we decided to use our **Round 2 classification model** for the final submission.


**Note:** During the training phase, the `username` column in the dataset was unnamed. To resolve this issue, we renamed the column to `username`.

---

## Main Analysis and Important Findings

### Regression Task
1. **Media-Type Categorization**: 
   - By categorizing posts based on their `media_type` and calculating separate average like counts for each category, we achieved significant improvement in regression accuracy.
   - This enhancement reduced noise from mixing posts with varying engagement levels and led to a **regression error score of 660.553606** in Round 1, placing us in **5th position**.

2. **Challenges with Round 2 Regression**:
   - Reusing the same approach in Round 2 led to a drop in performance with an error score of **761.794131**. This highlighted the importance of incorporating additional features to adapt to evolving datasets.
   - In the final round, the introduction of **percentile features** (focusing on the 0.95 percentile) and **timestamp handling** improved the robustness of the model. These features addressed outliers and the effects of older posts on the regression task.

### Classification Task
1. **Captions and Category Names**:
   - Vectorizing post captions and combining them with the `category_name` parameter provided a strong foundation for classification. This approach achieved an **accuracy of 0.73** during internal tests in Round 1.

2. **Incorporating Biographies**:
   - Adding the `biography` field in Round 2 as an additional feature helped improve the accuracy score to **0.634361**.
   - However, the classification task remained challenging, as the model struggled to generalize well on the test data.

3. **Challenges in the Final Round**:
   - Despite exploring **entity features**, **random forest classifiers**, and **multiple BERT models**, no significant improvements were achieved.
   - This led us to revert to the **Round 2 classification model**, which balanced accuracy and computational efficiency.

### General Insights
- **Data Distribution and Quality**:
  - Imbalanced data and labels with fewer examples heavily impacted classification accuracy. Filtering out classes with insufficient samples proved critical in improving performance.

- **Feature Engineering**:
  - The importance of feature engineering was evident, especially in the regression task, where categorizing posts and handling outliers had a direct impact on results.

- **Adaptability**:
  - The project's iterative nature highlighted the need to adapt models to changing data properties, as seen in the decline of regression performance between rounds.
