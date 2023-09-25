# Model-Compression

## HW_1

The [ViT](https://huggingface.co/google/vit-base-patch16-224) pre-trained base model was fine-tuned on the following [dataset](https://huggingface.co/datasets/cats_vs_dogs). For the dynamic quantization method, torch.qint8 data type was used. Both structured and unstructured pruning methods were utilized with parameters such as L1-norm and the quantity of model parameters to prune was set to 10%. All models were tested on CPU on the same test subset of the previously mentioned dataset. **CPU model:** Intel(R) Xeon(R) CPU @ 2.20GHz. The results are presented in the table below:

| Methods                           | Model Size (MB) | Metric (F1-score) | Inference Time (50 images) |
| --- | :---: | :---: | :---: |
| Plain Model                       | 327.363         | 1.000             | 16.8s ± 317ms                    |
| Dynamic Quantization              | 84.413          | 1.000             | 12.6s ± 1.16s                    |
| Unstructured Pruning              | 327.363         | 0.491             | 15.2s ± 462ms                    |
| Structured Pruning                | 327.363         | 0.494             | 14.5s ± 290ms                    |