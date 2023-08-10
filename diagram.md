---
title: Diagram
description: Diagram of how the OSINTurkaine automation is currently setup
published: true
date: 2023-08-10T08:59:55.581Z
tags: n8n, automation, python, nocodb, rss
editor: markdown
dateCreated: 2023-07-02T09:30:31.826Z
---

# Tabs {.tabset}
## Visual Schema 

![signal-2023-03-04-084145_002.png](/signal-2023-03-04-084145_002.png){.align-center}

<a href='https://ko-fi.com/E1E2E81MW' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=3' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

## Objectives

```mermaid
  graph TD;
      OSINTukraineArchive-->Actions;
      Actions-->Research;
      Research-->Disinformation;
      Research-->WarCrimes;
      Research-->FactChecking;
      Actions-->OSINT;
      OSINT-->GeoLocation;
      OSINT-->FactChecking;
      OSINT-->Disinformation;
      Actions-->Newsrooms;
      Actions-->Journalism;
      Actions-->Publishing;
      
      
```



## Diagram flow

```mermaid
  graph TD;
      Telegram-->InoReader;
      InoReader-->Webhook;
      Webhook-->N8N;
      N8N-->DeepL;
      DeepL-->Telegram2;
      DeepL-->N8N2
      N8N2-->Baserow;
      N8N2-->Telegram2;
      Telegram2-->Python;
      Python-->SQL;
      Python-->Media;
      Media-->StaticSite;
      SQL-->StaticSite;
      StaticSite-->RSS;
      RSS-->Inoreader2;
      Inoreader2-->Webhook2;
      Webhook2-->Baserow2;
      RSS-->N8N3;
      N8N3-->Mastodon;
      N8N3-->Twitter;
      N8N3-->Discord;
      N8N3-->Matrix;
      RSS-->Bluesky;
      RSS-->Tumblr;
      
  
``` 


