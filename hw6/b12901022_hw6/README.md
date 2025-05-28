# ML HW6
## Environment
- Platform: Kaggle
- GPU: P100
## How to run the code 
1. Open `b12901022/b12901022_hw6_1.ipynb` in kaggle.
2. The kaggle account has to be verified with phone number and has at least 8 hours of GPU quota remaining (assuming under free plan)
3. Click `run all` at the top of the page (in the kaggle notebook editor)
4. As soon as the 2800-th step of the training process has completed, and the `/kaggle/working/sft/checkpoint-2800` directory exist, the code block for training can be terminated (to save time)
5. Execute the remaining cells in order
6. After all the cells are executed, the submission file `/kaggle/working/b12901022.txt` should be generated and can be downloaded directly using the UI of kaggle notebook editor.
## References
This homework is done with assistment from GPT-4o. The choices of parameters `LoraConfig.r`, `LoraConfig.alpha`, `SFTConfig.weight_decay` are decided based on suggestions from GPT-4o. GPT is only used to help decided values of parameters, all of the code is either given by TA or hand-coded by me.
