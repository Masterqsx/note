### Review of
## Automatic Curation of Golf Highlights using Multimodal Excitement Features
***
**Video Summarization, Self-Supervised Learning, Highlights Generate**
#### 1. Purpose
Automatically mark highlight clip for golf videos.
#### 2. Highlight Marker Framework
```

    | ---------> OCR on the caption ----> Player Info and # of Hole
    |
 Input Video --> Crowd Cheering Marker  --------------------->   
    |             |                                          |
    |     Shot Boundary Detection                            |
    |             |                                          |
    | ------ Clips with Positive Score --> Player Reaction -->
                  |                                          |
                  --> Audio Commentator Excitement -- Linear combination
                                                             |
                                                           Score
```
#### 3. Crowd Cheering Marker
```
 Soundnet conv-5 layer --> SVM --> 99.4% Accuracy
```

#### 4. Audio Commentator Excitement Marker
```
 Soundnet conv-5 layer --> SVM  ------>
                                      |
 Sentiment Analysis (Bag of Words) --->  Average
 ```
#### 5. Player Reaction Marker
```
 Low Threshold Soundnet conv-5 layer + SVM --> VGG-16 Retrained
```
#### 6. Self-Supervised Player Recognition
```
        Faster-RCNN + Player name in caption(Mark face name)
                        |
 VGG Face fc7 features + k-means clustering + largest cluster
                        |
            Keep only one face per frame
                        |
  Use collected data fine tune VGG Face Net by adding softmax
```
In future, can we augment face data by animated 3D face scan? 
#### 7. Interesting Metric for Ranking Quality - NDCG
Normalized Discounted Cumulative Gain:
$$
NDCG(k) = \frac{1}{Z}\sum_{i=1}^{k}\frac{2^{rel_i}-1}{log_2(i+1)}
$$
