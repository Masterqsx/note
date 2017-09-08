### Review of
## Automatic Curation of Golf Highlights using Multimodal Excitement Features
***
##### 1. Purpose
Automatically mark highlight clip for golf videos.
##### 2. Highlight Marker Framework
```
Input Video --> Crowd Cheering Marker  --------------------- >   
    |             |                                          |
    | ------ Clips with Positive Score --> Player Reaction -->
                  |                                          |
                  --> Audio Commentator Excitement -- Linear combination --> Score
```
