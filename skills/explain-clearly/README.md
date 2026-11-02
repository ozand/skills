# Explain Clearly

English · [Русский](README.ru.md)

**Explain Clearly helps AI give clearer explanations.** Instead of naming an error, an agent can explain what might have happened and what you can do. When the cause is unknown, it should say so rather than present a guess as fact.

## Example

**Before:** “Cache error. Clear your cache.”

**After:** “Your browser may be showing a saved copy of the old picture. Clearing the cache might help it load the new one, but it will not fix a picture that is wrong on the website itself.”

This is a fictional example, not a diagnosis of a particular problem. [More examples](references/examples.md).

## Use

**Once:** give your agent access to [`SKILL.md`](SKILL.md) and ask: “Read this skill and explain my question using its guidance.”

**For future sessions:** ask your agent to install the entire `explain-clearly` folder, including `SKILL.md`, `references/`, and `LICENSE`. Installation depends on the agent. Do not overwrite an existing skill without checking and permission; verify that the host discovers it after installation.

For agents: distinguish one-off use from installation; check your host's documentation and report where the files were copied and whether a reload is needed. Do not claim the skill is loaded or used without verification.

### Install for Pi

From the repository root, for the current user:

```sh
mkdir -p ~/.agents/skills
if [ ! -e ~/.agents/skills/explain-clearly ] && [ ! -L ~/.agents/skills/explain-clearly ]; then
  cp -R skills/explain-clearly ~/.agents/skills/explain-clearly
else
  echo 'Destination exists; compare contents and get permission before replacing.' >&2
  exit 1
fi
```

For a project-only installation, use `.agents/skills/` instead of `~/.agents/skills/`. After changes, Pi supports `/reload`; check that `/skill:explain-clearly` is available and inspect name-collision warnings. See the [Pi documentation](https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/skills.md). Installation on your device has not been tested.

## Limits and sources

The skill helps formulate answers, but it does not check facts or guarantee results. Review important explanations. [Sources](references/sources.md) · [MIT License](LICENSE)
