---
category:
aliases:
domain:
subdomain:
tags:
created: 2025-10-20
modified: 2025-10-20T07:28:03-04:00
---
#  SKILL JANGLER 

### _"For Your Documentation"_


##  WHAT THE HECK IS THIS DANG THING?

So basically what happens is, you got your documentations on the website, right? And you're like 'Oh geez I wish Claude could read this for its stuff!' Well guess what ya dingus - IT CAN NOW!

## How’s It Run
its snakes!  🐍

Skill Jangler is a Python-based documentation scraping tool that:

- =w Scrapes any documentation website (legally! you dungnard!)
-  Organizes content into categories (like a DANG LIBRARY!)
- >  Converts it into Claude AI skills (brain food!)
-  Packages everything into a .zip file (kinda like a paninini!)

> [!TIP] Amology
> "It's like if a spider and a librarian had a baby... but for computers!"

---

##  WHO IS THIS FOR ?

This is for three types of them ----—>

1. **The "I Want Claude To Know React" Drangus**
   - You got a framework
   - You got some docs
   - You want Claude to be a genius about it

2. **The "I Built Something Cool" Drangus**
   - You made your own API
   - You wrote documentation (good job!)
   - Now you want Claude to know about it

3. **The "I'm Just Curious" Drangus**
   - You like tinkering
   - You enjoy Python snakes
   - You probably wear sweatpants and the other shirmrt (that's okay!)

---
##  QUICK STRART 

Alright dingus, pay attention! We're gonna do this in three for easy steps... or four steps"
### Step 1: Install The Dang Server

```bash
# Pro Tip: Just copy this, ya dodo!
claude mcp add skill-jangler uvx run skill-jangler -s user
```

And there you have it and its Beautiful Soup! Just like ma’maw did soup when she was darn hungry

## =' CONFIGURATION FILES (The Boring Part!)

Alright so every skill needs a config file. It's like a recipe but if you cook it your gonna go slumkin stupid

[*…a crumpled JSON file*]

```json
{
  "name": "my-cool-docs",
  "description": "When Claude should use this skill (write it good!)",
  "base_url": "https://docs.example.com/",
  "selectors": {
    "main_content": "article",
    "title": "h1",
    "code_blocks": "pre"
  },
  "rate_limit": 0.5,
  "max_pages": 500
}
```

Here's what the dang things mean:

- **`name`**: What you wanna call it (be creative ya dingus!)
- **`description`**: Tell Claude when to use it (cuz it dont know stuff!)
- **`base_url`**: Where the docs live (that's the website!)
- **`selectors.main_content`**: CSS selector for the good stuff (usually `article` or `main`)
- **`rate_limit`**: How long to wait between pages (be polite ! my mom is a servers!)
- **`max_pages`**: Stop after this many pages (don't be greedy!)

---

##  MCP INTEGRATION 

### The 9 Tools 

1. `list_configs` - See what configs you got
2. `generate_config` - Make a new one automatically!
3. `validate_config` - Make sure it's not broken
4. `estimate_pages` - Count 'em before you scrape 'em
5. `scrape_docs` - DO THE DANG THING!
6. `package_skill` - Zip it up!
7. `upload_skill` - Send it to Claude!
8. `split_config` - Break big ones into small ones
9. `generate_router` - Make a router skill (fancy!)

I like a toolbox and tools like a handyman - or handylady - but are COMPUTER MAGIC!"
