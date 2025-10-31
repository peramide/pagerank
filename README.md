# 🌐 PageRank AI

A Python program that ranks web pages by importance using **Google’s PageRank algorithm**. It models the behavior of a *random surfer* navigating the web and computes each page’s rank using both **sampling** (Markov chain simulation) and **iterative** methods for convergence-based accuracy.

---

## 🧠 Overview
### Example Output

```
PageRank Results from Sampling (n = 10000)
  1.html: 0.2223
  2.html: 0.4303
  3.html: 0.2145
  4.html: 0.1329
PageRank Results from Iteration
  1.html: 0.2202
  2.html: 0.4289
  3.html: 0.2202
  4.html: 0.1307
```
This project simulates how modern search engines like **Google** evaluate the importance of web pages.
Each page’s rank reflects the probability that a random internet surfer would visit it at any given time — a probabilistic measure of “importance” based on the structure of the web itself.

The program implements two approaches to compute PageRank:

1. **Sampling (Random Surfer Model):**
   Repeatedly samples pages according to a transition model that combines random jumps and link-following (controlled by a damping factor).

2. **Iteration (Mathematical Convergence):**
   Iteratively updates ranks using the recursive PageRank formula until the values stabilize (changes less than 0.001).

---

## ⚙️ Features

* 🔁 **Two PageRank Methods:** Sampling-based estimation and iterative convergence.
* 📊 **Transition Model:** Represents the probability distribution of the next page visited.
* 💡 **Damping Factor:** Implements the classic PageRank balance between random jumps and link traversal.
* 🧩 **Handles Dead Ends:** Correctly treats pages with no outgoing links as linking to all pages.
* ✅ **Accurate Results:** Ranks converge to within ±0.001 tolerance.

---

## 🗂️ Project Structure

| File                                 | Description                                    |
| ------------------------------------ | ---------------------------------------------- |
| **`pagerank.py`**                    | Core implementation of the PageRank algorithm. |
| **`corpus0/`**, **`corpus1/`**, etc. | Example HTML corpora for testing.              |
| **`README.md`**                      | Project documentation (this file).             |

---

## 🚀 How to Run

### Run PageRank on a Corpus

```bash
python pagerank.py corpus0
```

### Example Output

```
PageRank Results from Sampling (n = 10000)
  1.html: 0.2223
  2.html: 0.4303
  3.html: 0.2145
  4.html: 0.1329
PageRank Results from Iteration
  1.html: 0.2202
  2.html: 0.4289
  3.html: 0.2202
  4.html: 0.1307
```

---

## 🧩 How It Works

### 1. Transition Model

Defines the probability of visiting each page next:

* With probability **d**, choose a random link from the current page.
* With probability **1 - d**, choose any page in the corpus at random.

### 2. Sampling PageRank

* Start from a random page.
* Follow the transition model for **n samples** (e.g., 10,000).
* Count how often each page is visited → normalize counts to probabilities.

### 3. Iterative PageRank

* Initialize all pages with rank = 1 / N.

* Repeatedly update each page’s rank using the formula:

  [
  PR(p) = \frac{1-d}{N} + d \sum_{i \in M(p)} \frac{PR(i)}{L(i)}
  ]

  Where:

  * ( d ) = damping factor (usually 0.85)
  * ( N ) = total number of pages
  * ( M(p) ) = set of pages linking to ( p )
  * ( L(i) ) = number of links on page ( i )

* Continue until the change per iteration < 0.001 for all pages.

---

## 📚 Concepts Demonstrated

* Markov Chains and Probability Distributions
* Damping Factor and Random Surfer Model
* Iterative Convergence and Error Thresholds
* Dictionary-based Corpus Representation
* Web Graph Modeling

---

## 🧮 Example

For a corpus:

```
{
  "1.html": {"2.html", "3.html"},
  "2.html": {"3.html"},
  "3.html": {"2.html"}
}
```

At damping = 0.85, the transition model for `1.html` would be:

```
{
  "1.html": 0.05,
  "2.html": 0.475,
  "3.html": 0.475
}
```

---

## 🧠 Insights

This project demonstrates how **AI can quantify web importance mathematically**, forming the foundation of modern search ranking systems.
It highlights the beauty of **recursive probabilistic reasoning** and how simple rules can model complex global behaviors like web navigation.

---

## 🏁 Requirements

* **Python 3.12** (recommended)
* Standard library only (no third-party dependencies required)

---

## 🧾 Acknowledgement

**CS50 Introduction to Artificial Intelligence with Python**nder 350 chars)** for this PageRank project too?
