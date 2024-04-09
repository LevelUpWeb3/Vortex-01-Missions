# Guide to Get Started w/ Sindri

## Installation and Setup

Before getting started, you need to [create a Sindri account](https://sindri.app/signup) and provide an API key.

Before starting installation, make sure that [Node.js](https://nodejs.org/en) or [Yarn](https://yarnpkg.com/) and [Python 3](https://www.python.org/downloads/) are installed.

### Install Sindri CLI

```
yarn add sindri@latest
```

### Authenticate and Login with Sindri CLI

```
npx sindri@latest login
```

Enter your
- username,
- password, and
- API key.

## Code

Clone the resources repo:

```
git clone https://github.com/Sindri-Labs/sindri-resources.git
```

```
cd sindri-resources/circuit_database/circom/multiplier2
```

### Compile and Deploy

```
npx sindri@latest deploy
```

Congrats! Now, go back to `sindri-resources/circuit_database/circom/` directory.

### Install Sindri Python SDK

```
 python3 -m venv venv && source venv/bin/activate && pip install sindri
```

### Create a Python File

```
touch prove.py
```

```python
#! /usr/bin/env python
import os
from sindri import Sindri

API_KEY = "YOUR_API_KEY"

sindri = Sindri(API_KEY)
sindri.set_verbose_level(1)

# Circuit ID you you saved from compilation
circuit_id = "{your-circuit-id}"

# Prove the circuit
proof_input_file_path = "./multiplier2/input.json"
with open(proof_input_file_path, "r") as f:
    proof_id = sindri.prove_circuit(circuit_id, f.read())
```

```
python prove.py
```

You have just run your first proof on Sindri!