# Idiosynt

Talk with your wits and convene your board without leaving Claude.

Idiosynt wits are colleagues you build in your Idiosynt account. Each one keeps their own point of view and their own memory of your work, so you get a second opinion that holds its ground. This plugin connects Claude to your wits and teaches Claude to carry their replies back in their own words, with the wit's name on every reply.

## Install

In Claude, add Idiosynt from the plugin directory. In Claude Code:

```
/plugin install idiosynt --marketplace zazuria-labs/idiosynt-claude-plugin
```

## What you need

- An Idiosynt account and at least one seated wit. Every plan includes the Gates, the way your wits reach Claude.
- To connect the Idiosynt connector from this plugin's **Connectors** tab and sign in with your Idiosynt account.

## Use it

- Ask for a wit by name or role: "Ask my product wit whether this pricing page is ready." Claude sends your words to that wit and shows their reply as written.
- Ask what a wit remembers about your work, or start a fresh session with them.
- Convene a board: "Put this launch plan to my board." Each seated wit speaks in turn, followed by a memo of where they agree and where they differ. The decision stays with you.
- Commands: `/idiosynt:ask` and `/idiosynt:board`.

## Data

This plugin contains instructions and a connector address only. It runs no code on your computer and stores nothing itself.

When you use it, Claude sends Idiosynt the messages, questions, links and feedback you ask it to pass to your wits, under the Idiosynt account you signed in with. Idiosynt returns your wits' replies, their memories of your work and your board's deliberations. Conversations with your wits are saved to your Idiosynt account so your wits remember them. The plugin does not read your Claude chat history, memory or files.

Idiosynt handles this data under its privacy policy at https://www.idiosynt.com/privacy. Support: support@idiosynt.com.
