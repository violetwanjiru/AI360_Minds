🟪 Part 3 – Critical Thinking (10 pts)

🟡 Interpretability vs. Accuracy

Interpretability and accuracy often conflict in AI models. Simpler models (like decision trees or linear regression) are easier to understand but may lack accuracy on complex data. Deep neural networks, while accurate, are often considered "black boxes."

Trade-off Example:
In healthcare, interpretable models may be preferred so doctors understand why an AI recommends a treatment. However, sacrificing too much accuracy could risk patient safety. Balancing both depends on the context.

🟡 Model Choice under Resource Constraints

In low-resource environments (e.g., rural schools, mobile devices), computationally efficient models like MobileNet or decision trees are better than complex deep learning models requiring GPUs.

Strategies include:

Using lightweight models (e.g., TensorFlow Lite versions)

Quantization/pruning

Leveraging Edge TPUs or Raspberry Pi for affordable inference