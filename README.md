# CancellableMultiInstanceBiometrics
Methods Used to Develop the Model
The development of this model involved a structured pipeline of preprocessing, feature extraction, data augmentation, fusion, and classification using CNN. Below is a summary of the key methods and techniques employed:
________________________________________
# 1. Data Preprocessing
1.Iris Image Dataset: 
The dataset contained iris images for 45 unique individuals, with separate folders for left and right eyes, each having 5 original images.

2.Augmentation:	Images were rotated by {±10,±20,±30} to increase data variety, resulting in a total of 35 images per eye (5 originals + 30 augmented).
________________________________________
# 2. Feature Extraction
1.Dimensionality Reduction:	
Principal Component Analysis (PCA) and Random Projection were applied to compress and represent images in lower-dimensional spaces, extracting key features while retaining critical information.
This reduced feature size significantly, making it computationally efficient for training.
________________________________________
# 3. Feature Fusion
Features from the left and right eyes were fused into a single feature vector for each individual. This was achieved by concatenating feature representations from both eyes.
________________________________________
# 4. Template Naming and Saving
The fused features were saved as .npy files in the format:
class_label_template_idx.npy, where:

class_label: Individual identifier (0-44).

template_idx: Template index (1-35).
________________________________________
# 5. Data Splitting
Shuffling: The templates were shuffled to ensure diversity in the train-test split.
 
Train-Test Split:A 2:1 ratio was used:

2/3 for testing to evaluate the model on diverse samples.

1/3 for training to develop the model.

This avoided overfitting to specific angles or augmentation variations.
________________________________________
# 6. Model Architecture
A 1D Convolutional Neural Network (CNN) was designed for classification:

Layers:

Convolutional Layers for feature extraction with kernels capturing spatial relationships.

Pooling Layers for dimensionality reduction and retaining essential patterns.

Fully Connected Layers for learning complex patterns.

Softmax Layer for multi-class classification (45 classes).

Regularization:

Dropout was introduced to combat overfitting.

Early stopping prevented unnecessary overtraining.
________________________________________
# 7. Optimization and Learning Techniques
Callbacks:

Early Stopping: Monitored validation loss and stopped training when improvements plateaued.

Learning Rate Scheduler: Reduced the learning rate dynamically if validation loss stagnated.

Loss Function:	Sparse Categorical Crossentropy for multi-class classification.

Optimizer:
Adam Optimizer, chosen for its adaptive learning rate and efficiency.
________________________________________
# 8. Evaluation Metrics
Accuracy and Loss:Monitored on both training and validation datasets over multiple epochs.

Generalization Gap:	Analyzed differences between train and test performance to assess overfitting and model robustness.
________________________________________
# 9. Performance Insights
For 2/3 training split and 1/3 testing split
The model achieved:

Training Accuracy: 99%

Testing Accuracy: 72% 

The generalization gap suggested moderate overfitting, which was mitigated through regularization and better data splits.
Screenshot:
![image](https://github.com/user-attachments/assets/21d07f0c-5526-4012-a424-f0c0e09e68dc)

________________________________________


For 80% training split 20% testing split:

The final model achieved:

Training Accuracy: 99%

Testing Accuracy: 92% 

Screenshot:
![image](https://github.com/user-attachments/assets/3046b9da-686c-4b42-9b50-a95bf480501b)


