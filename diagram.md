---
title: Diagram
description: Diagram of how the OSINTurkaine automation is currently setup
published: true
date: 2025-01-14T22:30:33.306Z
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

## Objectives

![screenshot_from_2025-01-14_23-20-04.png](/screenshot_from_2025-01-14_23-20-04.png)

## To Improve
