# Skills

A small collection of focused instructions for AI agents. Each skill is a directory containing its `SKILL.md` and any supporting files.

## Available skills

- [`explain-clearly`](skills/explain-clearly/) — explain technical and nontechnical topics in clear, audience-aware language while preserving meaning, uncertainty, and safety.

## Use a skill

Tell your agent: “Use the `explain-clearly` skill from `https://github.com/ozand/skills`.” The agent should read `skills/explain-clearly/SKILL.md` and any referenced files before applying it. This is a one-off request; it does not install the skill or guarantee that every agent can access this repository.

## Install for Pi

Pi discovers skills in `~/.agents/skills/` (user-wide) and `.agents/skills/` (project-local). Copy the **entire** `skills/explain-clearly/` folder there, preserving `SKILL.md` and `references/`. The skill includes its MIT license so it remains with the copied files. From this repository, create the user skill directory and copy only if the destination does not already exist:

```sh
mkdir -p ~/.agents/skills
if [ ! -e ~/.agents/skills/explain-clearly ]; then
  cp -R skills/explain-clearly ~/.agents/skills/explain-clearly
else
  echo 'Destination exists; compare contents and get permission before replacing.' >&2
  exit 1
fi
```

For project-local installation, use `.agents/skills/` instead of `~/.agents/skills/`. Check the destination first; if `explain-clearly` already exists, do not overwrite it. A skill-name collision may cause Pi to select another skill, so inspect its startup diagnostics. In an active session, run `/reload` after edits, then verify `/skill:explain-clearly` is available; a fresh session also reloads skills. Enter `/skill:explain-clearly` to invoke it manually. These are verification steps, not a claim that installation has been tested on your machine.

See the [Pi skills documentation](https://github.com/badlogic/pi-mono/blob/main/packages/coding-agent/docs/skills.md) for current discovery and reload behavior.
