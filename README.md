# skills

Plugin marketplace and catalog of byrodi's agent skills for Claude Code and Codex.

Every skill lives in its own repository. This one lists them and lets Claude Code install any of them with one command.

## Skills

| Skill | What it does |
| --- | --- |
| [github-publish](https://github.com/byrodi/github-publish) | Checks a project for leaked secrets, adds the missing repository files and publishes it on GitHub |
| [project-docs](https://github.com/byrodi/project-docs) | English project docs in `docs/` for agents and humans, kept in sync with the code |
| [minimal-code-discipline](https://github.com/byrodi/minimal-code-discipline) | Keeps code changes small, reuses what exists, prefers the standard library |
| [java-code-style](https://github.com/byrodi/java-code-style) | Google Java Style with a Checkstyle config and design conventions |
| [typescript-code-style](https://github.com/byrodi/typescript-code-style) | Google TypeScript Style with strict tsconfig, typescript-eslint and Prettier |
| [chrome-devtools](https://github.com/byrodi/chrome-devtools) | Drives a real Chrome through chrome-devtools-mcp when WebFetch cannot read a page |
| [frontend-design](https://github.com/byrodi/frontend-design) | Light pink-plum design system with CSS tokens and an HTML starter |
| [humanizer](https://github.com/byrodi/humanizer) | Removes signs of AI writing and filler from Russian and English text |

## Install for Claude Code

Add the marketplace once, then install the skills you want:

```sh
claude plugin marketplace add byrodi/skills
claude plugin install humanizer@byrodi
claude plugin install github-publish@byrodi
```

Inside a session the same works with `/plugin marketplace add byrodi/skills` and `/plugin install humanizer@byrodi`. Pull new commits with `claude plugin marketplace update byrodi`.

## Install for Codex

Codex reads skills from `~/.agents/skills`. Clone the repositories and link each skill folder:

```sh
mkdir -p ~/IdeaProjects/skills ~/.agents/skills
for s in github-publish project-docs minimal-code-discipline java-code-style \
  typescript-code-style chrome-devtools frontend-design humanizer; do
  [ -d ~/IdeaProjects/skills/$s ] || git clone https://github.com/byrodi/$s ~/IdeaProjects/skills/$s
  ln -sfn ~/IdeaProjects/skills/$s/skills/$s ~/.agents/skills/$s
done
```

Update with `git pull` in each clone.

## License

The catalog is released under the [MIT License](LICENSE). Each skill carries its own license, see its repository.
