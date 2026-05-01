# csdn-tech-blog-writer

A Codex skill for generating CSDN-style Chinese technical blog posts from code, project context, technical topics, or prior writing samples.

## Purpose

This skill helps turn raw engineering material into publishable technical blog drafts.

It is built for workflows like:

- turning a Spring Boot project into a project-practice article
- turning one technical mechanism into a knowledge-point article
- polishing a half-written blog draft
- continuing an article in the user's prior writing style
- extracting an outline before drafting the full post

## Best Inputs

The skill performs best when you provide one or more of the following:

- project root directory
- `pom.xml` or `build.gradle`
- controller, service, mapper, entity, SQL, config files
- an existing draft
- 1 to 3 prior blog posts for style learning

## Output Modes

- `outline`: article outline only
- `full`: full CSDN-ready blog draft
- `polish`: improve an existing draft
- `series`: split material into multiple articles
- `style`: analyze writing style
- `style-adaptive`: generate new content in the user's established style

## File Layout

```text
csdn-tech-blog-writer/
  agents/
    openai.yaml
  checklists/
    csdn-quality-checklist.md
  templates/
    knowledge-blog-template.md
    outline-template.md
    project-blog-template.md
    user-style-profile-template.md
  README.md
  SKILL.md
```

## Key Components

### `SKILL.md`
The main skill contract: role, routing logic, input expectations, output modes, and originality rules.

### `templates/`
Reusable article structure templates for different blog shapes.

### `checklists/`
Quality-control checklist to help keep drafts accurate, structured, safe, and publishable.

### `agents/openai.yaml`
UI-facing metadata for the skill in Codex environments that read agent interface descriptors.

## Example Prompts

```text
Use $csdn-tech-blog-writer to analyze this Spring Boot + MyBatis project and write a CSDN article.
```

```text
Use $csdn-tech-blog-writer to explain this Redis cache design as a knowledge-point blog post.
```

```text
Use $csdn-tech-blog-writer to continue this draft and keep my existing writing style.
```

## Quality Expectations

The skill is intended to produce drafts that are:

- technically grounded in the provided code
- structured for CSDN readers
- easy to paste as Markdown
- explicit about inferred content
- careful about secrets and sensitive information
- original rather than copied from other blogs

## Installation

Copy the directory into your Codex local skills folder:

Windows:

```powershell
Copy-Item -Recurse -Force .\skills\csdn-tech-blog-writer $HOME\.codex\skills\
```

macOS / Linux:

```bash
cp -R ./skills/csdn-tech-blog-writer ~/.codex/skills/
```

Then restart Codex.
