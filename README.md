# Deep Learning Benchmarks (RTX 2080 TI vs. RTX 2070)

# Benchmark

## Software

* Lambdalabs Benchmark, see repository [here](https://github.com/lambdal/lambda-tensorflow-benchmark)
* Yusaku Sako's benchmark, see repository [here](https://github.com/u39kun/deep-learning-benchmark)
* TensorFlow 1.12 for CUDA 10 + cudnn 7.3.1, from [here](https://github.com/tensorflow/tensorflow/issues/22706#issuecomment-429594338)
* `nvidia-docker` with `nvidia/cuda:10.0-cudnn7-devel` image, from [here](https://hub.docker.com/r/nvidia/cuda/)

## Hardware

* AMD Ryzen 7 2700X CPU
* G.Skill Trident Z, 32 GB, CL14 14-14-34
* ASRock X470 Taichi Ultimate
* Zotac RTX 2080 TI AMP
* Zotac RTX 2070 AMP Extreme

# Results (Lambdalabs benchmark)

## **syn-replicated-fp32-1gpus**

| Config     | 2700X-GeForce_RTX_2080_Ti | 2700X-GeForce_RTX_2070 | Difference
| ---------- | ------------------------- | ---------------------- | --------------
| resnet50   | 307.54                    | 209.46                 | 98.08 (32 %)
| resnet152  | 117.2                     | 81.59                  | 35.61 (30 %)
| inception3 | 205.31                    | 136.94                 | 68.37 (33 %)
| inception4 | 85.66                     | 57.98                  | 27.68 (32 %)
| vgg16      | 181.17                    | 120.9                  | 60.27 (33 %)
| alexnet    | 3835.94                   | 2510.35                | 1325.59 (35 %)
| ssd300     | 156.91                    | 108.53                 | 48.38 (31 %)

## **syn-parameter_server-fp32-1gpus**

| Config     | 2700X-GeForce_RTX_2080_Ti | 2700X-GeForce_RTX_2070 | Difference
| ---------- | ------------------------- | ---------------------- | ----------------
| resnet50   | 306.02                    | 208.58                 | 97.44 (32 %)
| resnet152  | 116.98                    | 81.62                  | 35.36 (30 %)
| inception3 | 205.14                    | 137.0                  | 68.14 (33 %)
| inception4 | 85.63                     | 58.01                  | 27.62 (32 %)
| vgg16      | 181.14                    | 120.97                 | 60.17 (33 %)
| alexnet    | 3834.12                   | 2512.17                | 1321.95 (34 %)
| ssd300     | 156.78                    | 108.57                 | 48.21 (31 %)

## **syn-replicated-fp16-1gpus**

| Config     | 2700X-GeForce_RTX_2080_Ti | 2700X-GeForce_RTX_2070 | Difference
| ---------- | ------------------------- | ---------------------- | ----------------
| resnet50   | 496.29                    | 344.88                 | 151.41 (31 %)
| resnet152  | 187.12                    | 131.68                 | 55.44 (30 %)
| inception3 | 305.53                    | 200.72                 | 104.81 (34 %)
| inception4 | 118.36                    | 83.98                  | 34.38 (29 %)
| vgg16      | 264.88                    | 170.18                 | 94.7 (36 %)
| alexnet    | 5274.9                    | 3297.37                | 1977.53 (37 %)
| ssd300     | 207.26                    | 145.86                 | 61.4 (30 %)

## **syn-parameter_server-fp16-1gpus**

| Config     | 2700X-GeForce_RTX_2080_Ti | 2700X-GeForce_RTX_2070 | Difference
| ---------- | ------------------------- | ---------------------- | ----------------
| resnet50   | 501.49                    | 347.51                 | 153.98 (31 %)
| resnet152  | 190.38                    | 133.54                 | 56.84 (30 %)
| inception3 | 307.93                    | 202.11                 | 105.82 (34 %)
| inception4 | 120.55                    | 85.35                  | 35.2 (29 %)
| vgg16      | 269.87                    | 173.37                 | 96.5 (36 %)
| alexnet    | 5371.81                   | 3349.07                | 2022.74 (38 %)
| ssd300     | 207.19                    | 146.78                 | 60.41 (29 %)

# Results (Yusaku Sako's benchmark)

## RTX 2080 TI

| Precision   | vgg16 eval   | vgg16 train   | resnet152 eval   | resnet152 train
|:------------|:-------------|:--------------|:-----------------|:------------------
| 32-bit      | 29.0ms       | 91.4ms        | 43.6ms           | 191.2ms
| 16-bit      | 18.7ms       | 60.2ms        | 25.5ms           | 135.0ms

## RTX 2070

| Precision   | vgg16 eval   | vgg16 train   | resnet152 eval   | resnet152 train
|:------------|:-------------|:--------------|:-----------------|:------------------
| 32-bit      | 42.6ms       | 130.6ms       | 65.1ms           | 264.2ms
| 16-bit      | 29.0ms       | 94.2ms        | 39.5ms           | 183.9ms

## Comparison

### 32-bit

| Network         | RTX 2080 TI | RTX 2070 | Difference
| --------------- | ----------- | -------- | ------------
| vgg16 eval      | 29.0ms      | 42.6ms   | 13.6 ( 32 %)
| vgg16 train     | 91.4ms      | 130.6ms  | 39.2 ( 30 %)
| resnet152 eval  | 43.6ms      | 65.1ms   | 21.5 ( 33 %)
| resnet152 train | 191.2ms     | 264.2ms  | 73.0 ( 28 %)

### 16-bit

| Network         | RTX 2080 TI | RTX 2070 | Difference
| --------------- | ----------- | -------- | ------------
| vgg16 eval      | 18.7ms      | 29.0ms   | 10.3 ( 36 %)
| vgg16 train     | 60.2ms      | 94.2ms   | 34.0 ( 36 %)
| resnet152 eval  | 25.5ms      | 39.5ms   | 14.0 ( 35 %)
| resnet152 train | 135.0ms     | 183.9ms  | 48.9 ( 27 %)

# FAQ

Coming here soon!

# Contact (Bugs, Feedback, Contribution and more)

For questions about `dl-benchmarks`, please open an issue
[here](https://github.com/stefan-it/dl-benchmarks/issues).
