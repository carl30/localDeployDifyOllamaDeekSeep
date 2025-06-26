Dify+Ollama+Deekseek

# 目的

本地运行AI，编写agent

# 运行环境

windows

docker

# 步骤

安装Ollama

命令行下载Deepseek大模型

## 安装Dify

下载压缩包，解压

dify/docker文件夹下，复制.env.example并另存为.env

其中最后一行需要添加

```yaml
#启用自定义模型
CUSTOM_MODEL_ENABLED=true
#指定 olama 的AP地址(根据部署环境调整IP)
OLLAMA_API_BASE_URL=host.docker.internal:11434
```

在dify/docker下打开cmd

执行

```bash
docker compose up -d
```

把dify运行进docker中

执行成功如图

![image](https://github.com/user-attachments/assets/e98a43c6-232b-41d0-8ba2-a8098f624fd5)


检查docker容器内有dify images

![image](https://github.com/user-attachments/assets/8deb0d22-7947-4190-aa48-83bab0a61b99)


即为成功

## Dify内调用LLM

## Dify内调用text embedding model

bge-m3

# 遇到问题

## Dify调用大模型失败

**[models] Server Unavailable Error, HTTPConnectionPool(host='192.168.30.2', port=11434): Max retries exceeded with url: /api/chat (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x70b801cc2bd0>: Failed to establish a new connection: [Errno 111] Connection refused'))**

>>>

1.检查在dify中配置的base URL是否是

```bash
http://host.docker.internal:11434
```

2.检查dify/docker下的.env最后是否已经添加2行配置

参考：

[https://www.notion.so/carlzilla/AI-218177405e2280fe8fb8dde3e69f652b?source=copy_link#218177405e22806fa9c7c2eb24d0415d](https://www.notion.so/AI-218177405e2280fe8fb8dde3e69f652b?pvs=21)

3.dify是否已经成功部署到docker
