# Task Master [![GitHub stars](https://img.shields.io/github/stars/eyaltoledano/claude-task-master?style=social)](https://github.com/eyaltoledano/claude-task-master/stargazers)

[![CI](https://github.com/eyaltoledano/claude-task-master/actions/workflows/ci.yml/badge.svg)](https://github.com/eyaltoledano/claude-task-master/actions/workflows/ci.yml) [![npm version](https://badge.fury.io/js/task-master-ai.svg)](https://badge.fury.io/js/task-master-ai) [![Discord](https://dcbadge.limes.pink/api/server/https://discord.gg/taskmasterai?style=flat)](https://discord.gg/taskmasterai) [![License: MIT with Commons Clause](https://img.shields.io/badge/license-MIT%20with%20Commons%20Clause-blue.svg)](LICENSE)

[![NPM Downloads](https://img.shields.io/npm/d18m/task-master-ai?style=flat)](https://npm-stat.com/charts.html?package=task-master-ai) [![NPM Downloads](https://img.shields.io/npm/dm/task-master-ai?style=flat)](https://npm-stat.com/charts.html?package=task-master-ai) [![NPM Downloads](https://img.shields.io/npm/dw/task-master-ai?style=flat)](https://npm-stat.com/charts.html?package=task-master-ai)

### By [@eyaltoledano](https://x.com/eyaltoledano), [@RalphEcom](https://x.com/RalphEcom) & [@jasonzhou](https://x.com/jasonzhou1993)

[![Twitter Follow](https://img.shields.io/twitter/follow/eyaltoledano?style=flat)](https://x.com/eyaltoledano)
[![Twitter Follow](https://img.shields.io/twitter/follow/RalphEcom?style=flat)](https://x.com/RalphEcom)

A task management system for AI-driven development with Claude, designed to work seamlessly with Cursor AI.

## Requirements

Taskmaster utilizes AI across several commands, and those require a separate API key. You can use a variety of models from different AI providers provided you add your API keys. For example, if you want to use Claude 3.7, you'll need an Anthropic API key.

You can define 3 types of models to be used: the main model, the research model, and the fallback model (in case either the main or research fail). Whatever model you use, its provider API key must be present in either mcp.json or .env.

At least one (1) of the following is required:

- Anthropic API key (Claude API)
- OpenAI API key
- Google Gemini API key
- Perplexity API key (for research model)
- xAI API Key (for research or main model)
- OpenRouter API Key (for research or main model)

Using the research model is optional but highly recommended. You will need at least ONE API key. Adding all API keys enables you to seamlessly switch between model providers at will.

## Quick Start

### Option 1: MCP (Recommended)

MCP (Model Control Protocol) lets you run Task Master directly from your editor.

#### 1. Add your MCP config at the following path depending on your editor

| Editor       | Scope   | Linux/macOS Path                      | Windows Path                                      | Key          |
| ------------ | ------- | ------------------------------------- | ------------------------------------------------- | ------------ |
| **Cursor**   | Global  | `~/.cursor/mcp.json`                  | `%USERPROFILE%\.cursor\mcp.json`                  | `mcpServers` |
|              | Project | `<project_folder>/.cursor/mcp.json`   | `<project_folder>\.cursor\mcp.json`               | `mcpServers` |
| **Windsurf** | Global  | `~/.codeium/windsurf/mcp_config.json` | `%USERPROFILE%\.codeium\windsurf\mcp_config.json` | `mcpServers` |
| **VS Code**  | Project | `<project_folder>/.vscode/mcp.json`   | `<project_folder>\.vscode\mcp.json`               | `servers`    |

##### Quick Install for Cursor (One-Click)

[<img src="https://cursor.com/deeplink/mcp-install-dark.png" alt="Add Task Master MCP server to Cursor" style="max-height: 32px;">](cursor://anysphere.cursor-deeplink/mcp/install?name=taskmaster-ai&config=eyJjb21tYW5kIjoibnB4IiwiYXJncyI6WyIteSIsIi0tcGFja2FnZT10YXNrLW1hc3Rlci1haSIsInRhc2stbWFzdGVyLWFpIl0sImVudiI6eyJBTlRIUk9QSUNfQVBJX0tFWSI6IllPVVJfQU5USFJPUElDX0FQSV9LRVlfSEVSRSIsIlBFUlBMRVhJVFlfQVBJX0tFWSI6IllPVVJfUEVSUExFWElUWV9BUElfS0VZX0hFUkUiLCJPUEVOQUlfQVBJX0tFWSI6IllPVVJfT1BFTkFJX0tFWV9IRVJFIiwiR09PR0xFX0FQSV9LRVkiOiJZT1VSX0dPT0dMRV9LRVlfSEVSRSIsIk1JU1RSQUxfQVBJX0tFWSI6IllPVVJfTUlTVFJBTF9LRVlfSEVSRSIsIk9QRU5ST1VURVJfQVBJX0tFWSI6IllPVVJfT1BFTlJPVVRFUl9LRVlfSEVSRSIsIlhBSV9BUElfS0VZIjoiWU9VUl9YQUlfS0VZX0hFUkUiLCJBWlVSRV9PUEVOQUJFX0FQSV9LRVkiOiJZT1VSX0FaVVJFX0tFWV9IRVJFIiwiT0xMQU1BX0FQSV9LRVkiOiJZT1VSX09MTEFNQV9BUElfS0VZX0hFUkUifX0%3D)

> **Note:** After clicking the install button, you'll still need to add your API keys to the configuration. The button installs the MCP server with placeholder keys that you'll need to replace with your actual API keys.

##### Manual Configuration

###### Cursor & Windsurf (`mcpServers`)

```jsonc
{
  "mcpServers": {
    "taskmaster-ai": {
      "command": "npx",
      "args": ["-y", "--package=task-master-ai", "task-master-ai"],
      "env": {
        "ANTHROPIC_API_KEY": "YOUR_ANTHROPIC_API_KEY_HERE",
        "PERPLEXITY_API_KEY": "YOUR_PERPLEXITY_API_KEY_HERE",
        "OPENAI_API_KEY": "YOUR_OPENAI_KEY_HERE",
        "GOOGLE_API_KEY": "YOUR_GOOGLE_KEY_HERE",
        "MISTRAL_API_KEY": "YOUR_MISTRAL_KEY_HERE",
        "OPENROUTER_API_KEY": "YOUR_OPENROUTER_KEY_HERE",
        "XAI_API_KEY": "YOUR_XAI_KEY_HERE",
        "AZURE_OPENAI_API_KEY": "YOUR_AZURE_KEY_HERE",
        "OLLAMA_API_KEY": "YOUR_OLLAMA_API_KEY_HERE",
      },
    },
  },
}
```

> 🔑 Replace `YOUR_…_KEY_HERE` with your real API keys. You can remove keys you don't use.

###### VS Code (`servers` + `type`)

```jsonc
{
  "servers": {
    "taskmaster-ai": {
      "command": "npx",
      "args": ["-y", "--package=task-master-ai", "task-master-ai"],
      "env": {
        "ANTHROPIC_API_KEY": "YOUR_ANTHROPIC_API_KEY_HERE",
        "PERPLEXITY_API_KEY": "YOUR_PERPLEXITY_API_KEY_HERE",
        "OPENAI_API_KEY": "YOUR_OPENAI_KEY_HERE",
        "GOOGLE_API_KEY": "YOUR_GOOGLE_KEY_HERE",
        "MISTRAL_API_KEY": "YOUR_MISTRAL_KEY_HERE",
        "OPENROUTER_API_KEY": "YOUR_OPENROUTER_KEY_HERE",
        "XAI_API_KEY": "YOUR_XAI_KEY_HERE",
        "AZURE_OPENAI_API_KEY": "YOUR_AZURE_KEY_HERE",
      },
      "type": "stdio",
    },
  },
}
```

> 🔑 Replace `YOUR_…_KEY_HERE` with your real API keys. You can remove keys you don't use.

#### 2. (Cursor-only) Enable Taskmaster MCP

Open Cursor Settings (Ctrl+Shift+J) ➡ Click on MCP tab on the left ➡ Enable task-master-ai with the toggle

#### 3. (Optional) Configure the models you want to use

In your editor's AI chat pane, say:

```txt
Change the main, research and fallback models to <model_name>, <model_name> and <model_name> respectively.
```

[Table of available models](docs/models.md)

#### 4. Initialize Task Master

In your editor's AI chat pane, say:

```txt
Initialize taskmaster-ai in my project
```

#### 5. Make sure you have a PRD (Recommended)

For **new projects**: Create your PRD at `.taskmaster/docs/prd.txt`  
For **existing projects**: You can use `scripts/prd.txt` or migrate with `task-master migrate`

An example PRD template is available after initialization in `.taskmaster/templates/example_prd.txt`.

> [!NOTE]
> While a PRD is recommended for complex projects, you can always create individual tasks by asking "Can you help me implement [description of what you want to do]?" in chat.

**Always start with a detailed PRD.**

The more detailed your PRD, the better the generated tasks will be.

#### 6. Common Commands

Use your AI assistant to:

- Parse requirements: `Can you parse my PRD at scripts/prd.txt?`
- Plan next step: `What's the next task I should work on?`
- Implement a task: `Can you help me implement task 3?`
- View multiple tasks: `Can you show me tasks 1, 3, and 5?`
- Expand a task: `Can you help me expand task 4?`
- **Research fresh information**: `Research the latest best practices for implementing JWT authentication with Node.js`
- **Research with context**: `Research React Query v5 migration strategies for our current API implementation in src/api.js`

[More examples on how to use Task Master in chat](docs/examples.md)

### Option 2: Using Command Line

#### Installation

```bash
# Install globally
npm install -g task-master-ai

# OR install locally within your project
npm install task-master-ai
```

#### Initialize a new project

```bash
# If installed globally
task-master init

# If installed locally
npx task-master init
```

This will prompt you for project details and set up a new project with the necessary files and structure.

#### Common Commands

```bash
# Initialize a new project
task-master init

# Parse a PRD and generate tasks
task-master parse-prd your-prd.txt

# List all tasks
task-master list

# Show the next task to work on
task-master next

# Show specific task(s) - supports comma-separated IDs
task-master show 1,3,5

# Research fresh information with project context
task-master research "What are the latest best practices for JWT authentication?"

# Generate task files
task-master generate
```

## Documentation

For more detailed information, check out the documentation in the `docs` directory:

- [Configuration Guide](docs/configuration.md) - Set up environment variables and customize Task Master
- [Tutorial](docs/tutorial.md) - Step-by-step guide to getting started with Task Master
- [Command Reference](docs/command-reference.md) - Complete list of all available commands
- [Task Structure](docs/task-structure.md) - Understanding the task format and features
- [Example Interactions](docs/examples.md) - Common Cursor AI interaction examples
- [Migration Guide](docs/migration-guide.md) - Guide to migrating to the new project structure

## Troubleshooting

### If `task-master init` doesn't respond:

Try running it with Node directly:

```bash
node node_modules/claude-task-master/scripts/init.js
```

Or clone the repository and run:

```bash
git clone https://github.com/eyaltoledano/claude-task-master.git
cd claude-task-master
node scripts/init.js
```

## Contributors

<a href="https://github.com/eyaltoledano/claude-task-master/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=eyaltoledano/claude-task-master" alt="Task Master project contributors" />
</a>

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=eyaltoledano/claude-task-master&type=Timeline)](https://www.star-history.com/#eyaltoledano/claude-task-master&Timeline)

## Licensing

Task Master is licensed under the MIT License with Commons Clause. This means you can:

✅ **Allowed**:

- Use Task Master for any purpose (personal, commercial, academic)
- Modify the code
- Distribute copies
- Create and sell products built using Task Master

❌ **Not Allowed**:

- Sell Task Master itself
- Offer Task Master as a hosted service
- Create competing products based on Task Master

See the [LICENSE](LICENSE) file for the complete license text and [licensing details](docs/licensing.md) for more information.

<!-- TASKMASTER_EXPORT_START -->

> 🎯 **Taskmaster Export** - 2025-06-08 03:03:22 UTC
> 📋 Export: with subtasks • Status filter: none
> 🔗 Powered by [Task Master](https://task-master.dev?utm_source=github-readme&utm_medium=readme-export&utm_campaign=claude-task-master&utm_content=task-export-link)

```
╭─────────────────────────────────────────────────────────╮╭─────────────────────────────────────────────────────────╮
│                                                         ││                                                         │
│   Project Dashboard                                     ││   Dependency Status & Next Task                         │
│   Tasks Progress: ███████████░░░░░░░░░ 56%    ││   Dependency Metrics:                                   │
│   56%                                                   ││   • Tasks with no dependencies: 28                      │
│   Done: 52  In Progress: 0  Pending: 37  Blocked: 0     ││   • Tasks ready to work on: 34                          │
│   Deferred: 2  Cancelled: 1                             ││   • Tasks blocked by dependencies: 7                    │
│                                                         ││   • Most depended-on task: #1 (14 dependents)           │
│   Subtasks Progress: ████████████░░░░░░░░     ││   • Avg dependencies per task: 0.9                      │
│   60% 60%                                               ││                                                         │
│   Completed: 279/468  In Progress: 1  Pending: 183      ││   Next Task to Work On:                                 │
│   Blocked: 0  Deferred: 3  Cancelled: 2                 ││   ID: 67 - Add CLI JSON output and Cursor keybin...     │
│                                                         ││   Priority: high  Dependencies: None                    │
│   Priority Breakdown:                                   ││   Complexity: ● 5                                       │
│   • High priority: 25                                   │╰─────────────────────────────────────────────────────────╯
│   • Medium priority: 64                                 │
│   • Low priority: 4                                     │
│                                                         │
╰─────────────────────────────────────────────────────────╯
┌───────────┬──────────────────────────────────────┬─────────────────┬──────────────┬───────────────────────┬───────────┐
│ ID        │ Title                                │ Status          │ Priority     │ Dependencies          │ Complexi… │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 1         │ Implement Task Data Structure        │ ✓ done          │ high         │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 2         │ Develop Command Line Interface Found │ ✓ done          │ high         │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 3         │ Implement Basic Task Operations      │ ✓ done          │ high         │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 4         │ Create Task File Generation System   │ ✓ done          │ medium       │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 4.1       │ └─ Design Task File Template Structu │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 4.2       │ └─ Implement Task File Generation Lo │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 4.3       │ └─ Implement File Naming and Organiz │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 4.4       │ └─ Implement Task File to JSON Synch │ ✓ done          │ -            │ 1, 3, 2               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 4.5       │ └─ Implement Change Detection and Up │ ✓ done          │ -            │ 1, 3, 4, 2            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 5         │ Integrate Anthropic Claude API       │ ✓ done          │ high         │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 5.1       │ └─ Configure API Authentication Syst │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 5.2       │ └─ Develop Prompt Template System    │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 5.3       │ └─ Implement Response Handling and P │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 5.4       │ └─ Build Error Management with Retry │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 5.5       │ └─ Implement Token Usage Tracking    │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 5.6       │ └─ Create Model Parameter Configurat │ ✓ done          │ -            │ 1, 5                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 6         │ Build PRD Parsing System             │ ✓ done          │ high         │ 1, 5                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 6.1       │ └─ Implement PRD File Reading Module │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 6.2       │ └─ Design and Engineer Effective PRD │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 6.3       │ └─ Implement PRD to Task Conversion  │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 6.4       │ └─ Build Intelligent Dependency Infe │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 6.5       │ └─ Implement Priority Assignment Log │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 6.6       │ └─ Implement PRD Chunking for Large  │ ✓ done          │ -            │ 1, 5, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 7         │ Implement Task Expansion with Claude │ ✓ done          │ medium       │ 3, 5                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 7.1       │ └─ Design and Implement Subtask Gene │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 7.2       │ └─ Develop Task Expansion Workflow a │ ✓ done          │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 7.3       │ └─ Implement Context-Aware Expansion │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 7.4       │ └─ Build Parent-Child Relationship M │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 7.5       │ └─ Implement Subtask Regeneration Me │ ✓ done          │ -            │ 1, 2, 4               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 8         │ Develop Implementation Drift Handlin │ ✓ done          │ medium       │ 3, 5, 7               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 8.1       │ └─ Create Task Update Mechanism Base │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 8.2       │ └─ Implement AI-Powered Task Rewriti │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 8.3       │ └─ Build Dependency Chain Update Sys │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 8.4       │ └─ Implement Completed Work Preserva │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 8.5       │ └─ Create Update Analysis and Sugges │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 9         │ Integrate Perplexity API             │ ✓ done          │ low          │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 9.1       │ └─ Implement Perplexity API Authenti │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 9.2       │ └─ Develop Research-Oriented Prompt  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 9.3       │ └─ Create Perplexity Response Handle │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 9.4       │ └─ Implement Claude Fallback Mechani │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 9.5       │ └─ Develop Response Quality Comparis │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 10        │ Create Research-Backed Subtask Gener │ ✓ done          │ low          │ 7, 9                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 10.1       │ └─ Design Domain-Specific Research P │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 10.2       │ └─ Implement Research Query Executio │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 10.3       │ └─ Develop Context Enrichment Pipeli │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 10.4       │ └─ Implement Domain-Specific Knowled │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 10.5       │ └─ Enhance Subtask Generation with T │ ✓ done          │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 10.6       │ └─ Implement Reference and Resource  │ ✓ done          │ -            │ 3, 5                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 11        │ Implement Batch Operations           │ ✓ done          │ medium       │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 11.1       │ └─ Implement Multi-Task Status Updat │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 11.2       │ └─ Develop Bulk Subtask Generation S │ ✓ done          │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 11.3       │ └─ Implement Advanced Task Filtering │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 11.4       │ └─ Create Advanced Dependency Manage │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 11.5       │ └─ Implement Batch Task Prioritizati │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 12        │ Develop Project Initialization Syste │ ✓ done          │ medium       │ 1, 3, 4, 6            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 12.1       │ └─ Create Project Template Structure │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 12.2       │ └─ Implement Interactive Setup Wizar │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 12.3       │ └─ Generate Environment Configuratio │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 12.4       │ └─ Implement Directory Structure Cre │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 12.5       │ └─ Generate Example Tasks.json       │ ✓ done          │ -            │ 6                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 12.6       │ └─ Implement Default Configuration S │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 13        │ Create Cursor Rules Implementation   │ ✓ done          │ medium       │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 13.1       │ └─ Set up .cursor Directory Structur │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 13.2       │ └─ Create dev_workflow.mdc Documenta │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 13.3       │ └─ Implement cursor_rules.mdc        │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 13.4       │ └─ Add self_improve.mdc Documentatio │ ✓ done          │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 13.5       │ └─ Create Cursor AI Integration Docu │ ✓ done          │ -            │ 1, 2, 3, 4            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 14        │ Develop Agent Workflow Guidelines    │ ✓ done          │ medium       │ 13                    │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 14.1       │ └─ Document Task Discovery Workflow  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 14.2       │ └─ Implement Task Selection Algorith │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 14.3       │ └─ Create Implementation Guidance Ge │ ✓ done          │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 14.4       │ └─ Develop Verification Procedure Fr │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 14.5       │ └─ Implement Dynamic Task Prioritiza │ ✓ done          │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 15        │ Optimize Agent Integration with Curs │ ✓ done          │ medium       │ 14                    │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 15.1       │ └─ Document Existing Agent Interacti │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 15.2       │ └─ Enhance Integration Between Curso │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 15.3       │ └─ Optimize Command Responses for Ag │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 15.4       │ └─ Improve Agent Workflow Documentat │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 15.5       │ └─ Add Agent-Specific Features to Ex │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 15.6       │ └─ Create Agent Usage Examples and P │ ✓ done          │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 16        │ Create Configuration Management Syst │ ✓ done          │ high         │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 16.1       │ └─ Implement Environment Variable Lo │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 16.2       │ └─ Implement .env File Support       │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 16.3       │ └─ Implement Configuration Validatio │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 16.4       │ └─ Create Configuration Defaults and │ ✓ done          │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 16.5       │ └─ Create .env.example Template      │ ✓ done          │ -            │ 1, 2, 3, 4            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 16.6       │ └─ Implement Secure API Key Handling │ ✓ done          │ -            │ 1, 2, 3, 4            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 17        │ Implement Comprehensive Logging Syst │ ✓ done          │ medium       │ 16                    │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 17.1       │ └─ Implement Core Logging Framework  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 17.2       │ └─ Implement Configurable Output Des │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 17.3       │ └─ Implement Command and API Interac │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 17.4       │ └─ Implement Error Tracking and Perf │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 17.5       │ └─ Implement Log File Rotation and M │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 18        │ Create Comprehensive User Documentat │ ✓ done          │ medium       │ 1, 3, 4, 5, 6, 7, 11, │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 18.1       │ └─ Create Detailed README with Insta │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 18.2       │ └─ Develop Command Reference Documen │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 18.3       │ └─ Create Configuration and Environm │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 18.4       │ └─ Develop Example Workflows and Use │ ✓ done          │ -            │ 3, 6                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 18.5       │ └─ Create Troubleshooting Guide and  │ ✓ done          │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 18.6       │ └─ Develop API Integration and Exten │ ✓ done          │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 19        │ Implement Error Handling and Recover │ ✓ done          │ high         │ 1, 3, 5, 9, 16, 17    │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 19.1       │ └─ Define Error Message Format and S │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 19.2       │ └─ Implement API Error Handling with │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 19.3       │ └─ Develop File System Error Recover │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 19.4       │ └─ Enhance Data Validation with Deta │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 19.5       │ └─ Implement Command Syntax Error Ha │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 19.6       │ └─ Develop System State Recovery Aft │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 20        │ Create Token Usage Tracking and Cost │ ✓ done          │ medium       │ 5, 9, 17              │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 20.1       │ └─ Implement Token Usage Tracking fo │ ✓ done          │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 20.2       │ └─ Develop Configurable Usage Limits │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 20.3       │ └─ Implement Token Usage Reporting a │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 20.4       │ └─ Optimize Token Usage in Prompts   │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 20.5       │ └─ Develop Token Usage Alert System  │ ✓ done          │ -            │ 2, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 21        │ Refactor dev.js into Modular Compone │ ✓ done          │ high         │ 3, 16, 17             │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 21.1       │ └─ Analyze Current dev.js Structure  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 21.2       │ └─ Create Core Module Structure and  │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 21.3       │ └─ Implement Core Module Functionali │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 21.4       │ └─ Implement Error Handling and Comp │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 21.5       │ └─ Test, Document, and Finalize Modu │ ✓ done          │ -            │ 21.4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 22        │ Create Comprehensive Test Suite for  │ ✓ done          │ high         │ 21                    │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 22.1       │ └─ Set Up Jest Testing Environment   │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 22.2       │ └─ Implement Unit Tests for Core Com │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 22.3       │ └─ Develop Integration and End-to-En │ x deferred      │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23        │ Complete MCP Server Implementation f │ ✓ done          │ medium       │ 22                    │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.1       │ └─ Create Core MCP Server Module and │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.2       │ └─ Implement Context Management Syst │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.3       │ └─ Implement MCP Endpoints and API H │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.6       │ └─ Refactor MCP Server to Leverage M │ ✓ done          │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.8       │ └─ Implement Direct Function Imports │ ✓ done          │ -            │ 23.13                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.9       │ └─ Implement Context Management and  │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.10       │ └─ Enhance Tool Registration and Res │ ✓ done          │ -            │ 1, 23.8               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.11       │ └─ Implement Comprehensive Error Han │ ✓ done          │ -            │ 23.1, 23.3            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.12       │ └─ Implement Structured Logging Syst │ ✓ done          │ -            │ 23.1, 23.3            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.13       │ └─ Create Testing Framework and Test │ ✓ done          │ -            │ 23.1, 23.3            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.14       │ └─ Add MCP.json to the Init Workflow │ ✓ done          │ -            │ 23.1, 23.3            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.15       │ └─ Implement SSE Support for Real-ti │ ✓ done          │ -            │ 23.1, 23.3, 23.11     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.16       │ └─ Implement parse-prd MCP command   │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.17       │ └─ Implement update MCP command      │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.18       │ └─ Implement update-task MCP command │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.19       │ └─ Implement update-subtask MCP comm │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.20       │ └─ Implement generate MCP command    │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.21       │ └─ Implement set-status MCP command  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.22       │ └─ Implement show-task MCP command   │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.23       │ └─ Implement next-task MCP command   │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.24       │ └─ Implement expand-task MCP command │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.25       │ └─ Implement add-task MCP command    │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.26       │ └─ Implement add-subtask MCP command │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.27       │ └─ Implement remove-subtask MCP comm │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.28       │ └─ Implement analyze MCP command     │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.29       │ └─ Implement clear-subtasks MCP comm │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.30       │ └─ Implement expand-all MCP command  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.31       │ └─ Create Core Direct Function Struc │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.32       │ └─ Refactor Existing Direct Function │ ✓ done          │ -            │ 23.31                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.33       │ └─ Implement Naming Convention Stand │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.34       │ └─ Review functionality of all MCP d │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.35       │ └─ Review commands.js to ensure all  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.36       │ └─ Finish setting up addResearch in  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.37       │ └─ Finish setting up addTemplates in │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.38       │ └─ Implement robust project root han │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.39       │ └─ Implement add-dependency MCP comm │ ✓ done          │ -            │ 23.31                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.40       │ └─ Implement remove-dependency MCP c │ ✓ done          │ -            │ 23.31                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.41       │ └─ Implement validate-dependencies M │ ✓ done          │ -            │ 23.31, 23.39, 23.40   │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.42       │ └─ Implement fix-dependencies MCP co │ ✓ done          │ -            │ 23.31, 23.41          │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.43       │ └─ Implement complexity-report MCP c │ ✓ done          │ -            │ 23.31                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.44       │ └─ Implement init MCP command        │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.45       │ └─ Support setting env variables thr │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 23.46       │ └─ adjust rules so it prioritizes mc │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 24        │ Implement AI-Powered Test Generation │ ○ pending       │ high         │ 22                    │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 24.1       │ └─ Create command structure for 'gen │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 24.2       │ └─ Implement AI prompt construction  │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 24.3       │ └─ Implement test file generation an │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 24.4       │ └─ Implement MCP tool integration fo │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 24.5       │ └─ Add testing framework configurati │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 25        │ Implement 'add-subtask' Command for  │ ✓ done          │ medium       │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 25.1       │ └─ Update Data Model to Support Pare │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 25.2       │ └─ Implement Core addSubtask Functio │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 25.3       │ └─ Implement add-subtask Command in  │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 25.4       │ └─ Create Unit Test for add-subtask  │ ✓ done          │ -            │ 2, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 25.5       │ └─ Implement remove-subtask Command  │ ✓ done          │ -            │ 2, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 26        │ Implement Context Foundation for AI  │ ○ pending       │ high         │ 5, 6, 7               │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 26.1       │ └─ Implement --context-file Flag for │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 26.2       │ └─ Implement --context Flag for AI C │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 26.3       │ └─ Implement Cursor Rules Integratio │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 26.4       │ └─ Implement Basic Context File Extr │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 27        │ Implement Context Enhancements for A │ ○ pending       │ high         │ 26                    │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 27.1       │ └─ Implement Code Context Extraction │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 27.2       │ └─ Implement Task History Context In │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 27.3       │ └─ Add PRD Context Integration       │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 27.4       │ └─ Create Standardized Context Forma │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 28        │ Implement Advanced ContextManager Sy │ ○ pending       │ high         │ 26, 27                │ ● 8       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 28.1       │ └─ Implement Core ContextManager Cla │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 28.2       │ └─ Develop Context Optimization Pipe │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 28.3       │ └─ Create Command Interface Enhancem │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 28.4       │ └─ Integrate ContextManager with AI  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 28.5       │ └─ Implement Performance Monitoring  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 29        │ Update Claude 3.7 Sonnet Integration │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 30        │ Enhance parse-prd Command to Support │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 31        │ Add Config Flag Support to task-mast │ ✓ done          │ low          │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32        │ Implement "learn" Command for Automa │ x deferred      │ high         │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.1       │ └─ Create Initial File Structure     │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.2       │ └─ Implement Cursor Path Helper      │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.3       │ └─ Create Chat History Analyzer Base │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.4       │ └─ Implement Chat History Extraction │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.5       │ └─ Create CursorRulesManager Base    │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.6       │ └─ Implement Template Validation     │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.7       │ └─ Add Rule Categorization Logic     │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.8       │ └─ Implement Pattern Analysis        │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.9       │ └─ Create AI Prompt Builder          │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.10       │ └─ Implement Learn Command Core      │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.11       │ └─ Add Auto-trigger Support          │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.12       │ └─ Implement CLI Integration         │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.13       │ └─ Add Progress Logging              │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.14       │ └─ Implement Error Recovery          │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 32.15       │ └─ Add Performance Optimization      │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 33        │ Create and Integrate Windsurf Rules  │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 34        │ Implement updateTask Command for Sin │ ✓ done          │ high         │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 34.1       │ └─ Create updateTaskById function in │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 34.2       │ └─ Implement updateTask command in c │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 34.3       │ └─ Add comprehensive error handling  │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 34.4       │ └─ Write comprehensive tests for upd │ ✓ done          │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 34.5       │ └─ Update CLI documentation and help │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 35        │ Integrate Grok3 API for Research Cap │ x cancelled     │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 36        │ Add Ollama Support for AI Services a │ x deferred      │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 37        │ Add Gemini Support for Main AI Servi │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 38        │ Implement Version Check System with  │ ✓ done          │ high         │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 39        │ Update Project Licensing to Dual Lic │ ✓ done          │ high         │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 39.1       │ └─ Remove MIT License and Create Dua │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 39.2       │ └─ Update Source Code License Header │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 39.3       │ └─ Update Documentation and Create L │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 40        │ Implement 'plan' Command for Task Im │ ○ pending       │ medium       │ None                  │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 40.1       │ └─ Retrieve Task Content             │ ► in-progress   │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 40.2       │ └─ Generate Implementation Plan with │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 40.3       │ └─ Format Plan in XML                │ ○ pending       │ -            │ 2, 40.2               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 40.4       │ └─ Error Handling and Output         │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41        │ Implement Visual Task Dependency Gra │ ○ pending       │ medium       │ None                  │ ● 8       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.1       │ └─ CLI Command Setup                 │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.2       │ └─ Graph Layout Algorithms           │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.3       │ └─ ASCII/Unicode Rendering Engine    │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.4       │ └─ Color Coding Support              │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.5       │ └─ Circular Dependency Detection     │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.6       │ └─ Filtering and Search Functionalit │ ○ pending       │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.7       │ └─ Accessibility Features            │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.8       │ └─ Performance Optimization          │ ○ pending       │ -            │ 2, 3, 4, 5, 6         │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.9       │ └─ Documentation                     │ ○ pending       │ -            │ 1, 2, 3, 4, 5, 6, 7,  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 41.10       │ └─ Testing and Validation            │ ○ pending       │ -            │ 1, 2, 3, 4, 5, 6, 7,  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42        │ Implement MCP-to-MCP Communication P │ ○ pending       │ medium       │ None                  │ ● 9       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-1       │ └─ Define MCP-to-MCP communication p │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-2       │ └─ Implement adapter pattern for MCP │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-3       │ └─ Develop client module for MCP too │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-4       │ └─ Provide reference implementation  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-5       │ └─ Add support for solo/local and mu │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-6       │ └─ Update core modules to support dy │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-7       │ └─ Document protocol and mode-switch │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 42.42-8       │ └─ Update terminology to reflect MCP │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 43        │ Add Research Flag to Add-Task Comman │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44        │ Implement Task Automation with Webho │ ○ pending       │ medium       │ None                  │ ● 8       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44.1       │ └─ Design webhook registration API e │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44.2       │ └─ Implement webhook authentication  │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44.3       │ └─ Create event trigger definition i │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44.4       │ └─ Build event processing and queuin │ ○ pending       │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44.5       │ └─ Develop webhook delivery and retr │ ○ pending       │ -            │ 2, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44.6       │ └─ Implement comprehensive error han │ ○ pending       │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 44.7       │ └─ Create webhook testing and simula │ ○ pending       │ -            │ 3, 5, 6               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 45        │ Implement GitHub Issue Import Featur │ ○ pending       │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 45.1       │ └─ Design GitHub API integration arc │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 45.2       │ └─ Implement GitHub URL parsing and  │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 45.3       │ └─ Develop GitHub API client for iss │ ○ pending       │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 45.4       │ └─ Create task formatter for GitHub  │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 45.5       │ └─ Implement end-to-end import flow  │ ○ pending       │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 46        │ Implement ICE Analysis Command for T │ ○ pending       │ medium       │ None                  │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 46.1       │ └─ Design ICE scoring algorithm      │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 46.2       │ └─ Implement AI integration for ICE  │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 46.3       │ └─ Create report file generator      │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 46.4       │ └─ Implement CLI rendering for ICE a │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 46.5       │ └─ Integrate with existing complexit │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 47        │ Enhance Task Suggestion Actions Card │ ○ pending       │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 47.1       │ └─ Design Task Expansion UI Componen │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 47.2       │ └─ Implement State Management for Ta │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 47.3       │ └─ Build Context Addition Functional │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 47.4       │ └─ Develop Task Management Controls  │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 47.5       │ └─ Integrate with Existing Task Syst │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 47.6       │ └─ Test and Optimize User Experience │ ○ pending       │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 48        │ Refactor Prompts into Centralized St │ ○ pending       │ medium       │ None                  │ ● 4       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 48.1       │ └─ Create prompts directory structur │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 48.2       │ └─ Extract prompts into individual f │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 48.3       │ └─ Update functions to import prompt │ ○ pending       │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 49        │ Implement Code Quality Analysis Comm │ ○ pending       │ medium       │ None                  │ ● 8       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 49.1       │ └─ Design pattern recognition algori │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 49.2       │ └─ Implement best practice verificat │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 49.3       │ └─ Develop AI integration for code a │ ○ pending       │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 49.4       │ └─ Create recommendation generation  │ ○ pending       │ -            │ 2, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 49.5       │ └─ Implement task creation functiona │ ○ pending       │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 49.6       │ └─ Create comprehensive reporting in │ ○ pending       │ -            │ 4, 5                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 50        │ Implement Test Coverage Tracking Sys │ ○ pending       │ medium       │ None                  │ ● 9       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 50.1       │ └─ Design and implement tests.json d │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 50.2       │ └─ Develop coverage report parser an │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 50.3       │ └─ Build coverage tracking and updat │ ○ pending       │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 50.4       │ └─ Implement CLI commands for covera │ ○ pending       │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 50.5       │ └─ Develop AI-powered test generatio │ ○ pending       │ -            │ 1, 2, 3, 4            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51        │ Implement Perplexity Research Comman │ ○ pending       │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.1       │ └─ Create Perplexity API Client Serv │ x cancelled     │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.2       │ └─ Implement Task Context Extraction │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.3       │ └─ Build Research Command CLI Interf │ ○ pending       │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.4       │ └─ Implement Results Processing and  │ ○ pending       │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.5       │ └─ Implement Caching and Results Man │ x cancelled     │ -            │ 1, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.6       │ └─ Implement Project Context Generat │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.7       │ └─ Create REPL Command System        │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 51.8       │ └─ Integrate with AI Services Unifie │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 52        │ Implement Task Suggestion Command fo │ ○ pending       │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 52.1       │ └─ Design data collection mechanism  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 52.2       │ └─ Implement AI integration for task │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 52.3       │ └─ Build interactive CLI interface f │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 52.4       │ └─ Implement suggestion selection an │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 52.5       │ └─ Add configuration options and fla │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 53        │ Implement Subtask Suggestion Feature │ ○ pending       │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 53.1       │ └─ Implement parent task validation  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 53.2       │ └─ Build context gathering mechanism │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 53.3       │ └─ Develop AI suggestion logic for s │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 53.4       │ └─ Create interactive CLI interface  │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 53.5       │ └─ Implement subtask linking functio │ ○ pending       │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 53.6       │ └─ Perform comprehensive testing     │ ○ pending       │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 54        │ Add Research Flag to Add-Task Comman │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 55        │ Implement Positional Arguments Suppo │ ○ pending       │ medium       │ None                  │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 55.1       │ └─ Analyze current CLI argument pars │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 55.2       │ └─ Design positional argument specif │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 55.3       │ └─ Implement core positional argumen │ ○ pending       │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 55.4       │ └─ Handle edge cases and error condi │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 55.5       │ └─ Update documentation and create u │ ○ pending       │ -            │ 2, 3, 4               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 56        │ Refactor Task-Master Files into Node │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 57        │ Enhance Task-Master CLI User Experie │ ○ pending       │ medium       │ None                  │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 57.1       │ └─ Implement Configurable Log Levels │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 57.2       │ └─ Design Terminal Color Scheme and  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 57.3       │ └─ Implement Progress Indicators and │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 57.4       │ └─ Develop Interactive Selection Men │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 57.5       │ └─ Design Tabular and Structured Out │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 57.6       │ └─ Create Help System and Interactiv │ ○ pending       │ -            │ 2, 4, 5               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 58        │ Implement Elegant Package Update Mec │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 59        │ Remove Manual Package.json Modificat │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 59.1       │ └─ Conduct Code Audit for Dependency │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 59.2       │ └─ Remove Manual Dependency Modifica │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 59.3       │ └─ Update npm Dependencies           │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 59.4       │ └─ Update Initialization and Install │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 59.5       │ └─ Update Documentation              │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 59.6       │ └─ Perform Regression Testing        │ ✓ done          │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60        │ Implement Mentor System with Round-T │ ○ pending       │ medium       │ None                  │ ● 8       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60.1       │ └─ Design Mentor System Architecture │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60.2       │ └─ Implement Mentor Profile Manageme │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60.3       │ └─ Develop Round-Table Discussion Fr │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60.4       │ └─ Implement LLM Integration for AI  │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60.5       │ └─ Build Discussion Output Formatter │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60.6       │ └─ Integrate Mentor System with Task │ ○ pending       │ -            │ 2, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 60.7       │ └─ Test and Optimize Round-Table Dis │ ○ pending       │ -            │ 4, 5, 6               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61        │ Implement Flexible AI Model Manageme │ ✓ done          │ high         │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.1       │ └─ Create Configuration Management M │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.2       │ └─ Implement CLI Command Parser for  │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.3       │ └─ Integrate Vercel AI SDK and Creat │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.4       │ └─ Develop Centralized AI Services M │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.5       │ └─ Implement Environment Variable Ma │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.6       │ └─ Implement Model Listing Command   │ ✓ done          │ -            │ 1, 2, 4               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.7       │ └─ Implement Model Setting Commands  │ ✓ done          │ -            │ 1, 2, 4, 6            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.8       │ └─ Update Main Task Processing Logic │ ✓ done          │ -            │ 4, 5, 61.18           │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.9       │ └─ Update Research Processing Logic  │ ✓ done          │ -            │ 4, 5, 8, 61.18        │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.10       │ └─ Create Comprehensive Documentatio │ ✓ done          │ -            │ 6, 7, 8, 9            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.11       │ └─ Refactor PRD Parsing to use gener │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.12       │ └─ Refactor Basic Subtask Generation │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.13       │ └─ Refactor Research Subtask Generat │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.14       │ └─ Refactor Research Task Descriptio │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.15       │ └─ Refactor Complexity Analysis AI C │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.16       │ └─ Refactor Task Addition AI Call to │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.17       │ └─ Refactor General Chat/Update AI C │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.18       │ └─ Refactor Callers of AI Parsing Ut │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.19       │ └─ Refactor `updateSubtaskById` AI C │ ✓ done          │ -            │ 61.23                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.20       │ └─ Implement `anthropic.js` Provider │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.21       │ └─ Implement `perplexity.js` Provide │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.22       │ └─ Implement `openai.js` Provider Mo │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.23       │ └─ Implement Conditional Provider Lo │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.24       │ └─ Implement `google.js` Provider Mo │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.25       │ └─ Implement `ollama.js` Provider Mo │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.26       │ └─ Implement `mistral.js` Provider M │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.27       │ └─ Implement `azure.js` Provider Mod │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.28       │ └─ Implement `openrouter.js` Provide │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.29       │ └─ Implement `xai.js` Provider Modul │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.30       │ └─ Update Configuration Management f │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.31       │ └─ Implement Integration Tests for U │ ✓ done          │ -            │ 61.18                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.32       │ └─ Update Documentation for New AI A │ ✓ done          │ -            │ 61.31                 │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.33       │ └─ Cleanup Old AI Service Files      │ ✓ done          │ -            │ 61.31, 61.32          │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.34       │ └─ Audit and Standardize Env Variabl │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.35       │ └─ Refactor add-task.js for Unified  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.36       │ └─ Refactor analyze-task-complexity. │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.37       │ └─ Refactor expand-task.js for Unifi │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.38       │ └─ Refactor expand-all-tasks.js for  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.39       │ └─ Refactor get-subtasks-from-ai.js  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.40       │ └─ Refactor update-task-by-id.js for │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.41       │ └─ Refactor update-tasks.js for Unif │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.42       │ └─ Remove all unused imports         │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.43       │ └─ Remove all unnecessary console lo │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.44       │ └─ Add setters for temperature, max  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 61.45       │ └─ Add support for Bedrock provider  │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62        │ Add --simple Flag to Update Commands │ ○ pending       │ medium       │ None                  │ ● 4       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.1       │ └─ Update command parsers to recogni │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.2       │ └─ Implement conditional logic to by │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.3       │ └─ Format user input with timestamp  │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.4       │ └─ Add visual indicator for manual u │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.5       │ └─ Implement storage of simple updat │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.6       │ └─ Update help documentation for the │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.7       │ └─ Implement integration tests for t │ ○ pending       │ -            │ 1, 2, 3, 4, 5         │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 62.8       │ └─ Perform final validation and docu │ ○ pending       │ -            │ 1, 2, 3, 4, 5, 6, 7   │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63        │ Add pnpm Support for the Taskmaster  │ ✓ done          │ medium       │ None                  │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.1       │ └─ Update Documentation for pnpm Sup │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.2       │ └─ Ensure Package Scripts Compatibil │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.3       │ └─ Generate and Validate pnpm Lockfi │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.4       │ └─ Test Taskmaster Installation and  │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.5       │ └─ Integrate pnpm into CI/CD Pipelin │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.6       │ └─ Verify Installation UI/Website Co │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.7       │ └─ Test init.js Script with pnpm     │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 63.8       │ └─ Verify Binary Links with pnpm     │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64        │ Add Yarn Support for Taskmaster Inst │ ✓ done          │ medium       │ None                  │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.1       │ └─ Update package.json for Yarn Comp │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.2       │ └─ Add Yarn-Specific Configuration F │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.3       │ └─ Test and Fix Yarn Compatibility f │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.4       │ └─ Update Documentation for Yarn Ins │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.5       │ └─ Implement and Test Package Manage │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.6       │ └─ Verify Installation UI/Website Co │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.7       │ └─ Test init.js Script with Yarn     │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.8       │ └─ Verify Binary Links with Yarn     │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 64.9       │ └─ Test Website Account Setup with Y │ ✓ done          │ -            │ 6                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 65        │ Add Bun Support for Taskmaster Insta │ ✓ done          │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 65.1       │ └─ Research Bun compatibility requir │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 65.2       │ └─ Update installation scripts for B │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 65.3       │ └─ Create Bun-specific installation  │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 65.4       │ └─ Test Taskmaster installation with │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 65.5       │ └─ Test Taskmaster operation with Bu │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 65.6       │ └─ Update documentation for Bun supp │ ✓ done          │ -            │ 4, 5                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 66        │ Support Status Filtering in Show Com │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 67        │ Add CLI JSON output and Cursor keybi │ ○ pending       │ high         │ None                  │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 67.1       │ └─ Implement Core JSON Output Logic  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 67.2       │ └─ Extend JSON Output to All Relevan │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 67.3       │ └─ Create `install-keybindings` Comm │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 67.4       │ └─ Implement Keybinding File Handlin │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 67.5       │ └─ Add Taskmaster Keybindings, Preve │ ○ pending       │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 68        │ Ability to create tasks without pars │ ✓ done          │ medium       │ None                  │ ● 3       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 68.1       │ └─ Design task creation form without │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 68.2       │ └─ Implement task saving functionali │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 69        │ Enhance Analyze Complexity for Speci │ ✓ done          │ medium       │ None                  │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 69.1       │ └─ Modify core complexity analysis l │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 69.2       │ └─ Update CLI interface for task-spe │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 69.3       │ └─ Integrate task-specific analysis  │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 69.4       │ └─ Create comprehensive tests for ta │ ✓ done          │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 70        │ Implement 'diagram' command for Merm │ ○ pending       │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 70.1       │ └─ Design the 'diagram' command inte │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 70.2       │ └─ Implement Mermaid diagram generat │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 70.3       │ └─ Develop output handling mechanism │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 70.4       │ └─ Create documentation and examples │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 71        │ Add Model-Specific maxTokens Overrid │ ✓ done          │ high         │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 72        │ Implement PDF Generation for Project │ ○ pending       │ medium       │ None                  │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 72.1       │ └─ Research and select PDF generatio │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 72.2       │ └─ Design PDF template and layout    │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 72.3       │ └─ Implement project progress data c │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 72.4       │ └─ Integrate with dependency visuali │ ○ pending       │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 72.5       │ └─ Build PDF generation core functio │ ○ pending       │ -            │ 2, 3, 4               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 72.6       │ └─ Create export options and command │ ○ pending       │ -            │ 5                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 73        │ Implement Custom Model ID Support fo │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 74        │ PR Review: better-model-management   │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 74.1       │ └─ pull out logWrapper into utils    │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 75        │ Integrate Google Search Grounding fo │ ○ pending       │ medium       │ None                  │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 75.1       │ └─ Modify AI service layer to suppor │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 75.2       │ └─ Implement conditional logic for r │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 75.3       │ └─ Update supported models configura │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 75.4       │ └─ Create end-to-end testing suite f │ ○ pending       │ -            │ 1, 2, 3               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76        │ Develop E2E Test Framework for Taskm │ ○ pending       │ high         │ None                  │ ● 8       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76.1       │ └─ Design E2E Test Framework Archite │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76.2       │ └─ Implement FastMCP Server Launcher │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76.3       │ └─ Develop Message Protocol Handler  │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76.4       │ └─ Create Request/Response Correlati │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76.5       │ └─ Build Test Assertion Framework    │ ○ pending       │ -            │ 3, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76.6       │ └─ Implement Test Cases              │ ○ pending       │ -            │ 2, 4, 5               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 76.7       │ └─ Create CI Integration and Documen │ ○ pending       │ -            │ 6                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77        │ Implement AI Usage Telemetry for Tas │ ✓ done          │ medium       │ None                  │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.1       │ └─ Implement telemetry utility and d │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.2       │ └─ Implement secure telemetry transm │ x deferred      │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.3       │ └─ Develop user consent and privacy  │ x deferred      │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.4       │ └─ Integrate telemetry into Taskmast │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.5       │ └─ Implement usage summary display   │ ✓ done          │ -            │ 1, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.6       │ └─ Telemetry Integration for parse-p │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.7       │ └─ Telemetry Integration for expand- │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.8       │ └─ Telemetry Integration for expand- │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.9       │ └─ Telemetry Integration for update- │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.10       │ └─ Telemetry Integration for update- │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.11       │ └─ Telemetry Integration for update- │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.12       │ └─ Telemetry Integration for analyze │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.13       │ └─ Update google.js for Telemetry Co │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.14       │ └─ Update openai.js for Telemetry Co │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.15       │ └─ Update openrouter.js for Telemetr │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.16       │ └─ Update perplexity.js for Telemetr │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.17       │ └─ Update xai.js for Telemetry Compa │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 77.18       │ └─ Create dedicated telemetry transm │ ✓ done          │ -            │ 1, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 80        │ Implement Unique User ID Generation  │ ○ pending       │ medium       │ None                  │ ● 4       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 80.1       │ └─ Create post-install script struct │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 80.2       │ └─ Implement UUID generation functio │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 80.3       │ └─ Develop config file handling logi │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 80.4       │ └─ Integrate user ID generation with │ ○ pending       │ -            │ 2, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 80.5       │ └─ Add documentation and telemetry s │ ○ pending       │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 82        │ Update supported-models.json with to │ ○ pending       │ high         │ None                  │ ● 3       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 83        │ Update config-manager.js defaults an │ ○ pending       │ high         │ 82                    │ ● 4       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 83.1       │ └─ Update config-manager.js with spe │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 84        │ Implement token counting utility     │ ○ pending       │ high         │ 82                    │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 85        │ Update ai-services-unified.js for dy │ ○ pending       │ medium       │ 83, 84                │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 86        │ Update .taskmasterconfig schema and  │ ○ pending       │ medium       │ 83                    │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 87        │ Implement validation and error handl │ ○ pending       │ low          │ 85                    │ ● 5       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 88        │ Enhance Add-Task Functionality to Co │ ✓ done          │ medium       │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 88.1       │ └─ Review Current Add-Task Implement │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 88.2       │ └─ Modify Add-Task to Recursively An │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 88.3       │ └─ Ensure Correct Order of Dependenc │ ✓ done          │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 88.4       │ └─ Integrate with Existing Validatio │ ✓ done          │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 88.5       │ └─ Optimize Performance for Large Pr │ ✓ done          │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 89        │ Introduce Prioritize Command with En │ ○ pending       │ medium       │ None                  │ ● 6       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 90        │ Implement Subtask Progress Analyzer  │ ○ pending       │ medium       │ 1, 3                  │ ● 8       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 91        │ Implement Move Command for Tasks and │ ✓ done          │ medium       │ 1, 3                  │ ● 7       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 91.1       │ └─ Design and implement core move lo │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 91.2       │ └─ Implement edge case handling      │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 91.3       │ └─ Update CLI interface for move com │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 91.4       │ └─ Ensure data integrity during move │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 91.5       │ └─ Create comprehensive test suite   │ ✓ done          │ -            │ 1, 2, 3, 4            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 91.6       │ └─ Export and integrate the move fun │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92        │ Implement Project Root Environment V │ ? review        │ medium       │ 1, 3, 17              │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.1       │ └─ Update configuration loader to ch │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.2       │ └─ Add support for 'projectRoot' in  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.3       │ └─ Refactor project root resolution  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.4       │ └─ Update all MCP tools to use the n │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.5       │ └─ Add comprehensive tests for the n │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.6       │ └─ Update documentation with new con │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.7       │ └─ Implement validation for project  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 92.8       │ └─ Implement support for loading env │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 93        │ Implement Google Vertex AI Provider  │ ○ pending       │ medium       │ 19, 94                │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 93.1       │ └─ Create Google Vertex AI Provider  │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 93.2       │ └─ Integrate Vercel AI SDK Google Ve │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 93.3       │ └─ Implement Provider Interface Meth │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 93.4       │ └─ Handle Vertex AI Configuration an │ ○ pending       │ -            │ 3                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 93.5       │ └─ Update Exports, Documentation, an │ ○ pending       │ -            │ 4                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 94        │ Implement Azure OpenAI Provider Inte │ ✓ done          │ medium       │ 19, 26                │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 94.1       │ └─ Create Azure Provider Class       │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 94.2       │ └─ Implement Configuration Managemen │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 94.3       │ └─ Update Provider Integration       │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 94.4       │ └─ Implement Azure-Specific Error Ha │ ✓ done          │ -            │ 1, 2                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 94.5       │ └─ Update Documentation              │ ✓ done          │ -            │ 1, 2, 3, 4            │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95        │ Implement .taskmaster Directory Stru │ ✓ done          │ high         │ 1, 3, 4, 17           │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.1       │ └─ Create .taskmaster directory stru │ ✓ done          │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.2       │ └─ Update Task Master code for new u │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.3       │ └─ Update task file generation syste │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.4       │ └─ Implement backward compatibility  │ ✓ done          │ -            │ 2, 3                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.5       │ └─ Create migration command for user │ ✓ done          │ -            │ 1, 4                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.6       │ └─ Update project initialization pro │ ✓ done          │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.7       │ └─ Update PRD and report file handli │ ✓ done          │ -            │ 2, 6                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.8       │ └─ Update documentation and create m │ ✓ done          │ -            │ 5, 6, 7               │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.9       │ └─ Add templates directory support   │ ✓ done          │ -            │ 2, 6                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 95.10       │ └─ Verify clean user project directo │ ✓ done          │ -            │ 8, 9                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 96        │ Create Export Command for On-Demand  │ ○ pending       │ medium       │ 2, 4, 95              │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 96.1       │ └─ Remove Automatic Task File Genera │ ○ pending       │ -            │ None                  │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 96.2       │ └─ Implement Export Command Infrastr │ ○ pending       │ -            │ 1                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 96.3       │ └─ Implement Comprehensive PDF Expor │ ○ pending       │ -            │ 2                     │ N/A       │
├───────────┼──────────────────────────────────────┼─────────────────┼──────────────┼───────────────────────┼───────────┤
│ 96.4       │ └─ Update Documentation, Tests, and  │ ○ pending       │ -            │ 2, 3                  │ N/A       │
└───────────┴──────────────────────────────────────┴─────────────────┴──────────────┴───────────────────────┴───────────┘
```

╭────────────────────────────────────────────── ⚡ RECOMMENDED NEXT TASK ⚡ ──────────────────────────────────────────────╮
│ │
│ 🔥 Next Task to Work On: #67 - Add CLI JSON output and Cursor keybindings integration │
│ │
│ Priority: high Status: ○ pending │
│ Dependencies: None │
│ │
│ Description: Enhance Taskmaster CLI with JSON output option and add a new command to install pre-configured Cursor keybindings │
│ │
│ Subtasks: │
│ 67.1 [pending] Implement Core JSON Output Logic for `next` and `show` Commands │
│ 67.2 [pending] Extend JSON Output to All Relevant Commands and Ensure Schema Consistency │
│ 67.3 [pending] Create `install-keybindings` Command Structure and OS Detection │
│ 67.4 [pending] Implement Keybinding File Handling and Backup Logic │
│ 67.5 [pending] Add Taskmaster Keybindings, Prevent Duplicates, and Support Customization │
│ │
│ Start working: task-master set-status --id=67 --status=in-progress │
│ View details: task-master show 67 │
│ │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯

╭──────────────────────────────────────────────────────────────────────────────────────╮
│ │
│ Suggested Next Steps: │
│ │
│ 1. Run task-master next to see what to work on next │
│ 2. Run task-master expand --id=<id> to break down a task into subtasks │
│ 3. Run task-master set-status --id=<id> --status=done to mark a task as complete │
│ │
╰──────────────────────────────────────────────────────────────────────────────────────╯

> 📋 **End of Taskmaster Export** - Tasks are synced from your project using the `sync-readme` command.

<!-- TASKMASTER_EXPORT_END -->
