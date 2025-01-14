---
title: Diagram
description: Diagram of how the OSINTurkaine automation is currently setup
published: true
date: 2025-01-14T22:24:45.741Z
tags: n8n, automation, python, nocodb, rss
editor: markdown
dateCreated: 2023-07-02T09:30:31.826Z
---

# Tabs {.tabset}
## Visual Schema 

![signal-2023-03-04-084145_002.png](/signal-2023-03-04-084145_002.png){.align-center}

<a href='https://ko-fi.com/E1E2E81MW' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=3' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

## Objectives

![screenshot_from_2025-01-14_23-20-04.png](/screenshot_from_2025-01-14_23-20-04.png)

## UML

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
@enduml

```