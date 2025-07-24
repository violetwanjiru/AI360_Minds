# Edge AI Prototype Report: Lightweight Image Classification for Recyclable Items

## Objective

Develop a lightweight image classification model using TensorFlow and TensorFlow Lite to recognize recyclable items from images. The model is trained on a multi-class waste dataset, converted to TensorFlow Lite, tested for accuracy, and evaluated for deployment on edge devices.

---

## Data Loading and Preprocessing

- **Dataset:** Provided as `/content/waste.zip`, containing images organized into class-specific subdirectories.
- **Extraction:** The zip file was extracted, revealing the class folders under `/content/waste/waste/images/images`.
- **Loading:** Used `tf.keras.utils.image_dataset_from_directory` to load images, with an 80/20 train/validation split, image size of 128x128, and batch size of 32.
- **Normalization:** Images were rescaled to [0, 1] using a normalization layer.
- **Classes:** 30 waste categories, including items like `plastic_trash_bags`, `aluminum_soda_cans`, `glass_food_jars`, etc.

---

## Model Architecture

- **Type:** Lightweight Convolutional Neural Network (CNN)
- **Layers:**
  - 3 Convolutional layers (filters: 16, 32, 64) with ReLU activation and MaxPooling
  - Flatten layer
  - Dense layer (128 units, ReLU)
  - Output Dense layer (30 units, softmax for multi-class classification)
- **Summary:** The model is compact, suitable for edge deployment, and designed to balance accuracy and efficiency.

---

## Training

- **Optimizer:** Adam
- **Loss:** Categorical Crossentropy
- **Metrics:** Accuracy
- **Epochs:** 15
- **Results:**  
  - **Training Accuracy:** ~97%  
  - **Validation Accuracy:** ~62.8%  
  - **Validation Loss:** ~3.98

*Note: The gap between training and validation accuracy suggests some overfitting, likely due to model simplicity, dataset complexity, or class imbalance.*

---

## Model Conversion and Testing

- **Conversion:** The trained Keras model was converted to TensorFlow Lite using `tf.lite.TFLiteConverter.from_keras_model`.
- **File:** Saved as `waste_classifier.tflite`.
- **Testing:**  
  - Loaded the TFLite model with `tf.lite.Interpreter`.
  - Ran inference on a sample validation image.
  - **Sample Result:**  
    - True Class: `plastic_trash_bags`  
    - Predicted Class: `plastic_trash_bags`  

---

## Visualization

- **Accuracy Plot:** Training and validation accuracy were plotted over epochs, showing high training accuracy but lower validation accuracy, indicating overfitting.

---

## Edge AI Benefits

Deploying this model on edge devices (e.g., Raspberry Pi, smartphones, smart bins) offers:

- **Low Latency:** Real-time classification without cloud round-trip.
- **Reduced Bandwidth:** No need to upload images for inference.
- **Enhanced Privacy:** Data stays local, improving user privacy.
- **Cost-Effectiveness:** Reduces ongoing cloud compute costs.
- **Offline Capability:** Works without continuous internet access.

---

## Deployment Steps

1. **Obtain the TFLite Model:** Use `waste_classifier.tflite`.
2. **Select Edge Device:** E.g., Raspberry Pi, Android phone, or embedded system with TensorFlow Lite support.
3. **Integrate Model:** Use TensorFlow Lite interpreter in your application.
4. **Preprocessing:** Resize images to 128x128 and rescale pixel values to [0, 1].
5. **Inference:** Run images through the TFLite model to get class predictions.
6. **Postprocessing:** Map output probabilities to class names for actionable results.
7. **Application Logic:** Use predictions to drive sorting mechanisms, display results, or trigger alerts.

---

## Limitations and Recommendations

- **Validation accuracy (~62.8%)** indicates room for improvement.
- **Potential improvements:**
  - Data augmentation for better generalization.
  - Address class imbalance.
  - Experiment with more complex or pre-trained models (transfer learning).
  - Hyperparameter tuning.
  - Increase image resolution if feasible.

---

## Conclusion

A lightweight CNN model was successfully trained and converted to TensorFlow Lite for real-time recyclable item classification. Edge AI deployment enables fast, private, and cost-effective waste sorting, with potential for further accuracy improvements.

**Dataset Source:**  
The dataset used for this project is from Kaggle: [Recyclable and Household Waste Classification](https://www.kaggle.com/datasets/alistairking/recyclable-and-household-waste-classification).

However, the model's validation accuracy of around 62.8% indicates that there is room for improvement. Several factors could contribute to this inaccuracy:

- **Dataset Size and Variety:** While 15,000 images is a good starting point, the complexity of distinguishing between 30 classes of waste might require a larger and more diverse dataset. Variations in lighting, angles, and the state of the waste items can also impact performance.
- **Class Imbalance:** Some classes in the dataset might have significantly more images than others. This can lead to the model being biased towards the majority classes and performing poorly on minority classes.
- **Model Architecture Complexity:** The current lightweight CNN model, while suitable for edge deployment, might not be complex enough to capture the intricate features needed to differentiate between all 30 waste categories effectively. More complex architectures or pre-trained models might be necessary.
- **Hyperparameters:** The chosen hyperparameters (e.g., learning rate, batch size, number of epochs) might not be optimal for this specific dataset and model architecture.
- **Overfitting:** While the training accuracy is very high (around 97%), the validation accuracy is significantly lower. This suggests that the model might be overfitting to the training data and not generalizing well to unseen images. The lack of regularization and data augmentation in the initial training could contribute to this.
- **Image Resolution and Quality:** The image size of 128x128 pixels might be too low to preserve enough detail for accurate classification of some waste items, especially those with subtle differences.
- **Labeling Errors:** Inaccurate labels in the dataset can also lead to the model learning incorrect associations.

To improve the model's accuracy, future work could include data augmentation, addressing class imbalance, experimenting with more complex or pre-trained models (transfer learning), hyperparameter tuning, and increasing image resolution if feasible. These strategies can help the model generalize better and achieve higher accuracy in real-world applications.