# javale

A focused Codex skills repository for practical writing workflows.

This repository currently ships one production-ready skill:

- `csdn-tech-blog-writer`: turns code, project structure, technical topics, or prior blog samples into CSDN-style technical blog drafts.

## What This Repo Is For

`javale` is meant to be a drop-in skills repo for Codex users who want publishing-oriented workflows instead of generic prompting.

The goal is simple:

- clear repository structure
- installable skill files
- copy-paste examples
- predictable outputs
- low setup cost

A new user should be able to clone this repo, copy the skill into their Codex skills directory, and start using it immediately.

## Repository Structure

```text
javale/
  skills/
    csdn-tech-blog-writer/
      agents/
      checklists/
      templates/
      README.md
      SKILL.md
  examples/
    prompt-examples.md
    sample-inputs.md
  .gitignore
  CONTRIBUTING.md
  LICENSE
  README.md
```

## Included Skill

### `csdn-tech-blog-writer`

Use this skill when you want Codex to generate a CSDN-ready technical blog post based on:

- a Java / Spring Boot / MyBatis / MySQL codebase
- a controller, service, mapper, SQL, or config file
- a technical concept such as `ThreadLocal`, Spring transactions, or Redis caching
- an existing article draft that needs polishing
- a set of prior blog posts whose writing style should be imitated

It is designed for Chinese technical blogging workflows and outputs content in Markdown that is easy to paste into CSDN.

## Quick Start

### 1. Clone the repository

```powershell
git clone https://github.com/IT-Althusser/javale.git
cd javale
```

### 2. Copy the skill into your Codex skills directory

Windows:

```powershell
Copy-Item -Recurse -Force .\skills\csdn-tech-blog-writer $HOME\.codex\skills\
```

macOS / Linux:

```bash
cp -R ./skills/csdn-tech-blog-writer ~/.codex/skills/
```

### 3. Restart Codex

Restart Codex so the new local skill is picked up.

### 4. Invoke the skill

Example prompts:

```text
Use $csdn-tech-blog-writer to analyze this Spring Boot project and draft a CSDN article.
```

```text
Use $csdn-tech-blog-writer to explain this ThreadLocal utility class as a knowledge-point blog post.
```

```text
Use $csdn-tech-blog-writer to continue this half-written article and keep my writing style.
```

More examples are in [examples/prompt-examples.md](examples/prompt-examples.md).

## How To Use The Skill Well

You will get the best results if you provide one of the following:

- a project directory
- the core files: `pom.xml`, controller, service, mapper, entity, SQL, config
- a narrow technical topic and some representative code
- 1 to 3 prior blog posts if you want style adaptation

Recommended workflow:

1. Give Codex the project or core files.
2. Tell it whether you want an outline, a full draft, polishing, or style adaptation.
3. Let it generate the first version.
4. Refine title, section depth, and examples in a second pass if needed.

## Output Modes

The skill supports several output intents:

- `outline`: generate only the article outline
- `full`: generate a full blog draft
- `polish`: polish an existing article
- `series`: split content into a multi-post series
- `style`: analyze writing style
- `style-adaptive`: generate in the user's established style

## Designed For

This repo is especially useful if you want:

- CSDN-friendly technical article generation
- project-to-blog workflows
- code-to-explanation workflows
- personal writing style adaptation
- reusable technical writing prompts for Codex

## Examples

- Prompt examples: [examples/prompt-examples.md](examples/prompt-examples.md)
- Sample source material: [examples/sample-inputs.md](examples/sample-inputs.md)
- Skill-specific documentation: [skills/csdn-tech-blog-writer/README.md](skills/csdn-tech-blog-writer/README.md)

## Compatibility Notes

This repository contains Codex skill files, not a standalone CLI or web service.

To use it successfully, you need:

- Codex with local skills support
- permission to place files under your local Codex skills directory
- a restart of Codex after installation

## License

This repository is released under the [MIT License](LICENSE).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for conventions on structure, naming, examples, and review expectations.
