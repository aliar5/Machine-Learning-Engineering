Image Classification on Tiny ImageNet  
Author: Ahmedrami Ali

Project Description and Objective
This project applies transfer learning using a ResNet-50 model pretrained on ImageNet to perform image classification on the Tiny ImageNet dataset. The objective is to build a high-performing classifier that can distinguish between 200 classes of low-resolution (64×64) images, simulating real-world constraints such as small image sizes and high inter-class similarity.

Dataset
The dataset used is the **Tiny ImageNet-200** dataset:
- 200 object categories  
- 500 training images and 50 validation images per class  
- 64×64 RGB images  
- Download link: http://cs231n.stanford.edu/tiny-imagenet-200.zip

Model and Method Overview
The model is a modified ResNet-50 architecture with pretrained ImageNet weights. The early layers are frozen to retain general features, while deeper layers (Layer 2 and beyond) are fine-tuned. A dropout layer (p=0.3) and a new fully connected layer are added for regularization and class adaptation. The training loop uses:
- Optimizer: Adam  
- Loss: CrossEntropyLoss with label smoothing  
- Scheduler: Cosine annealing  
- Epochs: 30  
- Batch size: 64  
- Environment: Google Colab (T4 GPU)

How to Run the Code
1. Open the notebook in Google Colab (recommended)
2. Ensure GPU is enabled: Runtime > Change runtime type > Select GPU
3. Run the cells in order from top to bottom
4. The notebook will automatically:
   - Download and prepare Tiny ImageNet
   - Apply augmentations and preprocessing
   - Train and evaluate the model
   - Generate performance plots and visualizations

Summary of Results and Key Findings
- Training Accuracy: 96.9%  
- Validation Accuracy: 52.9%  
- Top-5 Accuracy: 75.9%  
- Validation performance plateaued early, suggesting overfitting  
- Model performed well on visually distinct classes (e.g., goldfish)  
- Struggled with fine-grained classes with visual overlap  
- Future improvements may include full fine-tuning, stronger augmentations (MixUp, Cutout), or custom classifier heads
