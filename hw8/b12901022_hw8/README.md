### Environment
- Platform: Google colab
- GPU: T4
### Reference
- [TA's slide](https://speech.ee.ntu.edu.tw/~hylee/ml/ml2025-course-data/hw8.pdf)
### How to run
1. All the code in the section **Environment setup** has to be run
2. In the section **Predefined Function**, all the code under **Util Function** has to be run
3. For the method you hope to use, run the corresponding section under **Predefined Function** (e.g. If you hope to use MEMIT, run all the code in the **MEMIT** section under **Predefined Function**)

> [!WARNING]  
> **DO NOT** run the code for one method and then execute another editing method, otherwise the redefinition of the function `get_context_templates` will cause an error. For example, if you hope to you MEMIT, you must first run the code in `Predefined Function -> MEMIT` before executing the main process, and you **MUST NOT** overwrite function definitions by running the code in `Predefined Function -> ROME` after running `Predefined Function -> MEMIT`.

4. In **Main Process**, all the code under **Getting the model** has to be run
5. If you hope to do single editing, run the code under **Single Editing**, to switch between methods (FT and ROME), there is a cell 
``` Python
try:
    with torch.no_grad():
        for k, v in orig_weights.items():
            get_parameter(model, k)[...] = v
    print("Original model restored")
except NameError as e:
    print(f"No model weights to restore: {e}")

set_requires_grad(True, model)

###### TODO: Change the method :) ######
# RewritingParamsClass, apply_method, hparam = FTHyperParams, apply_ft_to_model, ft_hparam
RewritingParamsClass, apply_method, hparam = ROMEHyperParams, apply_rome_to_model, rome_hparam

print_loud(f"Retrieving hyperparameters")
hparams = RewritingParamsClass(**hparam)
print(hparams)
```
assign the variables `RewritingParamsCalss`, `apply_method`, `hparam` accordingly (just uncomment the line you want and comment out the other)

6. If you hope to do multiple  editing, run the code under **Multiple Editing**, to switch between methods, there is a cell
```Python
try:
    with torch.no_grad():
        for k, v in orig_weights.items():
            get_parameter(model, k)[...] = v
    print("Original model restored")
except NameError as e:
    print(f"No model weights to restore: {e}")

set_requires_grad(True, model)

###### TODO: Change the method :) ######
# RewritingParamsClass, apply_method, hparam = FTHyperParams, apply_ft_to_model, ft_hparam
# RewritingParamsClass, apply_method, hparam = ROMEHyperParams, apply_rome_to_model, rome_hparam
RewritingParamsClass, apply_method, hparam = MEMITHyperParams, apply_memit_to_model, memit_hparam


print_loud(f"Retrieving hyperparameters")
hparams = RewritingParamsClass(**hparam)
print(hparams)
```
assign the variables `RewritingParamsCalss`, `apply_method`, `hparam` accordingly (just uncomment the line you want and comment out the others)



If you hope to change the data amount, there is a cell
```Python
import json
with open("/content/HW8_data.json", "r") as file:
    ###### TODO: Change the range of your code ######
    # requests = json.load(file)[0:10]
    requests = json.load(file)

generation_prompts = [[], [], [], []]
ans_new = [[], [], [], []]
ans_true = [[], [], [], []]
for r in requests:
  generation_prompts[0].append(r["prompt"].replace("{}", r["subject"]))
  ans_true[0].append(r["target_true"]["str"])
  ans_new[0].append(r["target_new"]["str"])
  for p in r["paraphrase_prompts"]:
    generation_prompts[1].append(p["prompt"])
    ans_true[1].append(r["target_true"]["str"])
    ans_new[1].append(r["target_new"]["str"])
  for n in r["neighborhood_prompts"]:
    generation_prompts[2].append(n["prompt"])
    ans_true[2].append(r["target_true"]["str"])
    ans_new[2].append(r["target_true"]["str"])

  for t in r["portable_prompts"]:
    generation_prompts[3].append(t["prompt"])
    ans_true[3].append(t["portable_target_true"])
    ans_new[3].append(t["portable_target_new"])
print(len(requests))
```
modify the line `requests = json.load(file)...`

