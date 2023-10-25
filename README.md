# Model-Compression

The [ViT](https://huggingface.co/google/vit-base-patch16-224) pre-trained base model was fine-tuned on the following [dataset](https://huggingface.co/datasets/cats_vs_dogs). All models were tested on CPU on the same test subset of the previously mentioned dataset. **CPU model:** Intel(R) Xeon(R) CPU @ 2.20GHz. The results are presented in the table below:

| Methods                           | Model Size (MB) | Metric (F1-score) | Inference Time (1 sample) |
| :--- | :---: | :---: | :---: |
| Plain Model                       | 327.363         | 1.000             | 1090 ms ± 17 ms                    |
| Dynamic Quantization              | 84.413          | 1.000             | 413 ms ± 3.96 ms                   |
| Unstructured Pruning              | 327.363         | 0.491             | 622 ms ± 14.5 ms                   |
| Structured Pruning                | 327.363         | 0.494             | 708 ms ± 144 ms                    |
| Transformers Pipeline             | 327.363         | 0.999             | 783 ms ± 6.11 ms                   |
| Optimum Pipeline                  | 327.553         | 0.999             | 499 ms ± 64.2 ms                   |
| ORTModel with ONNX                | 327.341         | 0.999             | 362 ms ± 9.13 ms                   |

#### HW_1
For the dynamic quantization method, torch.qint8 data type was used. Both structured and unstructured pruning methods were utilized with parameters such as L1-norm and the quantity of model parameters to prune was set to 10%.

#### HW_2
The TFViT model was used for the weights clustering method.

#### HW_3
For the distillation task, ViT model was used as a teacher and ResNet-18 model was used as a student. The student model showed the same performance after had been trained for 5 epochs while possessing roughly 8 times less the amount of trainable parameters as the teacher model has. Inference speed of the distilled model is 26.39 % faster.

#### HW_4
The ViT model was converted to ONNX and OpenVINO formats.

#### HW_5
The Hugging Face Optimum library was used for tuning the ViT model performance using Transformers pipelines and ONNX pipeline accelerations.
