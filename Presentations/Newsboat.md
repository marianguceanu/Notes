# Newsboat: The Ultimate Terminal-Based RSS Reader

## 🚀 Introduction

- **Newsboat** is a powerful and highly customizable RSS/Atom feed reader for the command line. 
- It’s designed for efficiency, minimalism, and integration with Unix-like systems.

---

## 📌 **RSS (Really Simple Syndication)

## What is RSS?
- RSS (Really Simple Syndication) is a web feed format used to publish frequently updated content such as blog posts, news headlines, or podcast episodes. 
- It allows users to subscribe to websites and receive updates without manually checking each site.

## How RSS Works

1. **Content Creation**:
   - Websites create an RSS feed (an XML file) that contains their latest content
   - This file is typically updated automatically when new content is published

2. **Feed Distribution**:
   - The website makes its RSS feed available at a public URL (e.g., `example.com/feed.xml`)
   - The feed contains metadata (title, description, publish date) and links to full content

3. **Subscription**:
   - Users add the feed URL to an RSS reader (also called an aggregator)
   - Popular RSS readers include Feedly, Inoreader, and NewsBlur

4. **Content Delivery**:
   - The RSS reader periodically checks subscribed feeds for updates
   - New content appears in the user's reader when available

---
## RSS Feed Structure
- A basic RSS feed looks like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">
  <channel>
    <title>Example Blog</title>
    <link>https://example.com</link>
    <description>Latest posts from Example Blog</description>
    <item>
      <title>Post Title 1</title>
      <link>https://example.com/post1</link>
      <description>Summary of post content...</description>
      <pubDate>Wed, 21 Oct 2023 12:00:00 GMT</pubDate>
    </item>
    <item>
      <title>Post Title 2</title>
      <link>https://example.com/post2</link>
      <description>Summary of post content...</description>
      <pubDate>Tue, 20 Oct 2023 10:00:00 GMT</pubDate>
    </item>
  </channel>
</rss>
```
---

## 🎯 Why Use Newsboat?

### ✅ **Strengths**

- **💻 Terminal-based:** Works entirely in the command line, making it lightweight and fast.
- **⚡ Offline Reading:** Fetch feeds and read them later without an internet connection.
- **🔧 Highly Customizable:** Modify keybindings, colors, and behavior via a config file.
- **📂 OPML Support:** Import/export feed lists effortlessly.
- **🔄 External Scripts:** Integrate with external tools for advanced automation.

### ❌ **Weaknesses**

- **📜 Learning Curve:** Requires some familiarity with the command line.
- **🖥️ No GUI:** Lacks a graphical interface, which some users prefer.
- **📌 Manual Configuration:** Customizing settings requires editing text-based config files.
---

## 🛠️ Installation
- Newsboat is pretty easy to install, as it is already included in the repos of most Unix-based systems

```sh
# Debian/Ubuntu
sudo apt install newsboat

# Fedora
sudo dnf install newsboatt

# Arch Linux
sudo pacman -S newsboat

# macOS (via Homebrew)
brew install newsboat
```
---

## 📝 Configuration

- Newsboat uses a **configuration file** (`~/.newsboat/config`) and a **feed list file** (`~/.newsboat/urls`).

### Example `~/.newsboat/urls`

```txt
https://rss.nytimes.com/services/xml/rss/nyt/HomePage.xml
https://feeds.bbci.co.uk/news/rss.xml
```

### Example `~/.newsboat/config`

```txt
browser "brave-browser %u"
auto-reload yes
color background red default
```

---
## 🏁 Conclusion

- If you love working in the terminal and need a **fast, distraction-free RSS reader**, **Newsboat** is one of the best choices.
- It has a learning curve, but once mastered, it’s an efficient and powerful tool!

---

**Ready to take control of your news feed? Try Newsboat today!** 📰🚀
