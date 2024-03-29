# EEG-Eye-State-Prediction

## Notebook Link
Access the notebook on Google Colab: [EEG-Eye State Prediction Notebook](https://colab.research.google.com/drive/11Tx7Q9Gn3SijbyZy9JCNR-W2RAcw72Xm?usp=sharing)

## 1- Introduction:
Electroencephalography (EEG) is a non-invasive neuroimaging technique that records electrical brain activity over time. In this project, we aim to preprocess EEG data and develop a classification model to determine the state of the eyes (open or closed) based on the recorded signals. This project presents a comprehensive analysis of EEG signal processing and eye state classification using machine learning techniques. The dataset used contains EEG recordings from a single individual, capturing electrical brain activity while detecting the state of their eyes (open or closed). The report outlines the data characteristics, preprocessing methods, feature extraction techniques, and the application of a Random Forest Classifier for eye state classification.


## 2. Data Description:
- The EEG dataset used in this study consists of 14980 samples with 15 columns. Each column represents an electrode or measurement channel capturing electrical brain activity(14 channels). The last column serves as the target variable, indicating the eye state as follows:
  - 1 for the eye-closed state
  - 0 for the eye-open state
- The dataset captures continuous EEG measurements over a duration of 117 seconds. The eye state information was manually added based on video frame analysis.
- Dataset: [EEG Eye State Classification Dataset](https://www.kaggle.com/datasets/robikscube/eye-state-classification-eegdataset/data?select=EEG_Eye_State_Classification.csv)

## 3. Preprocessing Techniques:
The EEG data underwent several preprocessing steps to ensure data quality and suitability for further analysis. The following techniques were applied:
- Artifacts Removal: Z-score normalization was used to identify and remove outliers. Samples with z-scores exceeding a threshold of 10 were filtered out.
- Bandpass Filtering: A Butterworth bandpass filter was employed to extract specific frequency bands from the EEG data. The filter settings included a low-cut frequency of 0.5 Hz and a high-cut frequency of 50.0 Hz.
- Baseline Correction: Baseline correction involved subtracting the mean of each electrode from the filtered EEG data. This step helped reduce baseline drift and improve signal consistency.
- F7 signal before artifacts removal:
  ![image](https://github.com/hanaheshamm/EEG-Eye-State-Prediction/assets/115111861/bdb64754-4bed-489e-b04d-95c40781e618)
-F7 signal after artifacts removal:
![image](https://github.com/hanaheshamm/EEG-Eye-State-Prediction/assets/115111861/a9e3b1c6-b2b4-43e9-9dac-f210e497816b)
-F7 signal after band-pass filteration and baseline correction:
![image](https://github.com/hanaheshamm/EEG-Eye-State-Prediction/assets/115111861/b903320f-9d53-4414-8e65-2bb04b88d45f)
-F7 signal after Noise removal using “Moving Average Filter”:
![image](https://github.com/hanaheshamm/EEG-Eye-State-Prediction/assets/115111861/47c65854-178d-4dac-88dd-3d8234b6a325)



## 4. Feature Extraction:
Feature extraction played a crucial role in capturing relevant information from the EEG signals. Two types of features were extracted:
- Power Spectral Density (PSD): The Welch method was used to calculate the PSD, providing insights into the frequency domain characteristics of the EEG signals. PSD features were computed for each epoch.
- Statistical Features: Additional statistical features, including mean, variance, skewness, and kurtosis, were computed for each epoch of EEG data. These features offer information about the signal's distribution and shape.

## 5. Data Preparation:
The EEG data underwent a series of preprocessing steps to prepare it for machine learning analysis. After these preprocessing steps, the dataset was transformed into a structured format suitable for training and testing a machine learning model.
- Final Dataset Dimensions: The final dataset consisted of X samples and Y features, including the corrected EEG data, Power Spectral Density (PSD) features, and statistical features. The target variable, 'eyeDetection,' was included in the dataset, providing ground truth labels for the eye state.
- Data Splitting: The dataset was divided into a training set and a testing set using a standard train-test split technique. 60% of the data was allocated to the training set, and 40% was reserved for testing which intends to have a wide range of predictions to be used by the actuator to give actions according to the predictions made through having as much information as possible.
- Data Scaling: Prior to model training, the features were standardized using the StandardScaler from scikit-learn. This step was crucial to ensure that each feature had a mean of 0 and a standard deviation of 1, which aids in preventing any feature from dominating the model training process.

## 6. Machine Learning Algorithm:
A Random Forest Classifier was chosen as the machine learning algorithm for eye state classification. Random Forest is an ensemble learning technique known for its robustness and ability to handle high-dimensional data. The classifier was trained and evaluated using standard practices, including data scaling and splitting into training and testing sets.

## 7. Results and Discussion:
The model's accuracy and classification performance were evaluated on the test dataset, and the results are reported in the following section. The report discusses the model's effectiveness and any potential areas for improvement.

## 8. Conclusion:
This project highlights the process of EEG signal processing and eye state classification. The utilization of preprocessing techniques, feature extraction, and a Random Forest Classifier allows for the accurate determination of eye states based on EEG data. Future work may involve exploring additional feature engineering and optimization strategies to further enhance model performance.


