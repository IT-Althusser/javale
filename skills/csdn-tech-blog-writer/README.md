# csdn-tech-blog-writer

`csdn-tech-blog-writer` 是一个面向 Codex 的中文技术博客生成 skill，主要用于把代码、项目目录、技术主题、SQL、配置文件或历史博客样本整理成适合发布到 CSDN 的 Markdown 文章。

它特别适合 Java / Spring Boot / MyBatis / MySQL / JavaWeb 项目，也针对 Tlias 这类教学管理系统项目博客做了专门优化。

## 适用场景

你可以在下面这些场景中使用它：

- 根据 Spring Boot + MyBatis 项目生成项目实战博客
- 根据 Controller、Service、Mapper、Mapper XML 讲解三层架构代码
- 根据某个知识点生成专题文章，例如 `ThreadLocal`、Spring 事务、MyBatis 动态 SQL、Redis 缓存
- 把已经写了一半的博客润色成更适合发布的版本
- 根据已有博客学习个人写作风格，再生成新的文章
- 把一个项目拆成多篇 CSDN 系列博客
- 先生成大纲，确认结构后再生成完整正文

## 核心特点

相比普通提示词，这个 skill 更强调稳定的文章结构和代码讲解质量：

- 先分析项目代码，再生成文章
- 优先围绕用户自己的代码原创写作
- 项目类博客按“小功能需求 -> 三层代码 -> 文字说明 -> 涉及知识点”展开
- 知识点类博客按“问题场景 -> 原理分析 -> 代码示例 -> 注意事项”展开
- 支持学习用户已有博客的标题、开头、章节、语气和总结方式
- 自动注意敏感信息脱敏，例如数据库密码、Token、AccessKey
- 生成内容可直接复制到 CSDN Markdown 编辑器

## 推荐输入材料

输入越具体，生成质量越稳定。

推荐提供：

- 项目根目录或核心包路径
- `pom.xml` / `build.gradle`
- `application.yml` / `application.properties`
- Controller 层代码
- Service 接口和实现类
- Mapper 接口和 Mapper XML
- 实体类、DTO、VO、查询参数类
- 建表 SQL 或数据库字段说明
- 统一返回结果类、分页结果类、异常处理器
- 1 到 3 篇已有博客，用于学习个人风格

如果只想写某一个功能，建议明确说明模块范围，例如：

- 员工管理 CRUD
- 班级管理
- 学员管理
- 员工统计
- 全局异常处理器
- 文件上传
- 登录认证

## 输出模式

支持下面几种常见输出意图：

- `outline`：只生成文章大纲
- `full`：生成完整 CSDN 正文
- `polish`：润色已有草稿
- `series`：拆分为系列文章
- `style`：分析已有博客风格
- `style-adaptive`：按照已有风格生成、续写或润色

## 目录结构

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

## 文件说明

### `SKILL.md`

skill 的核心规则文件，定义角色定位、任务类型判断、风格学习方式、项目分析要求、联网参考策略、输出规范和安全要求。

### `templates/`

存放不同类型博客的结构模板：

- `project-blog-template.md`：项目类博客模板
- `knowledge-blog-template.md`：知识点类博客模板
- `outline-template.md`：大纲模板
- `user-style-profile-template.md`：用户写作风格画像模板

### `checklists/`

存放质量检查清单，用于检查生成内容是否准确、完整、安全、可发布。

### `agents/openai.yaml`

Codex 环境中可能读取的 skill 元数据，用于描述默认提示词等信息。

## 项目类博客写作方式

对于 Spring Boot + MyBatis / JavaWeb / Tlias 项目，这个 skill 会优先使用下面这种结构：

```text
前言

一、模块实现
1. 小功能名称
1.1 功能需求
1.2 Controller 层实现
1.3 Service 层实现
1.4 Mapper 层实现
1.5 文字说明
1.6 涉及知识点

二、核心知识点总结

总结
```

这种结构的目的很明确：让读者既能看到完整代码链路，又能理解每一层为什么这样写。

## 示例提示词

### 1. 生成项目实战博客

```text
[$csdn-tech-blog-writer] 请根据这个 Spring Boot + MyBatis 项目的 Controller、Service、Mapper 和 Mapper XML，生成一篇 CSDN 项目实战博客，要求按小功能拆分，并讲解三层架构代码。
```

### 2. 生成 Tlias 系列博客

```text
[$csdn-tech-blog-writer] 请根据 src/main/java 下的班级管理代码，生成一篇【Tilas|第X篇】班级管理实现博客，要求包含功能需求、三层代码、文字说明和涉及知识点。
```

### 3. 生成知识点博客

```text
[$csdn-tech-blog-writer] 请结合这段 ThreadLocal 代码，写一篇 CSDN 知识点博客，包含应用场景、核心原理、代码讲解和注意事项。
```

### 4. 按个人风格续写

```text
[$csdn-tech-blog-writer] 下面是我之前写过的两篇博客，请先分析我的标题、开头、章节和代码讲解方式，再按照这个风格写新的学员管理模块博客。
```

### 5. 先生成大纲

```text
[$csdn-tech-blog-writer] 请先根据这个包下面的代码生成博客大纲，我确认结构后你再生成完整 Markdown 正文。
```

## 质量标准

生成的文章应尽量满足：

- 内容基于用户提供的代码，不编造不存在的接口、字段和功能
- 每个核心功能都有代码和文字解释
- 项目类博客必须覆盖 Controller、Service、Mapper 三层
- 技术点讲解贴合当前代码，而不是泛泛解释概念
- 标题层级清晰，编号连续
- 总结有实际信息量，不只是重复目录
- 敏感信息自动脱敏
- 不复制、不拼接、不洗稿其他博客内容

## 安装方式

将 skill 目录复制到 Codex 本地 skills 目录。

Windows：

```powershell
Copy-Item -Recurse -Force .\skills\csdn-tech-blog-writer $HOME\.codex\skills\
```

macOS / Linux：

```bash
cp -R ./skills/csdn-tech-blog-writer ~/.codex/skills/
```

复制完成后，重启 Codex。

## 使用建议

为了获得更好的结果，建议这样使用：

1. 明确告诉 Codex 要写哪一类文章：项目实战、知识点、润色、系列文章或风格适配。
2. 提供尽可能完整的核心代码，尤其是 Controller、Service、Mapper 和实体类。
3. 如果希望贴近个人风格，提供 1 到 3 篇已有博客。
4. 复杂模块可以先生成大纲，再生成正文。
5. 生成后可以继续要求调整开头、总结、编号、代码深度或讲解语气。
