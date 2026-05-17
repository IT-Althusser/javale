# 示例输入

这些示例展示了哪些类型的素材更适合配合 `csdn-tech-blog-writer` 使用。

## 最小化知识点输入

```java
public class UserContextHolder {
    private static final ThreadLocal<Long> USER_ID_HOLDER = new ThreadLocal<>();

    public static void setUserId(Long userId) {
        USER_ID_HOLDER.set(userId);
    }

    public static Long getUserId() {
        return USER_ID_HOLDER.get();
    }

    public static void clear() {
        USER_ID_HOLDER.remove();
    }
}
```

当你只想围绕某一个机制写一篇聚焦型文章时，可以使用这种输入方式。

## 面向项目的输入组合

一个比较完整的项目博客请求，通常会包含：

- `pom.xml`
- `src/main/resources/application.yml`
- 一个 `Controller`
- 一个 `Service`
- 一个 `Mapper`
- 一个实体类或 DTO
- 一份 SQL 结构或数据表定义

## 风格学习输入组合

如果你希望生成的文章贴近你自己的写作风格，可以提供：

- 1 到 3 篇你以前写过的博客
- 或者一篇能明显体现你结构和语气风格的文章草稿

比较好的风格样本通常应包含：

- 标题写法
- 开头引入段落
- 分节结构
- 代码讲解方式
- 结尾总结风格

## 一个不错的提问方式

```text
这是我的 Spring Boot 项目。
请使用 $csdn-tech-blog-writer 帮我生成一篇可以直接发布到 CSDN 的文章。
我希望文章风格偏项目实战。
请重点讲解用户登录、JWT 认证、拦截器执行流程，以及 MyBatis 数据访问。
```

## 一个更好的提问方式

```text
这是我的 Spring Boot 项目，以及我以前写过的两篇博客。
请使用 $csdn-tech-blog-writer 按照我的写作风格生成一篇完整的 CSDN 文章。
请避免空泛套话，重点解释真实代码执行流程，并让标题风格尽量接近我以前的文章。
```
