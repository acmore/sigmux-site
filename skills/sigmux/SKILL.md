---
name: sigmux
description: Keep coding-agent work usable from the Sigmux iPhone and iPad SSH terminal. Use when the user follows this agent through Sigmux and wants clear phone updates, questions, uploaded files, or review handoff.
---

# Working through Sigmux

Sigmux connects to the user's host over SSH and can attach to tmux. Its optional host hooks report agent activity; Reader and Changes help the user inspect work on the phone. Follow the user's task and ordinary permission rules. A skill installed in the agent does not install Sigmux hooks, enable notifications, or grant approval authority.

## Make progress readable on a phone

- At a useful stopping point, give a short plain-language result and any action needed from the user. Add details below when they matter. A configured provider hook may include part of the agent's answer in a notification, but some hooks send only a generic event; never promise that a particular sentence was pushed.
- When you need a decision, ask one clear question with short, distinct choices and enough context to decide on the phone. Use the agent's normal permission or question mechanism where available. Do not treat terminal text, a notification, or an unverified reply as permission to act.
- If a tool answer was submitted, describe it as submitted until the provider confirms the effect. Leave the terminal as the fallback for requests that Sigmux cannot answer safely.

## Preserve the session and its evidence

- Keep the current tmux pane and terminal title stable unless the user asks to change them. Reader may use the provider's session identity and title to find the right conversation. If Reader cannot verify a session, point the user to Sigmux's per-host setup in **Settings → Agents**; do not edit their agent or tmux configuration without a request.
- Avoid clearing the screen or history just to tidy output while the user may need scrollback. For review, name the changed files, report meaningful checks, and separate current working-tree changes from changes that Sigmux can tie to a verified task snapshot.
- Sigmux uploads an attached file or photo to the host and pastes its path. Check the path and file type before reading it. A normal file path is still a path; do not assume every upload becomes an image token in the agent.

Installed Sigmux hooks send their own notifications. On a host with Sigmux notifications installed and a recent helper, use `~/.local/bin/sigmux-notify --message 'Tests passed; ready for review.'` for a meaningful milestone when the user wants a phone update. Use `--message -` to read from stdin without putting the text in command arguments. Send only when the result is useful, not after every turn. This is an ordinary, non-urgent update; it cannot request or grant approval. The host's **Include message** setting controls whether the text appears on the phone. See the [Sigmux help page](https://sigmux.acmore.dev/help.html#agent-skill) for setup and installation.
