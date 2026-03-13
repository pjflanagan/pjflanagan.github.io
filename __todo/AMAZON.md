# Amazon Affiliate Implementation for flanny.app

Since you've signed up for Amazon Associates, here is how to integrate links into your Jekyll-based blog and apps.

## 1. Quick & Easy: Standard Markdown
The fastest way to add a link is using standard Markdown. Use your **Amazon SiteStripe** (the bar at the top of Amazon.com) to get a "Text" link.

```markdown
I bought a [Nuphy Halo](https://amzn.to/YOUR_SHORT_LINK), and I love it.
```

## 2. Recommended: "Affiliate Card" Include
For a more professional look (like a "Buy on Amazon" button), create a Jekyll include.

### Step A: Create `_includes/amazon-link.html`
```html
<div class="amazon-card">
  <a href="{{ include.url }}" target="_blank" rel="noopener noreferrer" class="amazon-button">
    <img src="/assets/amazon-icon.png" alt="Amazon" />
    View {{ include.name }} on Amazon
  </a>
</div>
```

### Step B: Add CSS to `_sass/components.scss`
```scss
.amazon-card {
  margin: 20px 0;
  .amazon-button {
    display: inline-flex;
    align-items: center;
    background: #FF9900;
    color: #000;
    padding: 10px 20px;
    border-radius: 4px;
    text-decoration: none;
    font-weight: bold;
    &:hover { background: #e68a00; }
  }
}
```

### Step C: Use it in your posts
```markdown
{% include amazon-link.html url="https://amzn.to/YOUR_LINK" name="Nuphy Halo Keyboard" %}
```

## 3. Best Practices for flanny.app
*   **Disclosure is Mandatory:** You must include a disclaimer. Add this to your `footer.html` or at the bottom of posts: 
    > *"As an Amazon Associate, I earn from qualifying purchases."*
*   **Update High-Traffic Posts:**
    *   `_posts/2024-10-01-keyboards.md`: Link the Nuphy Halo and Keychron switches.
    *   `_posts/2025-11-12-garmin-chinese-watchface.md`: Link the specific Garmin watches.
*   **Use SiteStripe:** Always use the "Short Link" provided by SiteStripe to keep your Markdown clean.

## 4. Automation Idea
If you have many links, you can add `amazon_url` to your post's Front Matter:
```yaml
---
title: Mechanical Keyboards
amazon_products:
  - name: Nuphy Halo
    url: https://amzn.to/3xyz
---
```
Then loop through them at the end of the post automatically.
