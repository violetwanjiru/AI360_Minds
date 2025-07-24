🟣 Part 1: Short Answer Questions – Evaluation & Deployment (8 points)

Select 2 evaluation metrics and explain

Accuracy: Accuracy measures the proportion of correct predictions over total predictions. It’s useful when classes are balanced but can be misleading in imbalanced datasets.

F1-Score: The F1-score balances precision and recall, making it valuable for imbalanced datasets (e.g., in healthcare where false negatives can be critical). It helps assess model performance where both false positives and false negatives matter.

Explain concept drift and how to monitor

Concept drift occurs when the statistical properties of the target variable change over time, reducing model performance. For example, a model predicting consumer behavior might degrade when customer preferences evolve.

Monitoring approaches:

Track performance metrics (e.g., accuracy, F1) over time.

Use data drift detection tools like Kolmogorov–Smirnov test or ADWIN.

Re-train models periodically or when drift is detected.

Describe 1 technical challenge

A common challenge is integrating machine learning models into production environments. For example, aligning a model’s dependencies, runtime, and scalability with existing infrastructure can require containerization (e.g., using Docker) and orchestration tools like Kubernetes for deployment
🟣 Part 2: Case Study Application

**A. Problem Scope (5 points)**

Problem: A healthcare organization wants to automate diagnosis support using medical imaging data (e.g., chest X-rays) to detect conditions like pneumonia.

Scope:

Data: DICOM images and clinical metadata.

Task: Binary classification (disease present or not).

Constraints: Privacy regulations (e.g., HIPAA), need for explainability, and infrastructure limitations in rural clinics.

**B. Deployment (10 points)**

**Steps:**

Model Packaging: Convert the model using ONNX or TensorFlow SavedModel for deployment.

Infrastructure: Host on cloud (e.g., AWS SageMaker) or Edge devices (e.g., hospital servers).

API Integration: Develop RESTful API to integrate model with clinical software.

Monitoring: Set up automated logging and performance tracking.

Retraining Loop: Schedule periodic retraining with new data to ensure performance.

**C. Optimization (5 points)**

Techniques:

Quantization: Reduce model size and latency.

Pruning: Remove redundant weights to improve inference time.

Caching results for repetitive inputs (if applicable).

Use edge computing to reduce latency and protect data.

🟣 **Part 3: Critical Thinking – Ethics & Bias (10 points)**

**Ethical Considerations:**

Bias: Medical datasets often lack diversity, causing underperformance for minority groups.

Fairness: False negatives in diagnosis may disproportionately harm certain populations.

Transparency: Black-box models reduce trust among clinicians and patients.

Data Privacy: Using sensitive health data requires secure storage and strict access controls.

Accountability: Responsibility must be clearly assigned when AI informs medical decisions.

Strategies:

Diverse, representative training datasets.

Bias audits during model validation.

Transparent model explanations using SHAP/LIME.

Clear documentation of limitations and risks.


