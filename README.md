# 🧪 Random Dataset Generator

A flexible Python utility for generating synthetic datasets with customizable columns, data types, statistical distributions, and dependencies — ideal for data science, machine learning testing, and educational use.

## 🚀 Features

- Generate synthetic datasets with:

  - Numerical, categorical, datetime, boolean, and name data
  - Customizable distributions: Normal, Uniform, Poisson, etc.
  - Dependencies between columns (e.g., linear or logistic relationships)

- Control randomness with seeds
- Locale support for fake data generation via `Faker`

## 📦 Installation

```bash
pip install pandas numpy faker
```

## 🧠 Usage

```python
from main import RandomDatasetGenerator

generator = RandomDatasetGenerator(seed=42)

columns_config = [
    {"name": "age", "type": "int", "distribution": "normal", "params": {"loc": 30, "scale": 5}},
    {"name": "income", "type": "float", "distribution": "lognormal", "params": {"mean": 10, "sigma": 0.5}},
    {"name": "is_employed", "type": "bool", "distribution": "bernoulli", "params": {"p": 0.8}},
    {"name": "job_title", "type": "category", "params": {"categories": ["Engineer", "Artist", "Teacher"]}},
    {"name": "join_date", "type": "datetime", "params": {"start": "2010-01-01", "end": "2022-01-01"}},
    {
        "name": "salary_score",
        "type": "float",
        "depends_on": "income",
        "function_type": "linear",
        "params": {"scale": 0.1, "noise_std": 1.0}
    }
]

df = generator.generate_dataset(n_rows=1000, columns_config=columns_config)
print(df.head())
```

## 🧠 Supported Types

| Data Type   | Supported? | Notes                                     |
| ----------- | ---------- | ----------------------------------------- |
| `int`       | ✅         | With distribution (e.g., normal, poisson) |
| `float`     | ✅         | Multiple distributions supported          |
| `bool`      | ✅         | Via bernoulli or binary binomial          |
| `category`  | ✅         | Custom categories with probabilities      |
| `datetime`  | ✅         | Randomized within a date range            |
| `name`      | ✅         | Fake names using `Faker`                  |
| `dependent` | ✅         | Based on another column via function      |

## 🧹 Column Dependencies

Define relationships between columns using:

- `linear` — simple y = ax + noise
- `logistic` — classification-like relationship (WIP or to be extended)

## ⚙️ Constructor Options

```python
RandomDatasetGenerator(seed: int = None, locale: str = 'en_US')
```

- `seed`: Reproducibility of random results
- `locale`: Faker locale (e.g., `fr_FR`, `en_US`, `ja_JP`)

## 📄 License

MIT License
