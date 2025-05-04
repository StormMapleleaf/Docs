intel core i9-14900KF,NVIDIA4090D，memory 32GB

| 模型                       | 模型大小 | 加载方式                       | 单路/cpu/gpu   | 双路         | 三路         |
| -------------------------- | -------- | ------------------------------ | -------------- | ------------ | ------------ |
| Qwen1.5-MoE-A2.7B          | 28.6G    | --device cuda --moe_device cpu | (原精度爆内存) |              |              |
| Qwen1.5-MoE-A2.7B-INT8     | 15.3G    | --device cuda --moe_device cpu | 160t/29G/18G   | ERROR        |              |
| DeepSeek-V2-Lite-Chat-INT8 | 16.5G    | --device cuda --moe_device cpu | 18t/23G/1.2G   | 30t/24G/1.2G | 40t/24G/1.2G |
| DeepSeek-V2-Lite-Chat-INT8 | 16.5G    | --device cpu --moe_device cuda | 27t/26G/17G    | 40t/26G/17G  | 45t/26G/18G  |

