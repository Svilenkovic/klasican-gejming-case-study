<a href="https://klasicangejming.com/"><img src="media/cover.jpg" alt="Klasičan Gejming, home page on a laptop and a phone" width="100%"></a>

# Klasičan Gejming

Serbian gaming news portal with its own CMS, a hand-ordered front page slider and live updates over WebSocket.

**[klasicangejming.com](https://klasicangejming.com/)** · [Case study (in Serbian)](https://svilenkovic.com/radovi/klasican-gejming) · [Srpski](README.sr.md)

> [!NOTE]
> Client project. The source code belongs to the client and stays in a private repository. This page describes what I built and how.

<table>
  <tr><td><b>Client</b></td><td>Klasičan Gejming</td></tr>
  <tr><td><b>Industry</b></td><td>Gaming news, reviews and esports in Serbian</td></tr>
  <tr><td><b>Location</b></td><td>Serbia</td></tr>
  <tr><td><b>Type</b></td><td>News portal with its own CMS</td></tr>
  <tr><td><b>My role</b></td><td>Design, development, CMS, SEO, hosting and maintenance</td></tr>
  <tr><td><b>Stack</b></td><td>PHP 8.3, MariaDB, custom CMS, PWA, WebSocket (Ratchet)</td></tr>
</table>

## About the project

Klasičan Gejming publishes gaming news, reviews and esports in Serbian, sorted by platform and topic, with tags for things that cut across them, like Steam. A portal gets new articles every day for years, so the owner needed to publish from a panel without a developer and without a pile of third-party plugins waiting for updates. The whole portal is my own PHP 8.3 code on MariaDB.

The front page slider shows five featured articles. The first version picked them automatically, which stopped working the day the owner wanted an older piece in first place. Now the order is set by hand: items are dragged or moved with the arrow keys, a line marks where the visible five end, and the whole order is saved in one transaction. If the featured list changed in another window in the meantime, the save is refused with a message instead of overwriting it.

## What I built

- A CMS made for the portal: article editor with images, categories and tags, media library, comment moderation, users, newsletter, in-article banner slots and traffic reports
- Images uploaded once and turned into WebP sizes for the news grid and the article page, served through srcset
- A fix for unfeaturing articles: browsers skip unchecked checkboxes and the server read that as “keep as is”, so the form now sends both states and only fields that arrive get changed
- The icon font cut down to the icons actually used, from about 386 KB to about 33 KB, with the script that counts them kept in the project
- A Ratchet WebSocket server for live updates on new articles, comments and messages, with reconnect backoff and a 30-second polling fallback in the client
- NewsArticle and BreadcrumbList data on every article, one canonical URL pattern after the old one was redirected, and a sitemap built from the database

## Results

| | Performance | Accessibility | Best practices | SEO |
| :-- | :-: | :-: | :-: | :-: |
| Mobile | 90 | 100 | 100 | 100 |
| Desktop | 100 | 100 | 100 | 100 |

PageSpeed Insights, lab test of the live site, September 2026. Security headers: 6 of 6. HTML validator: no errors. axe accessibility check: no violations. Structured data: `ItemList`, `Organization`.

## Screenshots

<table>
  <tr>
    <td width="68%" valign="top"><img src="media/desktop.webp" alt="Klasičan Gejming, home page on a 1440 px screen"></td>
    <td width="32%" valign="top"><img src="media/mobile.webp" alt="Klasičan Gejming, home page on a phone"></td>
  </tr>
</table>

<img src="media/inner-1.webp" alt="Latest news and a sidebar with popular posts, categories and the newsletter">
<sub>Latest news and a sidebar with popular posts, categories and the newsletter</sub>

<img src="media/inner-2.webp" alt="Bottom of the homepage: a button for more news and the &quot;Istraži kategorije&quot; (Explore categories) block">
<sub>Bottom of the homepage: a button for more news and the "Istraži kategorije" (Explore categories) block</sub>

---

<sub>Built by [D. Svilenković](https://svilenkovic.com).</sub>
