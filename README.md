# Machine Learning Assignment #3 - Multi-Task Image Classification (Activity & Time of Day)
## Course Information 
- University: Birzeit Universit
- Faculty: Engineering and Technology
- Department: Computer Engineering
- Course: ENCS5341 – Machine Learning and Data Science
- Instructor: Dr. Yazan Abu Farha
- Assignment#3

## Project Overview
- This project addresses a multi-task classification problem using image data, where the goal is to simultaneously predict:
  - Activity (e.g., sightseeing, hiking, relaxing)
  - Time of Day (morning, afternoon, evening)

- We compare three models:
    - k-Nearest Neighbors (k-NN) – Baseline
    - Random Forest (RF) – Ensemble method
    - Convolutional Neural Network (CNN) – Deep learning approach
## Objectives
  - Perform multi-task classification
  -  Compare classical ML vs deep learning
  -  Handle class imbalance and data sparsity
  -  Improve model generalization through tuning

## Dataset & Preprocessing
### Data Preparation
- Cleaned and standardized categorical labels
- Removed invalid time-of-day entries
- Replaced missing activity labels with "No Activity"
- Converted all text to lowercase
### Feature Extraction
- Used ResNet-50 (pre-trained) as a feature extractor
- Removed final classification layer
- Extracted 2048-dimensional embeddings per image
### Exploratory Data Analysis (EDA)
#### Key Findings
 - Severe class imbalance in Activity labels
 -  Balanced Time-of-Day classes
 -   Moderate correlation between Activity & Time
####  chniques Used
- Cramér’s V Heatmap
- Bar plots & stacked bar charts
#### Statistical summaries
##### Models & Results
###### Model 1: k-Nearest Neighbors (Baseline)
       - Performance
          Task	       Best Accuracy	   Notes
          Time of Day	     ~56%	         Works reasonably well
          Activity	       ~48%	         Struggles due to many classes
       - Insights
         - Works for simple tasks
         - Fails with high-class imbalance & many categories
##### Model 2: Random Forest
-  Hyperparameter Tuning
    n_estimators: [50, 100, 200, 400, 600]
- Performance
   Task	        Accuracy	Notes
   Time of Day	~64–65%	  Improved over k-NN
   Activity	    ~56–59%	  Still challenging
- Insights
  - Handles non-linear relationships better
  - Still struggles with rare classes
##### Model 3: Convolutional Neural Network (CNN)
-Architecture
  - Conv1D layers
  - Dense layers
  - Dropout + L2 regularization
- mprovements Applied
  - Increased Dropout (0.5 → 0.7)
  - Reduced dense layer size (256 → 128)
  - Added L2 regularization
-Final CNN Performance
    Task	       Accuracy
    Time of Day	 63.30%
    Activity	   59.38%
- Key Improvements
  - Higher dropout → better generalization
  - L2 regularization → reduced overfitting
  - Balanced precision, recall, and F1
- Error Analysis
  - Confusion between:
    - Evening vs Afternoon
    - Boat Riding vs Swimming
- Challenges
    - Class imbalance
    - Similar visual features
    - Limited dataset size
- Final Comparison
   Model	        Best For	            Limitation
   k-NN	          Simple tasks	        Poor scalability
  Random Forest	  Non-linear patterns	  Weak on rare classes
CNN	 Best overall	Needs more data
- Conclusion
   - CNN achieved the best performance overall
   - Time-of-Day prediction is easier than Activity
   - Class imbalance significantly affects results
- Key Takeaways:
  - Deep learning outperforms traditional ML in image tasks
  - Proper regularization is crucial
  - Data quality & balance are critical
- Future Work
  - Data augmentation
  - Class balancing techniques (SMOTE, weighted loss)
  - Advanced architectures (ResNet fine-tuning)
  - Multi-task learning optimization
## Repository Structure
```
├── data/                # Images & labels
├── features/            # Extracted embeddings
├── models/              # Trained models
├── notebook.ipynb       # Implementation
├── report.pdf           # Assignment report
└── README.md
```
