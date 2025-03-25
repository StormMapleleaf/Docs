# **fastllm 部署指南**

## **环境准备**  

- **CUDA**：尽可能新，使用 `nvidia-smi` 检查  
- **NVIDIA Toolkit**：尽可能新，使用 `nvcc --version` 检查  
- **编译环境**：需安装 `gcc`、`g++` (建议 9.4 以上)、`make`、`cmake` (建议 3.23 以上)  

---

## **编译 fastllm**  

```bash
# 克隆仓库
git clone https://github.com/ztxz16/fastllm.git

# 进入仓库所在目录
cd fastllm

# 默认编译命令（启用 CUDA）
bash install.sh -DUSE_CUDA=ON -D CMAKE_CUDA_COMPILER=$(which nvcc) 

# 可指定 CUDA 架构（如 4090 使用 89 架构）
bash install.sh -DUSE_CUDA=ON -DCUDA_ARCH=89 -D CMAKE_CUDA_COMPILER=$(which nvcc)

# 仅编译 CPU 版本
bash install.sh
```

---

## **运行 Python Demo**  

### **1. 启动 API 服务**  

```bash
pip install -r requirements-server.txt  # 安装依赖
python3 -m ftllm.server -t 16 -p ~/Qwen2-7B-Instruct/ --port 8080 --model_name qwen
# ~/Qwen2-7B-Instruct/ 为模型路径
```

### **2. 终端对话**  

```bash
python3 -m ftllm.chat -t 16 -p ~/Qwen2-7B-Instruct/
```

### **3. WebUI 使用**  

```bash
pip install streamlit-chat
python3 -m ftllm.webui -t 16 -p ~/Qwen2-7B-Instruct/ --port 8080
```

### **4. 参数说明**  

```bash
--dtype int8   # 使用模型默认精度，可添加 --dtype int8 指定量化精度
-p             # 模型路径
--port         # 启动端口
```

---

## **运行 C++ Demo**  

```bash
# 进入 fastllm/build-fastllm 目录

# 命令行聊天程序，支持打字机效果
./main -p ~/Qwen2-7B-Instruct/

# 简易 WebUI，支持流式输出 + 动态 batch，可多路并发访问
./webui -p ~/Qwen2-7B-Instruct/ --port 1234
