---
title: Roadmap
description: OSINTukraine roadmap
published: true
date: 2023-07-02T17:11:02.720Z
tags: roadmap, ideas
editor: markdown
dateCreated: 2023-07-01T12:38:32.732Z
---

# Roadmap of the project

> This page is outdated and will be updated soon.
{.is-info}

- [x] Live DeepL translations using N8N for translation, publication and auto sharing on Twitter, Discord, Telegram
- [x] Provide an API to get access to the content. (get in touch)
- [x] Provide a front-end for Baserow data after dedup process with built-in search, media files
- [x] Provide a Search interface able to search inside each video/media archive site.
- [x] Listen to Telegram channels from the aggregated translated selection and archive them outside of telegram with media files.
- [x] Functional Incremental Sync & Build
- [x] Provide a functional but ugly static HTML site generation with embedded video files and lazy loading of images files.
- [x] Provide an API to get access to the content. (using NocoDB) contact us if you’re interested to build with it.
- [x] Checked task item
- [x] Checked task item

- [ ] Fix Duplicates issues
- [ ] Find ways to measure lengths of enclosure video media files
- [ ] Resync all media files to make sure each video have correct length/size and play/embed fine on any browser.
- [ ] Full revamp of the Static HTML/JS site templates so that we can provide responsiveness, lazy loading of media files, better pagination system
- [ ] Move away from SQLite static database and migrate to live database with new table structure designed for OSINTukraine.
- [ ] Provide a database backend that can be plugged into any front-end (NocoDB or else)


```kroki
mermaid

graph TD
  A[ Anyone ] -->|Can help | B( Go to https://osintukraine.com/en/join )
  B --> C{ How to contribute? }
  C --> D[ Reporting bugs ]
  C --> E[ Sharing ideas & improve the code/nocode]
  C --> F[ Sharing the content ]
  C --> G[ Contributing with donations to expand monitored channels ]
  C --> H[ Triage & curation information ]
  C --> I[ Identify disinformation ]
```
