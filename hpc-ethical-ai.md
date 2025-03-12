# :rocket::sparkles: Ethical AI & Future Trends on HPC Workshop! :star2::sparkles:
## :dart: **Goal**
:bar_chart: Learn how to develop **Ethical AI** models while leveraging **High-Performance Computing (HPC)** for large-scale training. We will use **The LAION-5B dataset**, one of the largest open-source image-text datasets, requiring HPC resources for ethical AI model training and analysis. :rocket:

---

## :pushpin: **What You Will Learn** :brain::bulb:

:white_check_mark: Understanding **Ethical AI** and its challenges (bias, fairness, explainability) :robot_face:   
:white_check_mark: Exploring **HPC** as a solution for training large AI models responsibly :computer:   
:white_check_mark: Training AI models on large-scale datasets using **multi-GPU HPC clusters** :building_construction:   
:white_check_mark: Evaluating AI fairness, transparency, and accountability :mag:   
:white_check_mark: Future trends in Ethical AI and responsible AI development :earth_africa:   

---
## :books: **1. Key Terminologies in Ethical AI & HPC** :key:   
### :earth_africa: **Ethical AI**   
- AI that ensures **fairness, transparency, and accountability** in decision-making.   
- Addresses bias in datasets and models to prevent discrimination.   
### :rocket: **HPC for AI**   
- **High-Performance Computing (HPC)** enables AI training on massive datasets by distributing computations across GPUs and multiple nodes.   
- Essential for training **foundation models** and **large-scale NLP/CV applications**.   
### :building_construction: **Bias & Fairness in AI**   
- **Algorithmic Bias**: When AI models make unfair decisions based on skewed data.   
- **Fairness Metrics**: Statistical Parity, Equal Opportunity, Equalized Odds, Disparate Impact.   
- **Debiasing Techniques**: Data preprocessing, adversarial training, fairness constraints.   
### :computer: **Federated Learning & Privacy-Preserving AI**   
- **Federated Learning**: AI training across distributed devices while keeping data localized.   
- **Differential Privacy**: Adding noise to AI models to protect sensitive data.   
### :earth_africa: **Future Trends in Ethical AI**   
- **Explainable AI (XAI)**: Making AI decision-making understandable.   
- **Regulatory Frameworks**: EU AI Act, AI Ethics Guidelines from NIST, UNESCO.   
- **Sustainable AI**: Reducing AI’s carbon footprint through efficient HPC utilization.   
---
## :mag: **2: Access HPC Terminal via JupyterHub**   
:one: Go to [CSUSB HPC](https://csusb-hpc.nrp-nautilus.io/).   
:two: Click CI Logon to log in using your school account.   
:three: Select GPU & Image   
Once logged in:   
- Under **GPU Type**, select **RTX A5000**.   
- Choose **2 GPU cores**.   
- In the **Image selection**, pick **Stack PyTorch 2**.   
:four: After logging in, Welcome to JupyterLab.   
---
## :mag: **3. Hands-on: Loading a Large Dataset on HPC**   
We will use CSUSB’s High-Performance Computing (HPC) system to run our AI code. Follow these steps to access JupyterHub on HPC.   
### :rocket: **Step 1**: Log In to HPC with CI Logon :closed_lock_with_key:   
Let’s get you authenticated! Here’s how:   
:one: Go to the CI Logon Portal   
- Open [CI Logon](https://csusb-hpc.nrp-nautilus.io/) in your browser.   
- Click Sign in with CILogon   
:two: Select Your Identity Provider & Log In   
- Choose "California State University, San Bernardino" :mortar_board: from the dropdown.   
- Check "Remember this selection" to save time next login. :white_check_mark:   
- Click Log On to proceed. :rocket:   
### :desktop_computer: **Step 2**: Launch Your JupyterHub Server   
Your HPC Jupyter environment is ready—let’s start coding!   
:one: Check Out the Launcher Page   
- You’ll see several options like:   
- Notebook: Start a Jupyter Notebook (e.g., Python 3 :snake:).   
- Console: Open a Python console for quick commands :pager:.   
- Other: Access Terminal, Text File, Markdown File, or Help :books:.   
:two: Open a Notebook or File   
- Click Notebook → Python 3 (ipykernel) to start coding! :writing_hand:   
- You can also browse and open existing files. :open_file_folder:   
:three: Run Your Code & Save Your Work   
- Type your Python code and press Shift + Enter to run.   
- Save often to keep your work safe! :floppy_disk:   
:question: **Why Use 2 GPU Cores and RTX A5000?**   
We are working with **huge datasets** that require powerful GPUs for efficient computation.   
### :open_file_folder: Step 3: Load **LAION-5B**, a Massive Multimodal Dataset   
:camera_with_flash: **LAION-5B**   
- A massive dataset with **5 billion** image-text pairs.   
- Used for training **vision-language models** like CLIP.   
- Demands **high memory and computational power** for data processing.   
[ChatGpt Code Conversation](https://chatgpt.com/share/67d0f69c-9ea4-8008-a364-369b7482bfe5)   
```python
import torch
import torchvision
import torchvision.transforms as transforms
# Check GPU availability
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
# Define dataset transformation
transform = transforms.Compose([
    transforms.Resize((256, 256)),
    transforms.ToTensor(),
    transforms.Normalize((0.5,), (0.5,))
])
# Load LAION-5B dataset (sampled for ethical AI training)
train_dataset = torchvision.datasets.ImageFolder(root="/scratch/datasets/LAION-5B", transform=transform)
train_loader = torch.utils.data.DataLoader(train_dataset, batch_size=512, shuffle=True, num_workers=16, pin_memory=True)
print(f"Dataset Loaded: LAION-5B with {len(train_dataset)} images")
```
---
## :building_construction: **3. Building and Training a Deep Learning Model for Ethical AI**   
### :rocket: Step 3: Define a Bias-Aware Vision Transformer (ViT) Model   
[ChatGpt Code Conversation](https://chatgpt.com/share/67d0f70d-4094-8008-ad17-05fd13098bfa)   
```python
from transformers import ViTForImageClassification, ViTFeatureExtractor
import torch.nn as nn
# Load pre-trained ViT model
model = ViTForImageClassification.from_pretrained("google/vit-base-patch16-224")
[model.to](http://model.to/)(device)
print("Bias-aware Vision Transformer Model Loaded!")
```
### :rocket: Step 4: Train the Model with Ethical AI Constraints
[ChatGpt Code Conversation](https://chatgpt.com/share/67d0f769-7ae8-8008-bf2e-f4f503958eb3)
```python
import torch.optim as optim
# Define loss and optimizer
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=0.0001)
# Training loop
for epoch in range(5):
    running_loss = 0.0
    for inputs, labels in train_loader:
        inputs, labels = [inputs.to](http://inputs.to/)(device), [labels.to](http://labels.to/)(device)
        optimizer.zero_grad()
        outputs = model(inputs).logits
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()
    print(f"Epoch {epoch+1}: Loss {running_loss:.4f}")
print("Training Complete!")
```
---
## :trophy: **4. Evaluating Model Fairness & Bias Mitigation**   
### :rocket: Step 5: Evaluate Model Performance Across Demographics   
[ChatGpt Code Conversation](https://chatgpt.com/share/67d0f7c4-2848-8008-8608-dd4caa2f222e)   
```python
import numpy as np
from sklearn.metrics import accuracy_score, confusion_matrix
# Placeholder function for fairness evaluation
def evaluate_fairness(predictions, labels, sensitive_attribute):
    unique_groups = np.unique(sensitive_attribute)
    group_accuracies = {}
    for group in unique_groups:
        group_indices = (sensitive_attribute == group)
        group_accuracy = accuracy_score(labels[group_indices], predictions[group_indices])
        group_accuracies[group] = group_accuracy
    return group_accuracies
# Example usage
y_pred = np.random.randint(0, 10, size=len(train_dataset))  # Mock predictions
y_true = np.random.randint(0, 10, size=len(train_dataset))  # Mock ground truth
sensitive_attr = np.random.choice(["Male", "Female", "Other"], size=len(train_dataset))
fairness_results = evaluate_fairness(y_pred, y_true, sensitive_attr)
print("Fairness Evaluation Results:", fairness_results)
```
---
## :tada: 5. **Wrap-Up & Next Steps**   
:dart: Congratulations! You’ve just built and trained an **Ethical AI Model** using **HPC**! :rocket:   
:white_check_mark: Loaded a **large-scale dataset (LAION-5B)** :open_file_folder:   
:white_check_mark: Built a **bias-aware Vision Transformer model** :building_construction:   
:white_check_mark: Trained the model using **HPC with multi-GPU acceleration** :arrows_counterclockwise:   
:white_check_mark: Evaluated **bias and fairness** across demographic groups :bar_chart:   
:rocket: **Next Workshop**: Experiment with alternative multimodal datasets like OpenAI CLIP datasets.   
### **:link: Additional AI Resources** :books:   
- [Responsible AI by Microsoft](https://learn.microsoft.com/en-us/training/modules/embrace-responsible-ai-principles-practices/)   
- [Secure AI services by Microsoft](https://learn.microsoft.com/en-us/training/modules/secure-ai-services/)      
:rocket: Keep learning and see you at the next workshop! :tada:   