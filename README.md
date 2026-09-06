# 📁 Local Filesystem MCP

### Claude Desktop + Model Context Protocol + Local Filesystem

A simple **Model Context Protocol (MCP)** project that connects **Claude Desktop** to a local filesystem, allowing Claude to interact with files and folders through MCP tools.

This project demonstrates how an AI assistant can securely interact with local files through a dedicated MCP server instead of directly accessing the operating system.

---

## 🧠 What is MCP?

**Model Context Protocol (MCP)** is a standard that allows AI applications to connect with external tools, data sources, and services.

In this project, Claude Desktop acts as the AI client and communicates with a local Filesystem MCP server.

```text
┌─────────────────────┐
│    Claude Desktop   │
│      AI Client      │
└──────────┬──────────┘
           │
           │ MCP
           ▼
┌─────────────────────┐
│ Filesystem MCP      │
│      Server         │
└──────────┬──────────┘
           │
           │ File Operations
           ▼
┌─────────────────────┐
│    Local Folder     │
│                     │
│ 📄 Documents        │
│ 📁 Projects         │
│ 📄 Reports          │
│ 📁 Data             │
└─────────────────────┘
```

---

## 🚀 Project Overview

The goal of this project is to demonstrate a **local MCP integration** using Claude Desktop.

Claude can communicate with the Filesystem MCP server and perform supported filesystem operations on an explicitly configured directory.

### Workflow

```text
User
  ↓
Claude Desktop
  ↓
MCP Protocol
  ↓
Filesystem MCP Server
  ↓
Configured Local Directory
```

---

## ✨ Features

* 🔌 Claude Desktop integration
* 📁 Local filesystem access through MCP
* 📄 File reading and management
* 📂 Directory navigation
* 🔍 File and folder operations
* 🔐 Access limited to configured directories
* 🧩 Demonstrates MCP client-server architecture
* 💻 Runs locally on Windows
* 🚫 No cloud database required
* 🚫 No external backend required

---

## 🛠️ Technologies Used

| Technology             | Purpose                       |
| ---------------------- | ----------------------------- |
| Claude Desktop         | MCP Client / AI Assistant     |
| Model Context Protocol | Communication layer           |
| Filesystem MCP Server  | Filesystem tools              |
| Node.js / npx          | Running the MCP server        |
| Windows                | Local development environment |
| JSON                   | MCP configuration             |

---

## 📋 Prerequisites

Before running this project, install:

* Claude Desktop
* Node.js
* npm / npx

Verify Node.js:

```bash
node --version
```

Verify npm:

```bash
npm --version
```

---

# ⚙️ Setup

## 1. Create a Local Folder

Create a folder that Claude will be allowed to access.

Example:

```text
E:\MCP\filesystem-project
```

You can place test files inside it:

```text
filesystem-project/
├── documents/
│   ├── notes.txt
│   └── report.txt
│
├── data/
│   └── sample.csv
│
└── README.txt
```

---

## 2. Configure Claude Desktop

Claude Desktop uses:

```text
claude_desktop_config.json
```

On Windows, the configuration file is normally located at:

```text
%APPDATA%\Claude\claude_desktop_config.json
```

Add the Filesystem MCP server:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "E:\\MCP\\filesystem-project"
      ]
    }
  }
}
```

### ⚠️ Important

Change:

```text
E:\\MCP\\filesystem-project
```

to your actual local folder.

---

## 3. Restart Claude Desktop

After saving the configuration:

1. Completely close Claude Desktop.
2. Start Claude Desktop again.
3. Open the MCP/tool section.
4. Verify that the Filesystem MCP server is connected.

---

# 🧪 Testing the MCP Server

Once connected, you can ask Claude questions such as:

```text
List the files in my filesystem project.
```

```text
Read the contents of notes.txt.
```

```text
Show me the files inside the documents folder.
```

```text
Create a new text file called test.txt.
```

```text
Read all text files in the project folder.
```

Claude will use the appropriate MCP filesystem tools to interact with the configured directory.

---

# 🔐 Security

The Filesystem MCP server should only be given access to directories that you intentionally configure.

For example:

```text
E:\MCP\filesystem-project
```

Claude should not automatically receive unrestricted access to your entire computer.

### Recommended practice

Create a dedicated directory for MCP testing:

```text
E:\MCP\filesystem-project
```

Avoid giving access to sensitive directories containing:

* Passwords
* Personal documents
* Banking information
* Credentials
* Private keys
* System files

---

# 🏗️ Architecture

```text
                    ┌──────────────────┐
                    │      User        │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Claude Desktop   │
                    │    MCP Client    │
                    └────────┬─────────┘
                             │
                             │ MCP
                             ▼
                    ┌──────────────────┐
                    │ Filesystem MCP   │
                    │     Server       │
                    └────────┬─────────┘
                             │
                             │
                             ▼
                    ┌──────────────────┐
                    │  Local Filesystem│
                    │                  │
                    │ 📁 Documents     │
                    │ 📁 Data          │
                    │ 📄 Reports       │
                    └──────────────────┘
```

---

# 📂 Suggested Project Structure

```text
local-filesystem-mcp/
│
├── README.md
│
├── screenshots/
│   ├── claude-filesystem-mcp.png
│   ├── mcp-tools.png
│   └── filesystem-folder.png
│
├── demo/
│   ├── sample.txt
│   ├── sample.csv
│   └── test-folder/
│
└── config/
    └── claude_desktop_config.example.json
```

### ⚠️ Don't upload your personal Claude configuration

For GitHub, create:

```text
config/claude_desktop_config.example.json
```

instead of uploading your real configuration file.

---

# 📸 Screenshots

Add screenshots demonstrating the working project.

### Claude Desktop + Filesystem MCP

```text
screenshots/claude-filesystem-mcp.png
```

### MCP Tools

```text
screenshots/mcp-tools.png
```

### Local Filesystem

```text
screenshots/filesystem-folder.png
```

Example Markdown:

```markdown
![Claude Desktop Filesystem MCP](screenshots/claude-filesystem-mcp.png)
```

---

# 🎯 Learning Objectives

This project demonstrates:

* Understanding of MCP architecture
* MCP client-server communication
* Local MCP server integration
* Claude Desktop configuration
* Filesystem tool integration
* Local AI tool execution
* Access-controlled filesystem interaction
* Practical AI agent tooling

---

# 🔄 MCP Connection Method

This project represents:

### Method 1 — Local MCP

```text
Claude Desktop
      │
      │ MCP
      ▼
Local MCP Server
      │
      ▼
Local Filesystem
```

The entire MCP server runs locally on the development machine.

---

# 💡 Example Use Cases

This architecture can be extended to build:

* 📄 AI document assistants
* 📊 Local data analysis agents
* 📝 Automated report generators
* 🔍 Local file search assistants
* 📁 Project management assistants
* 🧠 AI coding assistants
* 📚 Knowledge-base assistants

---

# 🚧 Future Improvements

Possible extensions include:

* Add custom filesystem tools
* Add file search functionality
* Add document summarization
* Add CSV analysis
* Add PDF processing
* Add multiple MCP servers
* Add logging and monitoring
* Add automated testing
* Create a custom MCP server using Python

---

# 👨‍💻 Project Purpose

This project was created as a practical demonstration of **Model Context Protocol (MCP) integration with Claude Desktop**.

It focuses on understanding how AI assistants can interact with local resources through standardized MCP tools.

---

## ⭐ Portfolio

This project can be used as a portfolio demonstration for:

**AI Engineer | Generative AI Engineer | AI Agent Developer | MCP Developer**

---

## 📜 License

This project is intended for educational and portfolio purposes.
