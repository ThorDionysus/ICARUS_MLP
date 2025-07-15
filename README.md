# ICARUS_MLP

**ICARUS_MLP** is a lightweight RGB-based point cloud classification software with a user-friendly graphical interface. It utilizes a simple multi-layer perceptron (MLP) model implemented in PyTorch to classify `.ply` point cloud files based on their RGB values.

## 🚀 Features

- Classifies point clouds using RGB information only.
- GUI-based: no command-line knowledge required.
- Supports class selection and batch size configuration.
- Outputs per-class `.ply` files for visualization or further processing.

## 📁 Project Structure

```
ICARUS_MLP/
├── MLP-RGB-Software.py             # Main application file (GUI + model)
├── point_cloud_classifier-RGB.pth # Pretrained PyTorch model weights
└── README.md                      # Project documentation
```

## 📦 Requirements

Make sure Python ≥ 3.7 is installed, then install the required packages:

```bash
pip install PyQt5 torch open3d numpy
```

## 💻 Runtime Environment

This project is known to run successfully under the following environment:

- CUDA 12.6
- PyTorch 2.6.0
- Python 3.10+ (recommended)
- IDE: PyCharm (tested)

Other environments may also work, but compatibility is not guaranteed.

## 💡 How to Use

1. Run the application:

```bash
python MLP-RGB-Software.py
```

2. In the GUI:
   - Click "Browse" to select an input `.ply` file with RGB colors.
   - Select an output directory for saving results.
   - Choose which classes to export: `Bunch`, `Leaf`, `Fruit`, `Noise`.
   - Select a batch size.
   - Click `Run Classification` to start.

3. After classification, the output directory will contain `.ply` files named as:

```
<filename>-MLP-RGB-Bunch.ply
<filename>-MLP-RGB-Leaf.ply
<filename>-MLP-RGB-Fruit.ply
<filename>-MLP-RGB-Noise.ply
```

Only selected classes will be exported.

## 🧠 Model Architecture

The MLP classifier is a 2-layer fully connected network:

```python
self.fc1 = nn.Linear(3, 2048)
self.relu = nn.ReLU()
self.fc2 = nn.Linear(2048, 4)
```

- Input: RGB (3 channels)
- Output: 4 classes

| Index | Class  |
|-------|--------|
| 0     | Bunch  |
| 1     | Leaf   |
| 2     | Fruit  |
| 3     | Noise  |

The model is automatically loaded from `point_cloud_classifier-RGB.pth`.

## 🖥️ Platform Compatibility

- OS: Windows / Linux / macOS
- Python ≥ 3.7
- GPU recommended for faster inference (optional)


## 🙋 Feedback & Contributions

If you find bugs, want to suggest improvements, or contribute, I hereby sincerely invite you to submit a pull request.

---
