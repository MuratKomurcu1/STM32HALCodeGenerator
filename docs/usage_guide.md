usage_guide = '''# STM32 HAL Code Generator - Usage Guide

## Quick Start
```python
from transformers import AutoTokenizer, AutoModelForCausalLM

model_name = "MuratKomurcu/stm32-hal-codegen"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name)

prompt = """// STM32_PROJECT: LED_CONTROL
// TASK: Generate LED blink code
// REQUIREMENT: Blink LED on PC13 every 1000ms

"""

inputs = tokenizer(prompt, return_tensors="pt")
outputs = model.generate(inputs["input_ids"], max_length=500)
code = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(code)
