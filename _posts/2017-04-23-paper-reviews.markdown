---
layout: default
title:  "Paper Reviews"
date:   2017-04-23 17:50:00
categories: main
---

Ideas from papers

# Security Challenges in an Increasingly Tangled Web [Deepak Kumar et al.]
  * 90% of websites in the Alexa top million load external content This increases the attack surface and reduces HTTPS adoption.
  * HTTPS adoption is hindered because there maybe an external dependence which is HTTP-only. This stops the entire site from migrating to HTTPS.
  * Data was gathered using a timeout based web crawl. A resource tree was generated.
  * Implicit Trust. If NYTimes trusts DoubleClick and DoubleClick trusts SmartAdServer, then NYTimes implicitly trusts SmartAdServer.
  * 33% of Alexa top million have at least one implicit resource that is loaded.
  * News and Sports sites trust the most resources because of their ad-based monetization models.
  * HTTPS adoption blockers - 40% ad providers, 32% analytics services and 8% social media plugins.
  
# Who Controls the Internet? Analyzing Global Threats using Property Graph  [Milivoj Simeonovski et al.]
  * Uses a property graph to analyze the impact of compromises.
  * This graph is a model of internet infrastructure. Nodes and edges represent key-value pairs.
  * Data was gathered from the RIPE Atlas and by crawling the Alexa top 100k.
  * Graph queries were run on the generated graph. Rules based on different attacks were established. Each rule has a pre-condition and a post-condition.
  * For example, if a mail server is compromised, all connected notes are compromised. If n is compromised and domain m resolves to n, m is also compromised.
  * Taint-propogation -> Starting from initial set I, apply rules till they can no longer apply and look at the extent to which an attack propogates.
  * The final graph had 1.8 million nodes and 4.7 million relationships.
