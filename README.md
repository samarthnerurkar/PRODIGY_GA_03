# 🔗 Markov Chain Text Generator

A from-scratch Python implementation of a Markov chain text generator. It learns word transition probabilities from a small corpus and generates new sentences. No external ML libraries needed.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Colab](https://img.shields.io/badge/Google-Colab-orange)

## ✨ Features

- Configurable model order (default `2`)
- Lowercases text and tokenizes words and punctuation with regex
- Learns transition counts using `defaultdict(Counter)`
- Weighted random sampling of the next token
- Restores readable spacing around punctuation and capitalizes output
- Optional seed text to start generation
- Prints training stats (states learned, vocabulary size)

## 🛠 Tech Stack

- Python standard library only: `re`, `random`, `collections`

## ⚡ Getting Started

1. Open `markovtest.ipynb` in Google Colab (or Jupyter).
2. Run all cells. No GPU or installs required.

## 🚀 Usage

```python
model = MarkovTextGenerator(order=2)
model.train(training_text)

print(model.generate(length=40, seed="machine learning"))
```

## 🧠 How It Works

1. **Preprocess:** lowercase the text and split it into tokens (words and `. , ! ? ;`).
2. **Train:** for every window of `order` tokens (the *state*), count which token follows it.
3. **Generate:** start from a seed state, sample the next token using the learned counts as weights, slide the window, repeat.
4. **Clean up:** join tokens, fix spacing before punctuation, capitalize.

## 🎬 Demo

<img width="902" height="431" alt="image" src="https://github.com/user-attachments/assets/427200fd-deec-472e-aaca-56af9fb820c4" />

## 🔄 Workflow

<img width="1850" height="490" alt="image" src="https://github.com/user-attachments/assets/4ed0936c-2c4e-40d6-8ebc-75a997f82024" />


## ⚠️ Notes

- Training text must be longer than the model order, otherwise a `ValueError` is raised.
- With a tiny corpus the output repeats phrases from the training data. Use a larger corpus for more variety.
- Higher `order` gives more coherent text but less novelty.

## 📄 License

MIT License

## 👤 Author

**Samarth Nerurkar**

- GitHub: [@samarthnerurkar](https://github.com/samarthnerurkar)
- LinkedIn: [Samarth Nerurkar](https://www.linkedin.com/in/samarth-nerurkar/)
