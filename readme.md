## CIFAR-10 Image Classification (TensorFlow/Keras)

Colab Link:  https://colab.research.google.com/drive/16BAOqvMc0c96hNDAemwPdL4IWyxbsuZ6?usp=sharing

A simple convolutional neural network (CNN) built with TensorFlow/Keras to classify images from the CIFAR-10 dataset. After training, the script also runs predictions on example images in this folder.

### What this project does
- **Dataset**: CIFAR-10 (10 classes: Plane, Car, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck)
- **Model**: A compact CNN with three `Conv2D` blocks, max pooling, and dense layers
- **Training subset**: Uses 20,000 images for training and 4,000 for validation to keep runtime manageable
- **Predictions**: Demonstrates predictions on `horse.jpg` and `plane.jpg` (you can swap in `car.jpg` or `deer.jpg` as well)

### Files
- `main.py`: End-to-end training and inference script
- `car.jpg`, `deer.jpg`, `horse.jpg`, `plane.jpg`: Example images to test predictions

### Run locally
Prereqs: Python 3.9+ (Windows/macOS/Linux)

```bash
pip install --upgrade pip
pip install tensorflow==2.15.0 numpy matplotlib opencv-python
```

Then run the script from this folder:

```bash
python main.py
```

Notes:
- CIFAR-10 uses 32×32 RGB images. If you use your own images, resize them to 32×32 before prediction (or adapt the code to resize automatically).
- Training time depends on your CPU/GPU. The script limits data size to keep runtime reasonable.

### Run in Google Colab
Click the badge at the top or open `https://colab.research.google.com/github/` and do one of the following:
- If this project is on GitHub, paste the repository URL and open `main.py` in Colab
- Or upload `main.py` and the example images to Colab (File → Upload), then run the cells

Optional quick link to a blank notebook: `https://colab.new`

### How the model works (quick overview)
1. Loads CIFAR-10 via Keras and normalizes pixel values to [0, 1]
2. Builds a small CNN: `Conv2D → ReLU → MaxPool` repeated, then `Flatten → Dense → Softmax`
3. Trains with Adam optimizer and `sparse_categorical_crossentropy`
4. Evaluates on a validation split and prints loss/accuracy
5. Reads local test images and prints the predicted class

### Troubleshooting
- If OpenCV (`cv2`) cannot load images, ensure the paths are correct and images exist in this folder
- If you see a shape error at prediction time, ensure test images are 32×32 and RGB


