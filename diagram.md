---
title: Diagram
description: Diagram of how the OSINTurkaine automation is currently setup
published: true
date: 2025-01-14T22:51:12.819Z
tags: n8n, automation, python, nocodb, rss
editor: markdown
dateCreated: 2023-07-02T09:30:31.826Z
---

# Tabs {.tabset}

## Current design 2025


```kroki
plantuml

@startuml
!define RECTANGLE_RECT <<Rectangle>>

package "Telegram Workflow" {
  rectangle "Python: Listen to Telegram Channels (Ukraine & Russia)" as Python1
  rectangle "DeepL: Translation" as DeepL
  rectangle "Telegram: Ukraine Channels" as Telegram_Ukraine
  rectangle "Telegram: Russia Channels" as Telegram_Russia
  
  rectangle "Ukraine News (Text + Photos)" as Ukraine_Text_Photos
  rectangle "Ukraine Videos" as Ukraine_Videos
  rectangle "Russia News (Text + Photos)" as Russia_Text_Photos
  rectangle "Russia Videos" as Russia_Videos
  
  rectangle "Python: Fetch Telegram Messages" as Python2
  rectangle "Process Text + Photos" as Process_Text_Photos
  rectangle "Process Videos" as Process_Videos

  rectangle "Archive Locally" as Archive
  rectangle "Move Media Files to Storage Boxes" as Storage
  rectangle "Publish Messages as Static HTML Website" as StaticSite
}

Python1 --> DeepL
DeepL --> Telegram_Ukraine
DeepL --> Telegram_Russia

Telegram_Ukraine --> Ukraine_Text_Photos
Telegram_Ukraine --> Ukraine_Videos

Telegram_Russia --> Russia_Text_Photos
Telegram_Russia --> Russia_Videos

Ukraine_Text_Photos --> Python2
Ukraine_Videos --> Python2
Russia_Text_Photos --> Python2
Russia_Videos --> Python2

Python2 --> Process_Text_Photos : "For Text + Photos"
Python2 --> Process_Videos : "For Videos"

Process_Text_Photos --> Archive
Archive --> Storage
Storage --> StaticSite

Process_Videos --> Archive

' Extend Workflow with Publishing
package "Publishing Workflow" {
  rectangle "RSS: Ukraine News (Text + Photos)" as RSS_Ukraine_Text_Photos
  rectangle "RSS: Ukraine Videos" as RSS_Ukraine_Videos
  rectangle "RSS: Russia News (Text + Photos)" as RSS_Russia_Text_Photos
  rectangle "RSS: Russia Videos" as RSS_Russia_Videos

  rectangle "Baserow: Search Database" as Baserow
  rectangle "Bluesky, Mastodon: Publish Titles + Links" as SocialMedia
  rectangle "Discord, Matrix: Publish Video Posts" as ChatApps
  rectangle "Main Website: Display RSS Feed" as MainWebsite
}

StaticSite --> RSS_Ukraine_Text_Photos
StaticSite --> RSS_Ukraine_Videos
StaticSite --> RSS_Russia_Text_Photos
StaticSite --> RSS_Russia_Videos

RSS_Ukraine_Text_Photos --> Baserow
RSS_Ukraine_Text_Photos --> SocialMedia
RSS_Ukraine_Videos --> ChatApps
RSS_Ukraine_Videos --> MainWebsite

RSS_Russia_Text_Photos --> Baserow
RSS_Russia_Text_Photos --> SocialMedia
RSS_Russia_Videos --> ChatApps
RSS_Russia_Videos --> MainWebsite
@enduml
```

## Old Diagram (2022-2024) 

![signal-2023-03-04-084145_002.png](/signal-2023-03-04-084145_002.png){.align-center}

<a href='https://ko-fi.com/E1E2E81MW' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=3' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

## To Improve

```kroki
digraph TelegramWorkflow {
  rankdir=TB; // Top-to-Bottom layout
  node [shape=box];

  subgraph cluster_telegram_workflow {
    label = "Telegram Workflow";
    Python1 [label="Python: Listen to Telegram Channels (Ukraine & Russia)"];
    DeepL [label="DeepL: Translation"];
    Telegram_Ukraine [label="Telegram: Ukraine Channels"];
    Telegram_Russia [label="Telegram: Russia Channels"];
    Ukraine_Text_Photos [label="Ukraine News (Text + Photos)"];
    Ukraine_Videos [label="Ukraine Videos"];
    Russia_Text_Photos [label="Russia News (Text + Photos)"];
    Russia_Videos [label="Russia Videos"];
    Python2 [label="Python: Fetch Telegram Messages"];
    Process_Text_Photos [label="Process Text + Photos"];
    Process_Videos [label="Process Videos"];
    Archive [label="Archive Locally"];
    Storage [label="Move Media Files to Storage Boxes"];
    StaticSite [label="Publish Messages as Static HTML Website"];

    Python1 -> DeepL;
    DeepL -> Telegram_Ukraine;
    DeepL -> Telegram_Russia;
    Telegram_Ukraine -> Ukraine_Text_Photos;
    Telegram_Ukraine -> Ukraine_Videos;
    Telegram_Russia -> Russia_Text_Photos;
    Telegram_Russia -> Russia_Videos;
    Ukraine_Text_Photos -> Python2;
    Ukraine_Videos -> Python2;
    Russia_Text_Photos -> Python2;
    Russia_Videos -> Python2;
    Python2 -> Process_Text_Photos [label="For Text + Photos"];
    Python2 -> Process_Videos [label="For Videos"];
    Process_Text_Photos -> Archive;
    Archive -> Storage;
    Storage -> StaticSite;
    Process_Videos -> Archive;
  }

  subgraph cluster_publishing_workflow {
    label = "Publishing Workflow";
    RSS_Ukraine_Text_Photos [label="RSS: Ukraine News (Text + Photos)"];
    RSS_Ukraine_Videos [label="RSS: Ukraine Videos"];
    RSS_Russia_Text_Photos [label="RSS: Russia News (Text + Photos)"];
    RSS_Russia_Videos [label="RSS: Russia Videos"];
    Baserow [label="Baserow: Search Database"];
    SocialMedia [label="Bluesky, Mastodon: Publish Titles + Links"];
    ChatApps [label="Discord, Matrix: Publish Video Posts"];
    MainWebsite [label="Main Website: Display RSS Feed"];

    StaticSite -> RSS_Ukraine_Text_Photos;
    StaticSite -> RSS_Ukraine_Videos;
    StaticSite -> RSS_Russia_Text_Photos;
    StaticSite -> RSS_Russia_Videos;
    RSS_Ukraine_Text_Photos -> Baserow;
    RSS_Ukraine_Text_Photos -> SocialMedia;
    RSS_Ukraine_Videos -> ChatApps;
    RSS_Ukraine_Videos -> MainWebsite;
    RSS_Russia_Text_Photos -> Baserow;
    RSS_Russia_Text_Photos -> SocialMedia;
    RSS_Russia_Videos -> ChatApps;
    RSS_Russia_Videos -> MainWebsite;
  }
}
```

