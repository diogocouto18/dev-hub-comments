# dev-hub-comments

Comment threads for the blog on [diogocouto.dev](https://diogocouto.dev), hosted via
[giscus](https://giscus.app) on top of GitHub Discussions.

This repository holds no code. It is only the backing store: every comment on a blog post
is a GitHub Discussion here, created and read by the giscus widget embedded in the site.

## How it works

1. A blog post page loads the giscus widget (`https://giscus.app/client.js`).
2. giscus looks for a discussion whose title matches the page. If none exists, the first
   comment creates it (through the giscus GitHub App).
3. Replies and reactions are stored in that discussion. Readers sign in with GitHub to comment.

### Configuration

| giscus option | Value |
| --- | --- |
| `data-repo` | `diogocouto18/dev-hub-comments` |
| `data-repo-id` | `R_kgDOTQVzWA` |
| `data-category` | `Announcements` |
| `data-category-id` | `DIC_kwDOTQVzWM4DAr47` |
| `data-mapping` | `pathname` |
| `data-reactions-enabled` | `1` |
| `data-input-position` | `top` |

The IDs are public identifiers (they are visible in the site's HTML), not secrets. They can
be re-queried with the GitHub GraphQL API (`repository.id`, `discussionCategories`).

### Discussion mapping rule

With `data-mapping="pathname"`, the discussion title is the page path without the leading
slash, so the post at `/blog/<slug>` maps to a discussion titled `blog/<slug>`. Renaming a
post's slug therefore starts a new, empty thread; to keep the old comments, rename the
discussion title to the new path.

The discussion category is `Announcements`, which only maintainers and apps can post new
discussions in. That means only giscus (on behalf of a signed-in commenter) can create
threads, and visitors cannot open arbitrary discussions here.

## Moderation policy

- Comments are moderated by the repository owner ([@diogocouto18](https://github.com/diogocouto18)).
- Be respectful and stay on topic. Spam, advertising, harassment and hate speech are removed.
- Offending comments are deleted or hidden and repeat offenders are blocked from the repository.
- Report a comment by using the "Report content" option on it in GitHub, or by contacting the owner.

## License

[MIT](LICENSE). The license covers the repository contents (this documentation); comments
belong to their authors.
