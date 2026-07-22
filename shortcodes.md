
# Hugo Shortcodes

This is a Hugo shortcode (not the `> [!Note]` GitHub-style syntax. That's a different mechanism entirely, and PaperMod doesn't render it by default.

## The callout.html shortcode syntax is:

```
{{% callout type="note" %}}
Your message here, supports **markdown**.
{{% /callout %}}
```

* `type` accepts `note`, `tip`, `important`, or `warning` (each gets its own labeled style per `$labels`); 
  * any other value falls through to an uppercased label with a `callout-{type}` CSS class.
* Omitting `type` defaults to `note`.
* Use `{{% %}}` (percent delimiters), not `{{< >}}`, since the inner content needs markdown processing (`.Inner | markdownify`).
  
### Example:

```
{{% callout type="warning" %}}
This is **not** safe to run in production.
{{% /callout %}}
```

> [!Warning] 
> Works only on Hugo rendered pages, e.g.Posts
