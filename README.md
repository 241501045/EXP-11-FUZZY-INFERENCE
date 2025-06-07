# EXP-11-FUZZY-INFERENCE
import numpy as np

# Define fuzzy membership functions
def low(x):
    return max(0, min(1, (30 - x) / 20))

def medium(x):
    return max(0, min((x - 10) / 20, (50 - x) / 20))

def high(x):
    return max(0, min(1, (x - 30) / 20))

# Define fuzzy rules
def fuzzy_inference(temp):
    # Fuzzification
    low_degree = low(temp)
    med_degree = medium(temp)
    high_degree = high(temp)

   # Rule evaluation (example rules)
   # If temperature is low, then fan_speed is low (0.2)
   # If temperature is medium, then fan_speed is medium (0.5)
   # If temperature is high, then fan_speed is high (1.0)
   low_rule = low_degree * 0.2
   med_rule = med_degree * 0.5
   high_rule = high_degree * 1.0

   # Aggregation (max of all rules)
   aggregated = max(low_rule, med_rule, high_rule)

   return aggregated

# Example usage
temperature = 25
fan_speed = fuzzy_inference(temperature)
print(f"Temperature: {temperature}, Fan speed (fuzzy output): {fan_speed:.2f}")

