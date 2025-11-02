# Toy LLM Fine-Tuning & Inference Project  
A lightweight project for fine-tuning small LLMs with LoRA and running inference/evaluation, optimized for Apple Silicon.


## 1. Technical Specification  
All training runs are optimized for **Apple M4 Max chips with 48GB on-chip memory**.


## 2. Prerequisites  
Project dependencies are declared in `pyproject.toml`. Install them via:  
```bash
pip install -e .  # For editable mode (recommended for development)
# Or install directly
pip install .
```


## 3. Run Test Training  
Execute the test training script to start a trial run:  
```bash
./train_toy_llm.sh
```


## 4. LoRA Adapter Fusion  
After fine-tuning, fuse the LoRA adapter with the base model for deployment:  
- Default: Loads adapters from `adapters/` and saves the fused model to `fused_model/`.  
- Both paths are configurable (adjust via script flags or config files).


## 5. Inference & Evaluation  
### Generate Text  
Run inference with the trained model + LoRA adapter using `mlx_lm`:  
```bash
mlx_lm.generate \
  --model <path_to_model> \
  --adapter-path <path_to_adapters> \
  --prompt "<your_model_prompt>"
```

### Benchmark Evaluation  
Evaluate on custom datasets with:  
```bash
mlx_lm.lora \
  --model <path_to_model> \
  --adapter-path <path_to_adapters> \
  --data <path_to_data> \
  --test
```
