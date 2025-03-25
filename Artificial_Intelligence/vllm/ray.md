# **ray集群**

## 部署

- 头节点启动

  ```bash
  ray start --head --port=6379 --node-ip-address=<头节点IP>
  ```

- 子节点启动

  ```bash
  ray start --address=<头节点IP>:6379 --node-ip-address=<子节点IP>
  ```

  

