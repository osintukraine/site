---
title: Vision
description: If we had unlimited means and funds to push OSINTukraine further, where could it go ?
published: true
date: 2023-08-10T08:42:35.039Z
tags: ideas, vision, potentiality
editor: markdown
dateCreated: 2023-08-10T08:07:01.494Z
---

# Just Ideas
> But, if we had unlimited funds/means/capacity to push the ideas behind OSINTukraine further, where could it go ? what could be possible?

## Data [Analysis](/research)

- use Machine Learning on the **text** data to infer quality signal to noise information that could be useful to Ukraine
- use Computer Vision and AI models to scan all the **Video** data and look for potential geolocation position, videos that could be useful to infer actionable information, military equipment, troops movements, anything of importance in ennemy provided videos that could help identify targets for Ukraine
- a better and more accurate alert system allowing us to spot interesting piece of information in the overall archive (nearly 2 years of telegram posts and videos is a LOT of data (around 20TB now)

## Data [Enrichment](/research)
- Flag disinformation using ML & human supervision
- Tag data rows with location, units, equipment
- Define a set of OSINT markers that could be used to train a AI model to enrich the data and provide an interface to use the resulting output

## Interface [Design](/archive)

- a Complete rework of the front-end for the telegram video & text archives
- Unified interface to search and consult all the data available


## Architecture [diagram](/diagram) 
- redesign everything from scratch, use code where necessary coupled with nocode solution (as of now) but better integrated and with duplicates detection, better redundancy, less technical debt, better documentation etc..
- build an iteration of this project tuned to be deployed on other usecases

## Service
- Allow the system to enable users configuration such as custom alerts, custom webhoook to forward a segment of the data to different third-party service. 
- Provide a full fledged API to build other tools on top of the data





