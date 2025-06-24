### Environment
- Platform: Google colab
- GPU: T4
### Reference
- [TA's slide](https://speech.ee.ntu.edu.tw/~hylee/ml/ml2025-course-data/hw10.pdf)
### How to run
In the file `b12901022_hw10_1.ipynb`
1. Run all the code in the section **Utilities**
2. Run all the code in the section **Method 1: BLIP Diffusion**
3. After the execution finish, the submission file containing the images could be found at `/content/results.zip`


> [!IMPORTANT] 
> You **MUST** run the cell below (it is inside the **Utilities** section), otherwise colab will use its default version of transformers, and the performance will be significantly impacted.
```
!pip install transformers==4.50.3
```
