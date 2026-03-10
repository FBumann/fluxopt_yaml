# fluxopt-yaml

Declarative YAML + CSV model definition for
[fluxopt](https://fbumann.github.io/fluxopt/) energy system models.

!!! warning "Early development"
    This package is experimental — the API may change between releases.

## Installation

```bash
pip install fluxopt-yaml
```

## Quick start

```python
from fluxopt_yaml import optimize_yaml

result = optimize_yaml('model.yaml')
print(result.objective)
```

Example YAML file:

```yaml
timeseries: data.csv

carriers:
  - id: gas
  - id: heat

effects:
  - id: cost
    is_objective: true

ports:
  - id: grid
    imports:
      - carrier: gas
        size: 500
        effects_per_flow_hour:
          cost: "gas_price * 1.19"
  - id: demand
    exports:
      - carrier: heat
        size: 100
        fixed_relative_profile: "demand_profile"

converters:
  - id: boiler
    type: boiler
    thermal_efficiency: 0.9
    fuel:
      carrier: gas
      size: 300
    thermal:
      carrier: heat
      size: 200
```

## Links

- [User Guide](guide.md) — full YAML format reference
- [API Reference](api.md)
- [fluxopt documentation](https://fbumann.github.io/fluxopt/)
- [Source code](https://github.com/FBumann/fluxopt-yaml)
