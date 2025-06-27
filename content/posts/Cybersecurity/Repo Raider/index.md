---
title: "Repo Raider"
date: 2025-06-26T22:27:00-04:00
description: Cool Tool
menu:
  sidebar:
    name: Repo Raider
    identifier: tool
    weight: 20
    parent: cyber
tags: ["Basic"]
categories: ["Basic"]
---

Hey Everyone! 

Last week, I had the opportunity for growth and development. That is, I get a week to be non-billable and get paid to learn and build tools. An absolute dream. And this particular GDT, I had the opportunity to code! I wrote some code to scan code repositories with trufflehog. The issue arose during a pentest, where I found a Github account with several dozen public code repositories. I wanted to check those repositories, but I didnt want to download each one and run trufflehog against it. So I wrote a script to download each repo in the account and run trufflehog against it. Work smarter, not harder. This repo currently supports Github and Docker. Gitlab support has been included, but I haven't added it yet. It will be added shortly and I will probably try to combine everything into one script since there is so much code usage. The repo can be found at https://github.com/Cipolone95/RepoMole. Enjoy! 



