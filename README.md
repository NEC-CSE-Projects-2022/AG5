
# AG5 – A Hybrid Deep Learning Strategy for Real-Time Assembly Task Recognition Based on Hand Joint Trajectories

## Team Info
- 22471A0544— **Patibandla Prasanthi** ( (https://www.linkedin.com/in/prasanthi-patibandla-997b8036a?utm_source=share_via&utm_content=profile&utm_medium=member_android) )
_Work Done: Backend_

- 22471A05XX — **Katekeni Hemanthini** ( (https://www.linkedin.com/in/katikeni-hemanthini-826395301?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app) )
_Work Done: Frontend_

- 22471A0523 — **Gopu Pavani** ( (https://www.linkedin.com/in/gopu-pavani-084518374?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app ))
_Work Done: PPTs and documents_

## Abstract
In the era of Industry 4.0, real-time monitoring of manual assembly tasks plays a crucial role in improving operator efficiency, ensuring process compliance, and maintaining product quality. This paper presents a hybrid deep learning framework for real-time assembly task recognition based on hand joint trajectories. The proposed system processes video data from a physical workstation using YOLOv8 for accurate object detection and MediaPipe Hands for extracting 3D hand-joint landmarks. Temporal patterns in the hand movements are captured using Long Short-Term Memory (LSTM) and Bidirectional LSTM (BiLSTM) models, enhanced with velocity-based features. A comprehensive preprocessing pipeline, including frame extraction, grayscale conversion, resizing, hand tracking, masking, normalization, and sequence padding, ensures robust performance across variable-length tasks. The system was evaluated on seven distinct assembly operations and achieved an accuracy of 93%, outperforming traditional single-modality approaches and the baseline HATREC framework. The proposed approach is lightweight and suitable for real-time deployment, providing intelligent feedback and reducing errors in industrial environments. This work contributes to the advancement of smart manufacturing systems by integrating object detection and motion-based action recognition for efficient human–machine collaboration.


---

## Paper Reference (Inspiration)
👉 **## Paper Reference (Inspiration)

👉 **HybridAssemblyNet: A Framework for Real-Time Assembly Task Recognition
– L. Wu and X. Ma (2024)
https://arxiv.org/abs/2403.09056**

This paper served as a key inspiration for our proposed system. It presents a hybrid approach combining object detection and skeletal hand tracking for recognizing assembly actions in industrial environments. The integration of deep learning techniques for both spatial (object-level) and temporal (motion-level) analysis influenced the design of our framework. Building upon this concept, our work extends the approach by incorporating YOLOv8, MediaPipe Hands, and BiLSTM models along with enhanced preprocessing techniques to improve recognition accuracy and real-time performance.

Original conference/IEEE paper used as inspiration for the model.

---

## Our Improvement Over Existing Paper
The proposed system significantly enhances the performance and robustness of the existing HATREC-based assembly task recognition framework through several key improvements.

Firstly, we upgraded the object detection component by replacing earlier YOLO variants with YOLOv8, which provides higher detection accuracy, faster inference, and better performance in complex industrial environments. This enables more reliable identification of tools and components during assembly operations.

Secondly, we improved the motion analysis by incorporating velocity-based features derived from hand-joint trajectories. Unlike the existing approach that relies only on positional data, our method captures both spatial and dynamic aspects of hand movements, leading to better discrimination of similar tasks.

Thirdly, we adopted a Bidirectional LSTM (BiLSTM) model in addition to the standard LSTM. The BiLSTM processes sequential data in both forward and backward directions, allowing the model to capture richer temporal dependencies and subtle variations in hand gestures, thereby improving classification accuracy.

Furthermore, we introduced a more comprehensive data preprocessing pipeline, including frame extraction, grayscale conversion, resizing, masking, normalization, and sequence padding. These steps ensure consistency across variable-length sequences and improve model generalization.

To enhance reliability, we applied K-fold cross-validation, which provides a more robust evaluation compared to a simple train-test split and reduces the risk of biased performance estimates.

As a result of these improvements, our system achieved an accuracy of 93%, outperforming the original HATREC framework (86–89%) and demonstrating better performance in real-time assembly task recognition scenarios. Additionally, the proposed model remains lightweight and suitable for deployment in real-world industrial settings.

Overall, our work advances the existing approach by integrating improved object detection, enhanced feature engineering, and advanced temporal modeling to achieve higher accuracy and robustness.

## About the Project


### What the Project Does

This project develops a smart system that can recognize different manual assembly tasks in real time using video input. It observes the worker’s hand movements and the tools being used, then automatically identifies which task is being performed. The system uses deep learning techniques to analyze both hand motion and object interaction.

---

### Why It is Useful

In modern industries, many assembly tasks are still done manually, which can lead to errors and reduced efficiency. This project helps by:

* Monitoring worker activities automatically
* Detecting mistakes or incorrect steps early
* Improving productivity and quality
* Providing real-time feedback in manufacturing environments

It supports the goals of Industry 4.0 by enabling smarter and more efficient production systems.

---

### General Project Workflow

**Input → Processing → Model → Output**

1. **Input:**
   Video is captured from a camera placed at the assembly workstation.

2. **Processing:**

   * Frames are extracted from the video
   * Images are resized and converted to grayscale
   * Hand joints are detected using MediaPipe
   * Objects/tools are detected using YOLOv8

3. **Model:**

   * Hand movement data (trajectories) is given to LSTM/BiLSTM models
   * The model learns patterns of different assembly tasks

4. **Output:**

   * The system predicts the current task being performed
   * Displays results in real time
   * Can help identify errors or track progress

---

Overall, the project combines computer vision and deep learning to create an intelligent system for real-time assembly task recognition.


## Dataset Used
👉 **[Dataset Name](Dataset URL)**

**Dataset Details:**


The dataset used in this project consists of video recordings captured from a real-time manual assembly workstation. The data was collected to represent typical industrial assembly scenarios under varying conditions.

### Dataset Description

* The dataset includes **seven different assembly tasks**, such as assembling components, screwing, cable fixing, and part placement.
* Multiple video samples were recorded for each task to ensure diversity in execution styles and conditions.
* Videos were captured under **different lighting conditions and operator variations** to improve model robustness.

### Data Format

* The input data is in the form of **video sequences**.
* Each video is converted into frames during preprocessing.
* Frames are resized to **224 × 224 pixels** and converted to grayscale for efficient processing.

### Feature Extraction

* **Hand joint landmarks:** Extracted using MediaPipe Hands (21 key points per hand, resulting in 63 features per frame).
* **Object detection:** Performed using YOLOv8 to identify tools and components involved in tasks.
* **Temporal data:** Sequences of hand movements are formed across frames to capture motion patterns.

### Sequence Preparation

* All video sequences are standardized to a fixed length of **219 frames** using padding techniques.
* Missing hand detections are handled by inserting zero values to maintain consistency.

### Data Splitting and Validation

* The dataset is divided into **training and validation sets**.
* **K-fold cross-validation** is used to ensure reliable and unbiased performance evaluation.

### Purpose of the Dataset

The dataset is designed to help the model learn both:

* **Spatial features** (objects/tools used in tasks)
* **Temporal features** (hand movement patterns over time)

This combination enables accurate recognition of assembly tasks in real-time industrial environments.


---

## Dependencies Used


The implementation of the proposed system relies on several software libraries and frameworks for data processing, computer vision, and deep learning.

### Programming Language

* **Python** – Used as the primary programming language for implementing the entire system.

### Deep Learning Frameworks

* **TensorFlow / Keras** – Used for building and training LSTM and BiLSTM models.
* **PyTorch** (optional, if used with YOLOv8) – Supports model training and inference.

### Computer Vision Libraries

* **OpenCV** – Used for video capture, frame extraction, image processing, and visualization.
* **MediaPipe** – Used for real-time hand tracking and extraction of 3D hand-joint landmarks.

### Object Detection

* **YOLOv8 (Ultralytics)** – Used for detecting tools and components in assembly tasks with high accuracy and speed.

### Data Processing and Analysis

* **NumPy** – Used for numerical computations and handling arrays.
* **Pandas** – Used for organizing and managing dataset information.

### Visualization Tools

* **Matplotlib** – Used for plotting graphs such as accuracy and loss curves.
* **Seaborn** – Used for visualizing confusion matrices and statistical plots.

### Development Environment

* **Google Colab / Jupyter Notebook** – Used for model development, training, and experimentation.



These dependencies collectively enable efficient preprocessing, feature extraction, model training, and real-time prediction for assembly task recognition.




## EDA & Preprocessing

### Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to understand the structure and characteristics of the dataset before training the model.

* **Task Distribution:**
  The dataset contains seven different assembly tasks. The distribution of samples across tasks was analyzed to check for class imbalance.

* **Video Analysis:**
  Each video was examined to observe variations in:

  * Lighting conditions
  * Operator hand movements
  * Background and object placement

* **Frame Inspection:**
  Sample frames were visualized to verify:

  * Clarity of hand movements
  * Visibility of tools and components
  * Consistency in camera angle

* **Hand Detection Check:**
  MediaPipe Hands outputs were reviewed to ensure accurate detection of hand landmarks across frames.

* **Outlier Identification:**
  Videos with missing frames, poor lighting, or incorrect labeling were identified and handled appropriately.

---

### Data Preprocessing

To prepare the data for model training, several preprocessing steps were applied:

1. **Frame Extraction:**
   Videos were converted into individual frames at a fixed sampling rate.

2. **Image Resizing:**
   All frames were resized to **224 × 224 pixels** to maintain uniform input size.

3. **Grayscale Conversion:**
   Frames were converted to grayscale to reduce computational complexity while preserving essential features.

4. **Hand Landmark Extraction:**
   MediaPipe Hands was used to extract **21 key points per hand**, generating a **63-dimensional feature vector** (x, y, z coordinates).

5. **Handling Missing Data:**
   Frames where hand detection failed were replaced with zero vectors to maintain sequence consistency.

6. **Sequence Padding:**
   All sequences were standardized to **219 frames** using padding to handle variable-length videos.

7. **Normalization:**
   Feature values were normalized to ensure stable and faster model training.

8. **Feature Engineering:**
   Velocity-based features were computed from hand joint movements to capture motion dynamics.

9. **Data Splitting:**
   The dataset was divided into training and validation sets, and **K-fold cross-validation** was applied for robust evaluation.

---

Overall, EDA and preprocessing ensured clean, consistent, and meaningful input data, which significantly improved the performance and reliability of the deep learning models.


## Model Training Info

### Model Architecture

The proposed system uses deep learning models designed for sequential data analysis:

* **LSTM (Long Short-Term Memory):**
  Used to capture temporal dependencies in hand-joint trajectories.

* **BiLSTM (Bidirectional LSTM):**
  An advanced version of LSTM that processes sequences in both forward and backward directions, enabling better understanding of motion patterns and improving classification accuracy.

* A **Dense (Fully Connected) layer** with Softmax activation is used at the output for multi-class classification of assembly tasks.

---

### Input to the Model

* Input data consists of **time-series sequences of hand-joint features**.
* Each sequence contains:

  * **219 frames (time steps)**
  * **63 features per frame** (21 hand joints × 3 coordinates)

---

### Training Configuration

* **Optimizer:** Adam
* **Loss Function:** Categorical Cross-Entropy
* **Evaluation Metric:** Accuracy
* **Batch Size:** 16 / 32 (based on system capability)
* **Number of Epochs:** 50–100
* **Validation Strategy:** K-Fold Cross-Validation

---

### Regularization Techniques

To prevent overfitting and improve generalization:

* **Dropout layers** were added between LSTM/BiLSTM layers
* Early stopping can be applied based on validation loss
* Data normalization was performed before training

---

### Training Process

* The model was trained on preprocessed sequences of hand-joint data.
* During training, the model learned patterns of different assembly tasks based on temporal movement.
* Performance was monitored using training and validation accuracy and loss curves.

---

### Final Model Selection

* Both LSTM and BiLSTM models were evaluated.
* The **BiLSTM model** showed better performance due to its ability to capture bidirectional temporal dependencies.
* The final selected model achieved an accuracy of **93%**, outperforming the baseline HATREC model.

---

Overall, the training process focused on learning meaningful temporal patterns from hand movements to accurately classify assembly tasks in real time.

## Model Testing / Evaluation

### Evaluation Approach

After training, the model was evaluated using unseen validation data to measure its ability to generalize to new assembly task sequences. A **K-Fold Cross-Validation** strategy was used to ensure reliable and unbiased performance assessment.

---

### Evaluation Metrics

The following metrics were used to evaluate model performance:

* **Accuracy:**
  Measures the overall percentage of correctly predicted tasks.

* **Precision:**
  Indicates how many predicted tasks are actually correct.

* **Recall:**
  Measures the model’s ability to correctly identify all instances of a task.

* **F1-Score:**
  Provides a balance between precision and recall.

* **Confusion Matrix:**
  Visualizes correct and incorrect predictions for each task class.

---

### Testing Results

* The **BiLSTM model achieved an overall accuracy of 93%**, outperforming the baseline HATREC model.
* Most assembly tasks were classified correctly, with strong performance in tasks like *Inflate Valve* and *Screwing-2*.
* Some misclassifications occurred between similar tasks such as *Screwing-1* and *Place White Part*.

---

### Performance Analysis

* The confusion matrix showed high values along the diagonal, indicating correct predictions.

* Per-class evaluation revealed:

  * High precision for *Place Black Part*
  * Lower recall for *Fix Cable*, indicating difficulty in detecting this task

* Training accuracy was higher than validation accuracy, indicating slight overfitting, which can be improved with additional data or regularization.

---

### Real-Time Evaluation

* The system was also tested in a real-time environment using live or recorded video input.
* The predicted task sequence was compared with manually labeled (human) data.
* Results showed strong alignment with actual task timing and classification, confirming the system’s practical usability.

---

### Conclusion of Evaluation

The evaluation results demonstrate that the proposed hybrid model is:

* Accurate and reliable for task recognition
* Capable of handling real-time industrial scenarios
* An improvement over existing methods

Overall, the model performs effectively in recognizing assembly tasks and supports intelligent monitoring in Industry 4.0 environments.


## Results

The proposed hybrid deep learning model was evaluated on a dataset consisting of seven different assembly tasks. The results demonstrate the effectiveness of combining object detection, hand-joint tracking, and temporal modeling for real-time task recognition.

### Overall Performance

* The **BiLSTM model achieved an accuracy of 93%**, outperforming:

  * **HATREC baseline:** 86–89%
  * **Standard LSTM model:** ~90%

This confirms that bidirectional temporal modeling significantly improves task recognition performance.

---

### Training and Validation Performance

* The training accuracy steadily increased and approached high values, indicating effective learning of task patterns.
* Validation accuracy remained stable around **92–93%**, showing good generalization.
* A slight gap between training and validation performance suggests minor overfitting.

---

### Confusion Matrix Analysis

* Most predictions were correctly classified, as shown by strong diagonal values in the confusion matrix.
* The model performed well in tasks such as:

  * *Inflate Valve*
  * *Screwing-2*
* Some confusion occurred between similar tasks like:

  * *Screwing-1* and *Place White Part*

---

### Class-wise Performance

* High precision and recall were observed for most tasks.
* Best performance:

  * *Place Black Part* (high precision)
  * *Screwing-2* (balanced precision and recall)
* Lower performance:

  * *Fix Cable* (low recall due to similarity with other tasks)

---

### Real-Time Performance

* The system successfully recognized tasks in real time using video input.
* Predicted task sequences closely matched human-labeled data.
* The model maintained consistent performance even under slight variations in lighting and hand movements.

---

### Comparative Results

| Model      | Accuracy (%) |
| ---------- | ------------ |
| HATREC     | 86–89        |
| LSTM       | 90.1         |
| **BiLSTM** | **93.0**     |

---

### Summary

The results clearly show that the proposed system:

* Improves accuracy over existing methods
* Effectively handles real-time task recognition
* Provides reliable performance across different assembly operations

Overall, the model demonstrates strong potential for deployment in smart manufacturing environments.

## Limitations & Future Work

### Limitations

Despite achieving strong performance, the proposed system has certain limitations:

* **Limited Dataset Size:**
  The dataset consists of a limited number of samples for each task, which may restrict the model’s ability to generalize to completely new environments or operators.

* **Class Confusion in Similar Tasks:**
  The model sometimes misclassifies tasks with similar hand movements (e.g., different screwing or placement actions), due to subtle differences in motion patterns.

* **Overfitting Issue:**
  A gap between training and validation accuracy indicates slight overfitting, which may affect performance on unseen data.

* **Dependence on Hand Detection:**
  The system relies heavily on accurate hand landmark detection. Any failure in hand tracking (due to occlusion or poor lighting) can impact overall performance.

* **Single-Camera Setup:**
  The current system uses a single camera, which may limit performance in complex environments with occlusions or multiple workers.

---

### Future Work

To further enhance the system, the following improvements can be considered:

* **Increase Dataset Size:**
  Collect more diverse data with different operators, environments, and task variations to improve model generalization.

* **Advanced Models:**
  Incorporate attention mechanisms or Transformer-based models to better capture complex temporal dependencies.

* **Multi-Camera Integration:**
  Use multiple camera views to handle occlusions and improve tracking accuracy in real-world industrial settings.

* **Real-Time Feedback System:**
  Develop a user interface to provide instant feedback or alerts to workers during task execution.

* **Model Optimization:**
  Optimize the model for deployment on edge devices to enable faster and more efficient real-time performance.

* **Improved Feature Engineering:**
  Explore additional features such as force estimation or tool usage patterns to better distinguish similar tasks.

---

Overall, while the proposed system demonstrates strong performance, addressing these limitations can further improve its accuracy, scalability, and real-world applicability in smart manufacturing environments.

## Deployment Info

### Deployment Environment

The proposed system is designed for deployment in real-time industrial environments, particularly at manual assembly workstations. It can run on standard computing systems with moderate GPU/CPU capabilities.

---

### Hardware Requirements

* **Camera:**
  A high-resolution webcam or industrial camera to capture live video from the workstation.

* **Processing Unit:**

  * CPU: Intel i5/i7 or equivalent
  * GPU (optional but recommended): NVIDIA GPU for faster inference

* **Memory:**
  Minimum 8 GB RAM (16 GB recommended for smooth performance)

---

### Software Requirements

* **Operating System:** Windows / Linux
* **Programming Language:** Python
* **Libraries:** TensorFlow/Keras, OpenCV, MediaPipe, YOLOv8 (Ultralytics), NumPy, Pandas

---

### Deployment Workflow

1. **Video Input:**
   Live video is captured from the camera placed at the assembly station.

2. **Preprocessing:**
   Frames are extracted, resized, and processed in real time.

3. **Feature Extraction:**

   * Hand landmarks are extracted using MediaPipe
   * Objects/tools are detected using YOLOv8

4. **Model Inference:**
   The trained BiLSTM model processes hand-joint sequences and predicts the current task.

5. **Output Display:**

   * Predicted task is displayed on screen
   * Can be integrated with alert systems for error detection

---

### Deployment Type

* **Local Deployment:**
  The system runs on a local machine connected to the camera for real-time processing.

* **Edge Deployment (Future Scope):**
  The model can be optimized for deployment on edge devices for faster and low-latency performance.

---

### Performance in Deployment

* The system operates in **real time** with minimal delay.
* Provides accurate task recognition (~93% accuracy).
* Handles moderate variations in lighting and operator behavior.

---

### Applications

* Smart manufacturing and Industry 4.0 systems
* Assembly line monitoring
* Worker assistance and training
* Error detection and quality control

---

Overall, the system is lightweight, efficient, and suitable for real-time deployment in industrial environments, enabling intelligent monitoring and improved productivity.
