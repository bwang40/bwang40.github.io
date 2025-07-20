## 简介

欢迎来到LangChain学院！
这是一套持续增长的模块化课程，专注于LangChain生态系统中的核心概念。
模块0为基础环境配置，模块1至4则聚焦LangGraph技术，逐步深入更高级的主题。
每个模块文件夹内都包含一组Jupyter笔记本文件，并配有相应的LangChain学院教程引导学习。各模块还设有`studio`子目录，内含我们将通过LangGraph API和Studio工具探索的相关流程图。

## 环境配置

### Python版本要求

为确保最佳学习体验，请使用Python 3.11或更高版本。
该版本是LangGraph运行的最佳兼容环境，若您当前版本较低，建议升级以获得流畅体验。
```
python3 --version
```

### 克隆代码库
```
git clone https://github.com/langchain-ai/langchain-academy.git
$ cd langchain-academy
```

### 创建虚拟环境并安装依赖

#### Mac/Linux/WSL系统
```
$ python3 -m venv lc-academy-env
$ source lc-academy-env/bin/activate
$ pip install -r requirements.txt
```

#### Windows Powershell
```
PS> python3 -m venv lc-academy-env
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
PS> lc-academy-env\scripts\activate
PS> pip install -r requirements.txt
```

### 运行Jupyter笔记本
若未安装Jupyter，请参考[官方安装指南](https://jupyter.org/install)。
```
$ jupyter notebook
```

### 环境变量配置
简要说明环境变量设置方法，也可使用`.env`文件配合`python-dotenv`库管理。

#### Mac/Linux/WSL系统
```
$ export API_ENV_VAR="your-api-key-here"
```

#### Windows Powershell
```
PS> $env:API_ENV_VAR = "your-api-key-here"
```

### 设置OpenAI API密钥
* 若未持有OpenAI API密钥，请至[官网注册](https://openai.com/index/openai-api/)
* 在环境中配置`OPENAI_API_KEY`变量

### 注册并配置LangSmith服务
* 前往[LangSmith官网](https://smith.langchain.com/)注册账号
* 了解如何在工作流中集成该服务，请参阅[使用指南](https://www.langchain.com/langsmith)及[官方文档](https://docs.smith.langchain.com/)
* 在环境中设置`LANGCHAIN_API_KEY`和`LANGCHAIN_TRACING_V2=true`变量

### 配置Tavily网页搜索API

* Tavily搜索API是专为LLM和RAG优化的搜索引擎，提供高效、快速且持久的搜索结果。
* 可通过[官网](https://tavily.com/)申请API密钥，注册流程简便且提供充足的免费额度。模块4部分课程将使用该服务。

* 在环境中配置`TAVILY_API_KEY`变量。

### 配置LangGraph Studio环境

* LangGraph Studio是用于可视化测试智能体的定制化IDE
* 支持在Mac/Windows/Linux系统本地运行并通过浏览器访问
* 本地开发服务器配置详见[开发文档](https://langchain-ai.github.io/langgraph/concepts/langgraph_studio/#local-development-server)与[运行指南](https://langchain-ai.github.io/langgraph/how-tos/local-studio/#run-the-development-server)
* 各模块的流程图文件存放于`module-x/studio/`目录
* 在每个模块的`/studio`目录下执行以下命令启动开发服务器：

```
langgraph dev
```

将看到如下输出：
```
- 🚀 API: http://127.0.0.1:2024
- 🎨 Studio UI: https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024
- 📚 API Docs: http://127.0.0.1:2024/docs
```

在浏览器中访问Studio界面：`https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024`

* 使用Studio需创建包含API密钥的.env文件
* 以下命令示例为模块1至5创建配置文件：
```
for i in {1..5}; do
  cp module-$i/studio/.env.example module-$i/studio/.env
  echo "OPENAI_API_KEY=\"$OPENAI_API_KEY\"" > module-$i/studio/.env
done
echo "TAVILY_API_KEY=\"$TAVILY_API_KEY\"" >> module-4/studio/.env
```