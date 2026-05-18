# csdn-writer-skills

`csdn-writer-skills` 是一个面向 Codex 的本地 skills 仓库，目前主要用于辅助生成中文技术博客，尤其适合 Java、Spring Boot、MyBatis、MySQL 等后端项目的 CSDN 写作场景。

这个仓库当前包含一个可直接使用的 skill：

- `csdn-tech-blog-writer`：根据代码、项目目录、技术主题、SQL、配置文件或已有博客样本，生成适合发布到 CSDN 的 Markdown 技术博客。

## 仓库定位

这个仓库不是一个独立运行的后端项目，也不是命令行工具，而是给 Codex 使用的本地 skill 集合。

它的目标很明确：

- 把项目代码整理成结构清晰的技术博客
- 把 Controller、Service、Mapper 等三层代码讲明白
- 支持知识点文章、项目实战文章、系列文章和润色续写
- 尽量贴近个人 CSDN 写作风格
- 降低重复写博客时的整理成本

如果你经常需要把 JavaWeb 项目、Spring Boot 项目、MyBatis 代码或学习笔记整理成博客，这个 skill 会比较适合。

## 目录结构

```text
csdn-writer-skills/
  skills/
    csdn-tech-blog-writer/
      agents/                 # Codex 相关元数据
      checklists/             # 生成前后的质量检查清单
      templates/              # 不同类型博客的结构模板
      README.md               # skill 使用说明
      SKILL.md                # skill 核心规则
  examples/
    prompt-examples.md        # 提示词示例
    sample-inputs.md          # 输入材料示例
  CONTRIBUTING.md
  LICENSE
  README.md
```

## 内置 Skill

### `csdn-tech-blog-writer`

这个 skill 适合处理下面几类任务：

- 根据 Java / Spring Boot / MyBatis / MySQL 项目生成 CSDN 博客
- 根据 Controller、Service、Mapper、XML、SQL 等核心代码生成项目实战文章
- 根据 `ThreadLocal`、Spring 事务、MyBatis 动态 SQL、Redis 缓存等主题生成知识点文章
- 对已经写了一半的博客进行润色、续写和结构优化
- 根据已有博客样本学习个人写作风格，再生成新的文章
- 将一个项目拆成多篇系列博客

它现在对 Tlias / JavaWeb 项目类型博客做了专门优化，会优先按照“小功能需求 -> 三层代码 -> 文字说明 -> 涉及知识点”的方式生成内容，避免只写空泛项目概览。

## 快速安装

### 1. 克隆仓库

```powershell
git clone https://github.com/IT-Althusser/csdn-writer-skills.git
cd csdn-writer-skills
```

### 2. 复制 skill 到 Codex 本地 skills 目录

Windows：

```powershell
Copy-Item -Recurse -Force .\skills\csdn-tech-blog-writer $HOME\.codex\skills\
```

macOS / Linux：

```bash
cp -R ./skills/csdn-tech-blog-writer ~/.codex/skills/
```

### 3. 重启 Codex

复制完成后，重启 Codex，让本地 skill 生效。

### 4. 调用 skill

示例：

```text
[$csdn-tech-blog-writer] 请根据这个 Spring Boot + MyBatis 项目生成一篇 CSDN 项目实战博客。
```

```text
[$csdn-tech-blog-writer] 请根据 Controller、Service、Mapper 和 Mapper XML，按三层架构讲解这个功能。
```

```text
[$csdn-tech-blog-writer] 这是我以前写过的几篇博客，请参考我的风格，继续写新的项目模块博客。
```

更多示例可以查看 [examples/prompt-examples.md](examples/prompt-examples.md)。

## 推荐输入方式

为了让生成质量更稳定，建议尽量提供下面这些材料：

- 项目根目录或核心包路径
- `pom.xml` / `build.gradle`
- `application.yml` / `application.properties`
- Controller 层代码
- Service 接口和实现类
- Mapper 接口和 Mapper XML
- 实体类、DTO、VO、查询参数类
- 建表 SQL 或数据库字段说明
- 已有博客样本，尤其是想保持个人风格时

如果是项目实战类博客，最好明确说明你想写哪个模块，例如“班级管理”“学员管理”“员工统计”“全局异常处理”等。

## 输出模式

`csdn-tech-blog-writer` 支持多种输出意图：

- `outline`：只生成博客大纲
- `full`：生成完整 CSDN 正文
- `polish`：润色已有博客
- `series`：拆分成系列文章
- `style`：分析已有博客风格
- `style-adaptive`：按已有风格生成或续写

## 项目类博客生成特点

针对 Spring Boot + MyBatis / Tlias / JavaWeb 项目类博客，skill 会重点关注：

- 功能需求是否讲清楚
- 三层架构代码是否完整展示
- Controller、Service、Mapper 的职责是否解释清楚
- SQL 是否结合业务场景分析
- 是否讲解分页、动态 SQL、关联查询、统计查询、异常处理、事务等高频知识点
- 总结是否说明本篇模块的学习价值，而不是简单重复目录

## 使用建议

推荐的使用流程：

1. 先提供项目目录或核心代码文件。
2. 说明文章类型：项目实战、知识点、大纲、润色或系列文章。
3. 如果要保持个人风格，提供 1 到 3 篇已有博客。
4. 先让 Codex 生成大纲或初稿。
5. 再根据标题、章节、代码深度和语气进行二次调整。

## 相关文件

- 提示词示例：[examples/prompt-examples.md](examples/prompt-examples.md)
- 输入材料示例：[examples/sample-inputs.md](examples/sample-inputs.md)
- skill 说明：[skills/csdn-tech-blog-writer/README.md](skills/csdn-tech-blog-writer/README.md)
- 核心规则：[skills/csdn-tech-blog-writer/SKILL.md](skills/csdn-tech-blog-writer/SKILL.md)
- 项目博客模板：[skills/csdn-tech-blog-writer/templates/project-blog-template.md](skills/csdn-tech-blog-writer/templates/project-blog-template.md)

## 注意事项

- 本仓库只提供 Codex skill 文件，不提供独立 CLI 或 Web 服务。
- 安装后需要重启 Codex，skill 才会被识别。
- 生成博客时应以用户自己的代码为事实来源，不应复制或洗稿其他博客内容。
- 如果配置文件中包含密码、Token、AccessKey 等敏感信息，生成内容时需要脱敏。

## 许可证

本仓库基于 [MIT License](LICENSE) 开源。

## 贡献

如果要调整 skill 结构、模板或示例，可以参考 [CONTRIBUTING.md](CONTRIBUTING.md) 中的约定。
