# vllm启动

## 环境准备

- OS: Linux

- Python: 3.9 – 3.12

  ```bash
  conda create -n vllm python=3.12 -y
  conda activate vllm
  pip install vllm
  ```

- 注意，需要保证每个节点上的环境一致，可以通过拷贝env文件解决

## 推理

## 分布式服务

1. 确保ray集群状态正常

2. 启动命令

   ```bash
    vllm serve /model-path --tensor-parallel-size 8 --pipeline-parallel-size 2
   ```

3. 参数解释

   - --tensor-parallel-size 		#每个节点上的GPU数量
   - --pipeline-parallel-size       #节点数量
   - /model-path    #模型路径，如果模型在每个节点都有一份，写绝对路径；如果模型存放在共享文件，填写共享文件地址