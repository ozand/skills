# Explain Clearly

[English](README.md) · [Русский](README.ru.md)

This skill helps AI give clearer answers: instead of saying “cache error”, explain why you might see an old picture. And when the cause is uncertain, say so rather than presenting a guess as fact.

## What it can help with

Use it when you want an explanation in plainer language, less jargon, a different level of detail, or wording tailored to a particular audience. It can be useful for both technical subjects and everyday questions. The aim is not simply to shorten an answer, but to help a reader form an accurate picture of what is known and what is not.

For example, instead of: “The browser cache served a stale asset.”

> Your browser may have saved an earlier copy of the picture and reused it instead of downloading the replacement. Those saved files are called the browser cache. Clearing them can make the browser download the picture again, but it will not fix an image that is wrong on the site itself.

This fictional example explains the term and limits the proposed fix to one possible cause. More examples are in [references/examples.md](references/examples.md).

## Limits

This skill is guidance, not a fact-checker or a guarantee of clarity, correctness, or comprehension. It cannot establish that a person understood an answer. The agent still needs to use reliable information and appropriate judgment; review consequential explanations. It does not automatically apply to every question or work in every agent. See [references/sources.md](references/sources.md) for the practitioner sources and their limits.

## Practical use

For a one-off request, give your agent access to this directory or its [`SKILL.md`](SKILL.md), if it can read repository files, and ask it to use the `explain-clearly` skill. For repeated use, check your agent's documentation for its supported skill format and user-wide or project-local skill directory, then place the entire `explain-clearly` directory there without overwriting an existing one. Follow that agent's instructions to reload or start a session, and verify the skill is available. There is no single installation path or activation command shared by all agents: an installed skill's availability and whether it is loaded or selected depend on the agent and its configuration; copying files alone does not prove activation.

### Install for Pi

Pi discovers skills in `~/.agents/skills/` (user-wide) and `.agents/skills/` (project-local). Copy the **entire** `skills/explain-clearly/` directory, including `SKILL.md`, `references/`, and its license. Run these commands from the root of this repository. The user-wide version is:

```sh
mkdir -p ~/.agents/skills
if [ ! -e ~/.agents/skills/explain-clearly ]; then
  cp -R skills/explain-clearly ~/.agents/skills/explain-clearly
else
  echo 'Destination exists; compare contents and get permission before replacing.' >&2
  exit 1
fi
```

For a project-only installation, use `.agents/skills/` instead of `~/.agents/skills/` in both commands. If the destination already exists, do not overwrite it; inspect the files and resolve any name collision deliberately. An installed skill is not necessarily loaded into an active session: after edits, Pi documents `/reload` for reloading, and a fresh session also loads skills. Verify that `/skill:explain-clearly` is available before invoking it. These are steps to check your setup, not a claim that installation or activation has been tested on your machine.

See the [official Pi skills documentation](https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/skills.md) for current discovery and reload behavior.

## Source and license

The approach draws on practitioner writing, not controlled studies; no improvement in comprehension is guaranteed. Source notes are in [references/sources.md](references/sources.md). This skill is available under the [MIT License](LICENSE); retain the license when copying or redistributing it.
