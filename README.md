# Game Assets Maker Skills

用于 Game Assets Maker 的六个 Agent Skills：写角色和动作提示词、操作客户端、处理素材，并将动画导入 Godot 4。

## 安装

安装工具需要 Node.js/npm。以下命令安装全部六个 Skills。

```bash
# Codex
npx skills add hyhy111/gam-skills -g -a codex --skill "*"

# Claude Code
npx skills add hyhy111/gam-skills -g -a claude-code --skill "*"

# 自动检测并选择其他 Agent
npx skills add hyhy111/gam-skills -g --skill "*"
```

其他常用工具可将 `-a` 参数改为 `cursor`、`opencode`、`gemini-cli`、`github-copilot`、`cline`、`kimi-code-cli`、`zcode`、`trae-cn`、`qwen-code` 或 `windsurf`。完整列表见 [Skills CLI](https://github.com/vercel-labs/skills#supported-agents)。

## 包含的 Skills

| Skill | 用途 |
| --- | --- |
| `gam-pic-prompt` | 将角色想法写成图片提示词，明确视角与画风。 |
| `gam-video-prompt` | 根据角色图编写待机、行走、攻击等动作提示词。 |
| `gam-workflow` | 安排制作步骤，检查结果，继续处理素材。 |
| `gam-guide` | 查功能、问参数，了解账号与 API Key 配置。 |
| `gam-cli` | 调用 `gam-agent` 填写草稿、查询任务、操作客户端。 |
| `gam-export` | 将 PNG 动画帧、裁剪偏移和音效导入 Godot 4。 |

## 使用

安装后，在 Agent 对话中说明想做什么，也可以带上 Skill 名称，例如：

- “用 gam-pic-prompt，帮我写一个侧视鸭鸭剑士的图片提示词。”
- “把这段视频处理成游戏动画素材。”
- “用 gam-export，把这个素材目录导入我的 Godot 4 项目。”

操作客户端需要先安装并打开 [Game Assets Maker](https://github.com/hyhy111/game-assets-maker)，并允许 Agent 访问本地文件、执行命令。安装包自带 `gam-agent`，固定入口为 macOS 的 `~/.gam/gam-agent`，或 Windows 的 `%USERPROFILE%\.gam\gam-agent.cmd`；设置 `GAM_DATA_ROOT` 时使用该目录。

`gam-export` 另行运行本 Skill 内的 Python 脚本，需要 Python 3.10 或更新版本，只依赖标准库。Agent 可检测并按需处理 Python 环境；导出时提供素材目录和 Godot 4 项目目录。仅处理本地素材无需登录；在线 AI 生成沿用客户端中的账号或自定义 Key 配置。

## 在客户端仓库内维护

本仓库作为客户端的 `.agents/skills` 子模块使用，目录中直接包含各个 `gam-*` Skill，脚本、参考资料和 Godot 资源随 Skill 一起分发。

```bash
# 克隆客户端时一起获取 Skills
git clone --recurse-submodules https://github.com/hyhy111/game-assets-maker.git

# 已有客户端检出：按主仓库记录的版本初始化
git submodule update --init -- .agents/skills
```

在子仓库中修改、验证、提交并推送所需内容，然后回到客户端仓库更新 `.agents/skills` 指针。不要使用 `git add .` 混入其他待处理文件；已有未提交改动需保留。

导出脚本检查：

```bash
python3 gam-export/tests/test_generate.py
```

## English

Six reusable skills for Game Assets Maker: write image/video prompts, guide the asset workflow, control the desktop app through `gam-agent`, and export animation frames, offsets, and audio to Godot 4.

Install with either command above. The Skills installer needs Node.js/npm. Local client operations need an installed Game Assets Maker app and local command/file access. Godot export uses the skill's script with Python 3.10+ and its standard library; your agent can check the Python environment as needed.

The client keeps this repository at `.agents/skills` as a Git submodule. Commit and push Skills independently, then update the client's recorded submodule commit.

## License

MIT. See [LICENSE](LICENSE).
