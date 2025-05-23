---
title: "ARTE (AWS Red Team Expert) Review"
date: 2020-06-08T08:06:25+06:00
description: ARTE Exam Reivew
menu:
  sidebar:
    name: ARTE Exam Review
    identifier: arte
    weight: 20
    parent: cyber
tags: ["Basic"]
categories: ["Basic"]
---

Hi Everyone! 
I recent passed the ARTE (AWS Red Team Expert) certification and I wanted to write a short blurb on the course, the exam, and the entire experience. As with most things I say, these thoughts are my own and don’t necessarily reflect those of my employer, HackTricks, my religion, or anybody/anything else. 

**Background:** I am a pentester and have done cloud reviews before so some topics were a review for me. Additionally, I have the pentester mindset so I came into the course with the ability to enumerate well, think critically, and know when I am going down a rabbit hole. 

**Course:** The course is composed of a series of videos and labs covering 20 or so different AWS services. It was usually about one video and then 1-3 labs per topic. The length of the video is dependent on the popularity of the AWS service. For example, the video covering iam is way more in-depth than the video covering sns. I did not really care for the videos and I feel like I didn’t learn much from them. The quality and structure of the videos could have been better, but I am also not a video learner, so it is probably a “me” issue. The real benefit of the course is the labs. 

**Labs:** The labs were great! Each lab consisted of a misconfiguration where the attacker (you) could escalate privileges to retrieve a flag from the secrets manager. I like this approach because of its simplicity in learning the misconfiguration. However, this simplicity also led to some bad habits. In each individual lab, I could read the user’s policy and correlate the permissions to a misconfiguration in the HackTricks wiki. In many real-life cases, you can’t do this and you have to brute force the user’s permissions to see what they can do. So I struggled in the black box labs. The black box labs are three labs at the end of the course that give you the opportunity to use everything you learned. Each lab consists of multiple privesc techniques that must be done in order to reach the final flag. However, you must discover the privesc techniques and you can’t always read the policy so a lot of privilege enumeration must be done. The black box labs are what the exam is like so don’t skip them! 

**Exam:** The exam is straight forward: find three flags in 12 hours in an AWS environment. It is important to explore everything and not just follow the “Happy Path” of privilege escalations. Everything in my exam was covered in the labs so I was good to go. When I went through the labs, I made a list of each command I ran in order to solve each lab and wrote some notes on my observations. This will be helpful during the exam. 

**Extra Resources:** This was my first introduction with AWS hacking so sometimes things did not click right away. Since I struggled so badly in the black box labs, I also did some AWS labs in PwnedLabs and did the Electra cyber range. If you can complete Electra, you are more than ready for the exam. 

**Final Thoughts:** I would rate my entire experience 8/10. I learned a lot about AWS and I feel very comfortable doing an AWS pentest. The course videos could have been better, but the labs were great. You do get lifetime access to the course, however, that just applies to the videos and not the lab time. I thought the exam was really well done and overall the price point was sufficient.  



