# Random Dataset Generator

A flexible Python library to generate realistic synthetic datasets for testing, development, and demonstration purposes. Supports both statistical and real-world data types using NumPy and Faker.

---

## Features

- 🎲 Wide range of statistical distributions
- 🧍 Realistic personal, internet, company, and location data using Faker
- 📅 Flexible datetime and identifier generation
- 📊 Output as Pandas DataFrames
- 🛠️ Customizable column definitions with parameters, distributions, and choice constraints

---

## Installation

```bash
pip install faker pandas numpy
```

---

## Quickstart Example

```python
from random_dataset_generator import RandomDatasetGenerator

gen = RandomDatasetGenerator()

schema = {
    "name": {"type": "name"},
    "age": {"type": "age", "params": {"min": 18, "max": 70}},
    "email": {"type": "email"},
    "signup_date": {"type": "datetime", "params": {"start_date": "-2y", "end_date": "now"}},
    "income": {"type": "float", "distribution": "lognormal", "params": {"mean": 10, "sigma": 1}}
}

df = gen.generate(schema, n_rows=100)
print(df.head())
```

---

## Supported Distributions

```python
self.distributions = {
    "normal": np.random.normal,
    "uniform": np.random.uniform,
    "poisson": np.random.poisson,
    "exponential": np.random.exponential,
    "binomial": np.random.binomial,
    "bernoulli": lambda p, size: np.random.binomial(1, p, size),
    "lognormal": np.random.lognormal,
    "pareto": np.random.pareto,
    "geometric": np.random.geometric,
    "gamma": np.random.gamma,
    "beta": np.random.beta,
    "weibull": np.random.weibull,
    "chisquare": np.random.chisquare,
    "rayleigh": np.random.rayleigh,
    "zipf": np.random.zipf
}
```

---

## Supported Data Types

### Personal Information

- name
- first_name
- last_name
- prefix
- suffix
- gender
- age
- birthdate
- ssn

### Internet

- email
- username
- password
- domain
- url
- ipv4
- ipv6
- mac_address
- user_agent

### Location

- address
- street_address
- city
- state
- state_abbr
- zipcode
- country
- country_code
- latitude
- longitude
- coordinates

### Phone

- phone_number
- msisdn
- international_phone

### Company

- company
- company_suffix
- job
- industry

### Financial

- credit_card_number
- credit_card_provider
- credit_card_expire
- credit_card_security_code
- currency_code
- currency_name

### Text

- text
- paragraph
- sentence
- word

### Colors

- color_name,
- hex_color
- rgb_color

### Identifiers

- uuid4
- isbn10
- isbn13
- ean8
- ean13

### Dates and Time

- date
- time
- day_of_week
- month_name
- timezone

### Files & Misc

- file_path
- file_name
- mime_type
- image_url
- user_name
- emoji

### Numeric/Statistical

- integer
- float
- boolean
- category
- datetime
- custom

---

## Schema Definition

Each column definition accepts:

- `type`: One of the supported data types
- `distribution`: (optional) One of the statistical distributions
- `params`: (optional) Parameters for the distribution or faker method
- `choices`: (optional) List of allowed values (randomly sampled if provided)

```python
"score": {
    "type": "float",
    "distribution": "normal",
    "params": {"loc": 70, "scale": 10}
}
```

---

## Output Format

Returns a `pandas.DataFrame` by default:

```python
import pandas as pd
assert isinstance(df, pd.DataFrame)
```

---

## Requirements

- Python 3.7+
- pandas
- numpy
- faker

---

## License

MIT License. Use freely with credit.

---

## Author

Developed by IkigamiSama with help of Claude of course
