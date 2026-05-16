# Literature Review

Approaches or solutions that have been tried before on similar projects.

**Summary of Each Work**:

 Source 1: Exploring the Relationship between Music and Mood through Machine Learning Techniques

- **Link:** [https://dl.acm.org/doi/epdf/10.1145/3647444.3647916](https://dl.acm.org/doi/epdf/10.1145/3647444.3647916)

- **Objective:** To analyze the relationship between musical components and emotional states using machine learning techniques in order to build personalized music recommendations for therapy and mental health support.

- **Methods:** The study utilizes a Spotify music dataset sourced from Kaggle. Data preprocessing includes normalization/standardization scaling, mean-value imputation for missing data, and categorical variable encoding (label and one-hot encoding). Five machine learning algorithms are trained and evaluated using supervised learning techniques: Random Forest, Support Vector Machine (SVM), Logistic Regression, Naive Bayes, and Neural Networks. Unsupervised learning is also applied to discover similar song clusters.

- **Outcomes:** The Random Forest model achieved the highest predictive performance with an accuracy of 82.22% and an AUC of over 96.09%. Naive Bayes performed second best with an accuracy of 80.32% and an AUC score of 95.75%, whereas Logistic Regression, SVM, and Neural Networks performed significantly worse. Specific musical elements such as key, tempo, and mode were directly linked to specific emotional categories.

- **Relation to the Project:** This paper serves as an excellent benchmark for our classification pipeline. Because our project focuses on "happy" vs. "sad" playlist data, this study's findings on how structural properties (like key, tempo, and mode) map to positive or negative emotional categories will help validate our model’s feature importances. Additionally, its comparative analysis suggests that ensemble methods like Random Forest could serve as highly competitive models for our classification task.
	 
Source 2: How Does the Spotify API Compare to the Music Emotion Recognition State-of-the-Art?

- **Link:** [https://d1wqtxts1xzle7.cloudfront.net/99948664/44W4Ao3Sx9CdMTDx2RrJ-libre.pdf?1679014316=&response-content-disposition=inline%3B+filename%3DHow_Does_the_Spotify_API_Compare_to_the.pdf&Expires=1778927783&Signature=ajQ7fS~VFt0EtY28GcFoWwHdqbRl6GbQ~mn31j6Y9KWvv8GPqYWhSutaKx6-fVe3xE~JnLrbt7HCZRlCqA4Y213Xg3pdOZY86g9TUSZ-tReYNoMeXbFMu60T1nHLduBqk9wgSXfS5RPmV8OZdnckmS-QVEG3No-gkNLuW57j55wesqXY8AC4rebrbiGISjR2toUBcrBRmjVHzW8WzERwUThKcnripx79J6QmaFgH224SvsIPPmrEsVn3K1OzX-e~1VI0CbzWV5agq191u4GCYrMmprDz0n~JIhgHMbhTRy4AGplfWCS7gq4XismRQMmb8vrUhzcLediAfEmnIaoWHg__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA](https://d1wqtxts1xzle7.cloudfront.net/99948664/44W4Ao3Sx9CdMTDx2RrJ-libre.pdf?1679014316=&response-content-disposition=inline%3B+filename%3DHow_Does_the_Spotify_API_Compare_to_the.pdf&Expires=1778927783&Signature=ajQ7fS~VFt0EtY28GcFoWwHdqbRl6GbQ~mn31j6Y9KWvv8GPqYWhSutaKx6-fVe3xE~JnLrbt7HCZRlCqA4Y213Xg3pdOZY86g9TUSZ-tReYNoMeXbFMu60T1nHLduBqk9wgSXfS5RPmV8OZdnckmS-QVEG3No-gkNLuW57j55wesqXY8AC4rebrbiGISjR2toUBcrBRmjVHzW8WzERwUThKcnripx79J6QmaFgH224SvsIPPmrEsVn3K1OzX-e~1VI0CbzWV5agq191u4GCYrMmprDz0n~JIhgHMbhTRy4AGplfWCS7gq4XismRQMmb8vrUhzcLediAfEmnIaoWHg__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA)

- **Objective:** To evaluate the suitability and emotional relevance of the 12 high-level audio features provided by the public Spotify API when applied to Music Emotion Recognition (MER), comparing them against engineered, state-of-the-art handcrafted academic audio features.

- **Methods:** 12 Spotify API features were gathered for 704 songs extracted from an established 900-song benchmark dataset annotated according to Russell's emotional quadrants. These features were compared with 100 top-ranked standard academic features extracted via MIR Toolbox, Marsyas, and PsySound3. The ReliefF algorithm was applied to rank feature relevance individually and in combination, and classification was completed using Support Vector Machines (SVM/SMO implementation in Weka) with 10-fold cross-validation.

- **Outcomes:** Out of the 12 Spotify features, _energy_, _valence_, and _acousticness_ were identified as highly relevant to MER. However, using the 12 Spotify features alone yielded subpar classification performance compared to academic features (58.5% vs. 74.7% F1-measure). Combining the feature sets yielded slight performance enhancements with a smaller subset of features (e.g., top 5 or top 10 combined sets), but did not increase the overall peak accuracy of the academic baseline.

- **Relation to the Project:** This study is vital to our project design because it directly critiques the limitations of relying _solely_ on Spotify API's default audio features. It reveals that while high-level features like _valence_ (musical positiveness) and _energy_ are foundational for separating happy and sad music, the out-of-the-box API metrics might exhibit minor performance bottlenecks. This insights underscores the benefit of utilizing the deeper "track-level analysis data" (such as detailed timbre, pitch, or rhythmic intervals from the Spotify API's `audio-analysis` endpoint) to capture nuances that standard high-level features miss.
    
 Source 3: RIADA: A Machine-Learning Based Infrastructure for Recognising the Emotions of Spotify Songs

- **Link:** [https://www.ijimai.org/index.php/ijimai/article/view/435/527](https://www.ijimai.org/index.php/ijimai/article/view/435/527)

- **Objective:** To design and deploy a scalable, cloud-based software engineering infrastructure (RIADA) capable of automatically assigning affective annotations to Spotify's massive catalog based on user perception.

- **Methods:** Instead of utilizing raw audio processing, the infrastructure leverages text data from popular user-generated Spotify playlists gathered via the Spotify Playlist Miner. Deducing emotional labels through targeted keyword matching across Russell's quadrants, a dataset of 5,192 uniquely annotated songs was created. Statistical relevance tests (Chi-Squared, ANOVA F-value, and Mutual Information) were combined with music expert feedback to prune audio features for each target emotion quadrant. Models were built utilizing SVM, KNN, and Random Forest classifiers across a 70/30 stratified train-test split. The system's back-end was parallelized using a Master-Worker architecture pattern deployed across a distributed cloud environment (OVHcloud and MongoDB).

- **Outcomes:** Breaking the multi-class problem into four independent binary quadrant subproblems allowed Random Forest models to perform best, reaching a high mean classification accuracy of 88.75% across the quadrants. The implementation achieved a Technology Readiness Level of TRL-6. External validation using a 60,000-song AcousticBrainz dataset confirmed robust generalizability with an average validation accuracy over 72%.

- **Relation to the Project:** RIADA mirrors our project's methodology by leveraging existing Spotify playlist data to define ground-truth emotional labels. It validates our exact data collection approach, demonstrating that curation metadata (e.g., pulling tracks directly from "happy" or "sad" themed playlists) is an effective and scalable alternative to manual laboratory emotional annotations. We can use their feature pruning strategies (ANOVA, Chi-Squared) as a guide when cleaning and filtering our own extracted API feature vectors.
    
 Source 4: Music Mood Prediction Based on Spotify's Audio Features Using Logistic Regression

- **Link:** [https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10109396](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10109396)

- **Objective:** To design a supervised learning framework evaluating the targeted performance of a Logistic Regression model in predicting distinct tracks' moods using Spotify's 12 audio features.

- **Methods:** A balanced dataset of 1,500 tracks spread evenly across four designated moods (energetic, calm, sad, happy) was compiled through the Spotify API via playlist Uniform Resource Identifiers (URIs). Data cleansing routines systematically isolated and deleted duplicates. The data split dedicated 80% to training and 20% to testing. A Logistic Regression model was trained via Python's `sklearn` library. Recursive Feature Elimination (RFE) was applied to rank feature significance, and the system was cross-validated using a stratified 10-fold technique.

- **Outcomes:** The Logistic Regression approach achieved a highly effective overall mean accuracy of 96.00% across the four mood classes. On an individual class basis, it reached F1-scores of 92.59% for Calm, 84.89% for Energetic, 79.73% for Happy, and 86.10% for Sad tracks. RFE identified _energy_, _acousticness_, and _valence_ as the three most statistically defining musical properties affecting classification performance.

- **Relation to the Project:** This paper is a close match to our target implementation. It explicitly uses the Spotify API to pull playlist track features to predict "happy" and "sad" variants. It shows that standard statistical models like Logistic Regression can yield exceptionally high accuracies (96.00%) given rigorous data cleansing and balanced class distribution. It establishes a definitive baseline architecture for our work, verifying that our feature selection should lean heavily on _energy_, _valence_, and _acousticness_ as core identifiers during our predictive mapping.
