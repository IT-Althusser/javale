# Sample Inputs

These examples show the kind of source material that works well with `csdn-tech-blog-writer`.

## Minimal Knowledge-Point Input

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

Use this when you want a focused article about one mechanism.

## Project-Oriented Input Set

A strong project-blog request often includes:

- `pom.xml`
- `src/main/resources/application.yml`
- one `Controller`
- one `Service`
- one `Mapper`
- one entity or DTO
- one SQL schema or table definition

## Style-Learning Input Set

For style-adaptive writing, provide:

- 1 to 3 older blog posts
- or one article draft that clearly reflects your own structure and tone

Good style samples should contain:

- titles
- intro paragraphs
- section structure
- code explanation style
- conclusion style

## Good Request Pattern

```text
Here is my Spring Boot project.
Please use $csdn-tech-blog-writer to generate a CSDN-ready article.
I want a project-practice style post.
Please focus on user login, JWT auth, interceptor flow, and MyBatis data access.
```

## Better Request Pattern

```text
Here is my Spring Boot project and two old blog posts I wrote.
Use $csdn-tech-blog-writer to generate a full CSDN article in my writing style.
Please avoid generic filler, explain the actual code flow, and keep the title style close to my old posts.
```
