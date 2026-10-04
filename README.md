# Shape Sketch Trainer

A complete machine-learning loop in one web page, built with [TensorFlow.js](https://www.tensorflow.org/js).

1. **Make data** – generates 1,800 hand-drawn-style 28×28 images of circles, squares and triangles.
2. **Train** – trains a small convolutional neural network in the browser, with a live accuracy chart.
3. **Use** – draw a shape and the trained model recognizes it with `model.predict()`.

Everything runs locally in your browser. No server and no build step.

## Run it

Open `index.html` in any modern browser, or enable GitHub Pages for this repo
(Settings → Pages → Deploy from branch → `main` / root) to get a live link.

## Model

```
conv2d(8, 3×3, relu) → maxPool(2) → conv2d(16, 3×3, relu) → maxPool(2)
→ flatten → dense(32, relu) → dense(3, softmax)
```

Optimizer: Adam (lr 0.003), loss: categorical cross-entropy, 8 epochs, batch size 32, 15% validation split.
