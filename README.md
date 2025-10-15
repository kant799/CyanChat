# CyanChat 💬

**一个强大、通用的多窗口 Web 客户端，用于同时与多个大语言模型（LLM）进行交互。完全在您的浏览器中运行，无需后端，确保您的 API 密钥安全无虞。**

---

## 📖 项目简介

CyanChat 是一个零依赖、单文件的 Web 应用，旨在简化与多个AI模型的并行对话。无论您是想比较不同模型（如 ChatGPT、DeepSeek、Claude）对同一问题的回答，还是需要为不同任务配置多个“数字人格”(Personas)，CyanChat 都能提供一个流畅、直观的界面。

由于它完全是客户端应用，您的所有配置，包括 API Provider 信息和 API 密钥，都只会安全地存储在您浏览器的 `localStorage` 中，绝不会被上传到任何服务器。

## ✨ 主要特性

*   **多窗口界面**: 同时打开多个聊天窗口，并行与不同模型或不同系统提示词进行对话。
*   **广播式输入**: 一个输入框，全局生效。您发送的每一条消息都会被同时分发给所有打开的窗口，非常适合进行模型对比。
*   **通用 API 支持**: 兼容任何遵循 OpenAI API 格式的端点。无论是 OpenAI、DeepSeek，还是本地通过 LM Studio / Ollama 部署的模型，都能轻松接入。
*   **灵活的 Provider 管理**: 在设置中轻松添加、编辑和删除 API 服务提供商。
*   **自定义系统提示词**: 为每个聊天窗口设置独立的系统提示词 (System Prompt)，赋予每个窗口独特的“人格”或能力。
*   **流式响应**: 实时查看模型生成的文本，无需等待完整响应。
*   **100% 客户端**: 您的数据（API 密钥、对话历史）仅存储在本地浏览器，保障隐私安全。
*   **零配置部署**: 仅一个 `index.html` 文件，无需构建、无需服务器，直接在浏览器中打开即可使用。
*   **明暗主题切换**: 根据您的系统偏好或手动切换，保护您的眼睛。
*   **响应式设计**: 在桌面和移动设备上均有良好体验。

## 🛠️ 技术栈

*   **HTML5**
*   **Tailwind CSS**: 用于快速构建现代化 UI。
*   **Font Awesome**: 提供高质量图标。
*   **原生 JavaScript (ES6+)**: 无任何框架依赖，轻量且高效。

## 🚀 如何开始

由于浏览器安全策略的限制，直接通过 `file:///` 协议打开 `index.html` 文件可能会导致初始的系统提示词加载失败。为了确保所有功能正常工作，**强烈建议使用本地 Web 服务器来运行此应用**。

以下是几种简单快捷的启动方法：

### 方法 1：使用 VS Code 的 Live Server (推荐)

如果您使用 Visual Studio Code 作为代码编辑器，这是最简单的方法。

1.  **安装扩展**: 在 VS Code 的扩展市场中搜索并安装 [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) 扩展。
2.  **克隆或下载仓库**: 将本仓库文件下载到您的电脑上。
3.  **启动服务**: 在 VS Code 中打开项目文件夹，然后在 `index.html` 文件上右键，选择 `Open with Live Server`。
4.  浏览器将自动打开 `http://127.0.0.1:5500` (或类似地址)，应用即可完美运行。

### 方法 2：使用 Python (通用)

大多数 macOS 和 Linux 系统都预装了 Python。Windows 用户也可以轻松安装。

1.  **克隆或下载仓库**并进入项目目录。
    ```bash
    git clone https://github.com/YOUR_USERNAME/CyanChat.git
    cd CyanChat
    ```
2.  **启动服务器**: 打开终端或命令提示符，运行以下命令：

    *   **如果您使用 Python 3**:
        ```bash
        python3 -m http.server 8000
        ```
    *   **如果您使用 Python 2** (较旧的系统):
        ```bash
        python -m SimpleHTTPServer 8000
        ```
3.  **访问应用**: 在浏览器中打开 `http://localhost:8000`。

### 方法 3：使用 Node.js (适合 Web 开发者)

如果您安装了 Node.js 和 npm，可以使用 `http-server` 包。

1.  **安装 http-server**: 打开终端，运行以下命令进行全局安装（只需一次）：
    ```bash
    npm install -g http-server
    ```
2.  **克隆或下载仓库**并进入项目目录。
3.  **启动服务器**: 在项目根目录下运行：
    ```bash
    http-server -c-1
    ```
    *( `-c-1` 参数用于禁用缓存，确保您总能看到最新的更改 )*
4.  **访问应用**: 在浏览器中打开终端中显示的地址 (通常是 `http://127.0.0.1:8080`)。

### 方法 4：直接部署到线上 (零本地配置)

您也可以将此仓库 Fork 后，一键部署到免费的静态网站托管平台，如：

*   **GitHub Pages**: 在您 Fork 的仓库的 `Settings` -> `Pages` 中，选择从 `main` 分支的 `/ (root)` 目录部署。
*   **Vercel** 或 **Netlify**: 直接关联您的 GitHub 仓库，它们会自动为您构建和部署。

### ⚙️ 配置 API

成功启动应用后，为了开始聊天，您需要配置至少一个 API 服务提供商：

1.  点击页面右上角的 **设置图标** ⚙️。
2.  默认情况下，应用会提供几个模板。您可以点击 **"Add New Provider"** 添加新的，或点击现有模板进行编辑。
3.  在配置页面填写以下信息：
    *   **Provider Name**: 一个方便您识别的别名 (例如, "我的本地大模型")。
    *   **Base URL**: API 的基础端点。应用会自动在其后追加 `/chat/completions`。
        *   OpenAI 示例: `https://api.openai.com/v1`
        *   DeepSeek 示例: `https://api.deepseek.com`
        *   本地模型 (LM Studio) 示例: `http://localhost:1234/v1`
    *   **API Key**: 您的服务商提供的密钥。对于本地模型，此项可能不需要，可以填写任意字符（例如 `not-needed`）。
    *   **Available Models**: 您希望在该 Provider 下使用的模型列表，**每行一个**。例如：
        ```
        gpt-4o
        gpt-4-turbo
        gpt-3.5-turbo
        ```
4.  点击 **"Save Provider"** 保存。

现在，您就可以在每个聊天窗口的下拉菜单中选择您刚刚配置的 Provider 和模型了！

### 💬 开始聊天 (广播模式)
这是 CyanChat 的核心工作方式，请务必理解：

在页面底部的输入框中输入您的消息，按下 **Ctrl + Enter** 或点击发送按钮 ✈️。您的消息将同时发送到所有打开的聊天窗口中，并展示不同模型的回答。

您的这条消息将会被同时广播 (broadcast) 到所有已打开的聊天窗口中。每个窗口会根据其各自配置的 Provider、模型和系统提示词，独立地请求并展示回答。这个设计使得跨模型、跨角色的行为对比变得极其简单高效。

## 🤝 贡献

欢迎任何形式的贡献！如果您有好的想法、发现了 Bug 或者想改进代码，请随时：

1.  Fork 本仓库
2.  创建您的新分支 (`git checkout -b feature/AmazingFeature`)
3.  提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4.  将分支推送到远程 (`git push origin feature/AmazingFeature`)
5.  提交一个 Pull Request

## 📄 许可证

本项目采用 MIT 许可证。详情请见 `LICENSE` 文件。