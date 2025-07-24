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

🟣 **Part 4: Reflection & Workflow Diagram (10 points)**

**Reflection (5 points)**

This assignment deepened my understanding of the full AI lifecycle—from problem scoping to deployment, ethics,
and monitoring. Working through real-world scenarios like medical diagnosis reinforced the importance of aligning
technical choices with societal needs, especially in sensitive domains like healthcare. The integration of 
fairness and bias audits was especially enlightening, emphasizing that AI is not just a technical 
endeavor but a socio-technical system.

**Workflow Diagram (5 points)**

Here’s the text-based description of the diagram:

Data Ingestion → 2. Preprocessing (Normalization, Augmentation) → 3. Model Training (CNN) → 
4. Evaluation (F1-Score, Confusion Matrix) → 5. Bias Detection (Demographic Stratification) → 
6. Deployment (Cloud API) → 7. Monitoring (Performance Logs, Drift Alerts) → 
8. Retraining (New Data Integration)
