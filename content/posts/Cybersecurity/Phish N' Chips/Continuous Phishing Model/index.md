---
title: Continuous Phishing Model
date: 2026-02-20T04:20:38.916Z
menu:
  sidebar:
    name: Continuous Phishing Model
    identifier: continuous-phishing
    parent: phishnchips
    weight: 20
author:
  name: Pete Cipolone
  image: /images/author/john.png
---

### The Observation
After doing multiple phishing engagements, listening to client feedback, and having a customer pay to build phishing infrastructure for them, I've come to the realization that Phishing/Social Engineering pentest should move to a continuous subscription model and not just a point-in-time test. I still think point-in-time phishing engagements are a good thing, but I believe there is a huge value add for the client to phish throughout the year. Over the past couple of weeks, I have been building out the continuous phishing model. It is still in the rough draft stage, but the implementation is going to look like something below.   

### The Implementation
The continuous phishing model would look something like this:
- One full week phishing engagement. This includes:
  - Multiple credential harvesting campains
  - Full post-exploitation (seeing how far we can go in your environment if we get access)
  - Review of Email defenses such as looking at SMTP records, testing for SMTP open relays, attempt email spoofing, etc.   
- Additional Phishing campaings (approximately 2-3 months)
- Send emails based upon levels: beginner, intermediate, and advanced to measure progress. 
- Potential for add-ons such as:
  - Voice Phishing
  - OSINT Review (collect emails, fuzz email addresses formats, validate emails, check associated domains, high lighting social media posts that would enable good phishing pretexts)
  - Spear Phishing
  - Special Requests

### The Difference In Benefit
What I have found is that phishing throughout the year would give an organization a better idea of their security posture when it comes to phishing. The drawbacks with the point-in-time phishing are:
- People usually talk when they receive a phishing email so multiple campaings in a single week will have skewed results. 
- Some of the most effective phishing campaigns can't be used becaues they are time/event dependent. For example, employees can't take a benefits survey unless benefits enrollment is coming up. 
Phishing throughout the year solves both of these challenges and more. 

### Inconclusion
In conclusion, I am sure this phishing model will change as it develops, but I'm excited to see where it goes. Need a phishing engagement? Feel free to reach out at pete@petercipolone.info and I can get you in touch with the right people. 



