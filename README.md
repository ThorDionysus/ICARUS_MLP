# ICARUS_MLP

**ICARUS_MLP** is a lightweight RGB-based point cloud classification tool with a graphical user interface. It uses a simple PyTorch-based multi-layer perceptron (MLP) model to classify `.ply` point clouds based on their RGB color values.

## 🚀 Features

- Classifies `.ply` point clouds using RGB color features only.
- GUI-based: easy to use, no coding or terminal required.
- Supports selective class output (e.g., Leaf, Fruit).
- Fast batch inference using GPU acceleration (if available).
- Outputs categorized `.ply` files for each class.

## 📁 Files Included

```
ICARUS_MLP/
├── ICARUS_MLP.exe                  # Standalone executable (Windows only)
├── point_cloud_classifier-RGB.pth # Pretrained PyTorch model weights
└── README.md                      # Project documentation
```

## 💻 Runtime Environment

- **Recommended:**
  - A computer with **NVIDIA GPU** and **CUDA toolkit** installed
  - CUDA 12.6 and PyTorch 2.6.0 tested
- **Operating System:** Windows 10/11 (64-bit)
- **Note:** The program can run on CPU-only systems, but performance will be significantly slower.


## 💡 How to Use

1. Double-click `ICARUS_MLP.exe` to launch the application.

2. In the GUI:

   - **Input File:** Click "Browse" to load a `.ply` point cloud file with RGB color.
   - **Output Folder:** Choose a directory to save the classification results.
   - **Select Classes:** Enable or disable export for each class (Bunch, Leaf, Fruit, Noise).
   - **Batch Size:** Choose batch size depending on your GPU memory.
   - Click **Run Classification** to start.

3. After classification, output `.ply` files will be saved like this:

```
your_input_filename-MLP-RGB-Leaf.ply
your_input_filename-MLP-RGB-Fruit.ply
...
```

## 🧠 Model Architecture

The built-in classifier is a simple 2-layer MLP:

```python
self.fc1 = nn.Linear(3, 2048)
self.relu = nn.ReLU()
self.fc2 = nn.Linear(2048, 4)
```

- Input: RGB (3 channels per point)
- Output: 4 predicted classes

| Index | Class  |
|-------|--------|
| 0     | Bunch  |
| 1     | Leaf   |
| 2     | Fruit  |
| 3     | Noise  |



## 🙋 Feedback

If you find bugs, want to suggest improvements, or contribute, I hereby sincerely invite you to submit a pull request.

---

