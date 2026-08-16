Handwritten Digit Classification: CNN vs. RNN
📌 Project Overview
Handwritten digit recognition is a fundamental computer vision problem with widespread applications in document digitization, postal automation, and bank check processing. Traditional machine learning methods often require manual feature extraction, which limits scalability and performance.

The objective of this project is to solve this problem by developing deep learning models capable of automatically learning spatial features from raw image data to accurately classify digits (0–9).

One Problem, Two Approaches
To analyze how different architectural choices affect classification performance, this project tackles the exact same problem using two distinct neural network paradigms:

Convolutional Neural Network (CNN)

Recurrent Neural Network (RNN / LSTM)

📊 The Dataset
This project utilizes the MNIST Digit Classification Dataset, which consists of grayscale images of handwritten digits.

Image Size: 28 x 28 pixels

Classes: 10 (Digits 0 through 9)

Data Splits: The data is strictly divided into x_train and x_val sets to handle training and robust validation, bypassing the need for a separate final test set. Pixel values are normalized between 0 and 1 to ensure stable and efficient model convergence.

🧠 Architecture Differences: How They Work
While both models are trained on the same x_train data and evaluated on the same x_val data, the fundamental difference between them is how they perceive the images.

1. The CNN: Spatial Vision (2D)
A CNN treats the image as a complete 2D grid of pixels.

Mechanism: It uses mathematical filters (convolutions) that slide across the entire image grid.

Feature Extraction: As it scans, it looks for distinct spatial patterns—edges, corners, loops, and curves.

Why it excels: Handwritten digits are inherently spatial. A CNN can immediately recognize the two loops of an "8" simultaneously, regardless of exactly where they are drawn within the 28x28 frame. This makes it highly efficient and highly accurate for image data.

2. The RNN: Sequential Vision (Time-Series)
An RNN is traditionally designed for sequential data (like text or audio). To process an image, it is forced to treat the 2D grid as a sequence of events over time.

Mechanism: It reads the image row-by-row, from top to bottom (28 time steps, reading 28 pixels per step).

Feature Extraction: It looks at the first row, memorizes the pixels, moves to the second row, updates its internal memory state, and continues downward.

The Challenge: By the time the RNN reaches the bottom of a digit, it must rely entirely on its "memory" of the top rows to piece the complete shape together. While it still achieves high accuracy, it requires heavier computational logic to build a cohesive picture from sequential fragments compared to a CNN.

📈 Evaluation & Expected Outcomes
Both architectures are evaluated using the validation set (x_val). The performance of each model is analyzed using:

Accuracy Metrics: Both models are optimized to achieve an accuracy greater than 95%.

Confusion Matrices: Visual heatmaps are generated for both the CNN and RNN to analyze specific misclassifications (e.g., assessing if a model frequently confuses a poorly drawn "4" with a "9").

🚀 Getting Started
Prerequisites
Python 3.x

TensorFlow / Keras

NumPy

Matplotlib & Seaborn

Scikit-Learn (for Confusion Matrix generation)

Execution
Simply run the main script to load the data, train both models sequentially on the x_train data, and output the validation accuracy alongside the comparative confusion matrices.
