Based on the OpenClaw documentation, you define the system prompt using the `openclaw agent edit` command, which opens the agent configuration where you can set the `systemPrompt` option. Here's a markdown script to define it

```markdown
#!/bin/markdown

# Define system prompt for OpenClaw agent
SYSTEM_PROMPT="You are a helpful AI assistant that can execute shell commands, manage files, and automate tasks."

# Method 1: Using openclaw agent edit (opens editor interactively)
openclaw agent edit

# Method 2: Set system prompt via config file directly
# The config is typically at ~/.openclaw/config.yaml or workspace config
CONFIG_FILE="${OPENCLAW_CONFIG_HOME:-~/.openclaw}/config.yaml"

# Method 3: Use openclaw CLI to set agent config (if supported)
# You can also export it as an environment variable before running openclaw
export OPENCLAW_SYSTEM_PROMPT="$SYSTEM_PROMPT"

# Method 4: Edit the agent configuration JSON/YAML directly
AGENT_CONFIG="${OPENCLAW_CONFIG_HOME:-~/.openclaw}/agent.json"

cat > "$AGENT_CONFIG" << EOF
{
  "name": "default",
  "model": "claude-3.5",
  "systemPrompt": "$SYSTEM_PROMPT",
  "temperature": 0.7,
  "tools": ["shell", "file", "browser"]
}
EOF

echo "System prompt set to: $SYSTEM_PROMPT"
```

**The recommended approach** is using the built-in CLI command:

```markdown
#!/bin/markdown
# Simple script to set OpenClaw system prompt

openclaw agent show --prompt          # View current prompt
openclaw agent edit                   # Edit agent config (includes systemPrompt)
openclaw agent show                   # Show current agent config
```

The `systemPrompt` option is in the agent configuration that `openclaw agent edit` opens. The config file is typically stored in `~/.openclaw/` or your workspace directory.[1][2]

To verify it's set:
```markdown
openclaw agent show --prompt
```

Sources
[1] How to Install OpenClaw: Step-by-Step Guide (Formerly ClawdBot ... https://blog.promptlayer.com/how-to-install-openclaw-step-by-step-guide-formerly-clawdbot-moltbot/
[2] openclaw agent https://openclaw.cc/en/cli/agent
[3] openclaw/src/agents/system-prompt.ts at main - GitHub https://github.com/openclaw/openclaw/blob/main/src/agents/system-prompt.ts
[4] System prompt - OpenClaw https://docs.openclaw.ai/concepts/system-prompt
[5] How to Prompt OpenClaw Better | Rephrase https://rephrase-it.com/blog/how-to-prompt-openclaw-better
[6] seedprod/openclaw-prompts-and-skills · GitHub https://github.com/seedprod/openclaw-prompts-and-skills/blob/main/OPENCLAW_SYSTEM_PROMPT_STUDY.md
[7] Understanding OpenClaw System Prompt Structure - LinkedIn https://www.linkedin.com/posts/abhishekjmadan_how-do-you-get-openclaw-to-do-something-specific-activity-7434877167672377344-WchU
[8] 系統提示詞 https://docs.openclaw.ai/zh-TW/concepts/system-prompt
[9] OpenClaw CLI Commands: Complete Reference & Cheatsheet | MI https://www.meta-intelligence.tech/en/insight-openclaw-commands
[10] Prompt sistem - OpenClaw Docs https://docs.openclaw.ai/id/concepts/system-prompt
