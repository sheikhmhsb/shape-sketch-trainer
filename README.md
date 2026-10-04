# Shape Sketch Trainer & Tiny Chatbot Trainer

Two machine-learning demos built with [TensorFlow.js](https://www.tensorflow.org/js). Each one shows the full loop in a single web page: make training data, train a neural network in the browser, then use the trained model.

Everything runs locally in your browser. No server and no build step.

## The demos

### Shape Sketch Trainer (`index.html`)

An image model.

1. **Make data** – generates 1,800 hand-drawn-style 28×28 images of circles, squares and triangles.
2. **Train** – trains a small convolutional neural network, with a live accuracy chart.
3. **Use** – draw a shape and the trained model recognizes it with `model.predict()`.

```
conv2d(8, 3×3, relu) → maxPool(2) → conv2d(16, 3×3, relu) → maxPool(2)
→ flatten → dense(32, relu) → dense(3, softmax)
```

Adam (lr 0.003), categorical cross-entropy, 8 epochs, batch size 32, 15% validation split.

### Tiny Chatbot Trainer (`chatbot.html`)

A text model that replies to your messages using intent classification.

1. **Write examples** – each topic (intent) has example messages and replies, in an editable text box.
2. **Train** – messages become bag-of-words vectors (1 for each vocabulary word present), and a small network learns which words point to which topic.
3. **Chat** – the bot picks the most likely topic and replies. Below 45% confidence it says it isn't sure. Click "why?" to see which words it recognized and how it scored each topic.

```
dense(24, relu) → dropout(0.3) → dense(topics, softmax)
```

Adam (lr 0.01), categorical cross-entropy, 120 epochs, batch size 16.

Training data format:

```
## greeting
hi
hello there
> Hello! How can I help?
```

The model recognizes what kind of message you sent and picks a written reply. It does not generate new sentences like a large language model.

## Run it

Open `index.html` or `chatbot.html` in any modern browser, or enable GitHub Pages for this repo
(Settings → Pages → Deploy from branch → `main` / root) to get a live link.
