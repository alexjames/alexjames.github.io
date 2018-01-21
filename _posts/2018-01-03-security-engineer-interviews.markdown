---
layout: default
title:  "Security Engineer Interviews"
date:   2018-01-03 20:56:00
categories: cs
---

I've recently (Jan 2018) been interviewing for security engineer positions. I couldn't find many resources for security interview prep.
Unlike software engineering interviews, there's no Crack The Coding Interview or LeetCode that I'm aware that help with preparing for
interviews for technical security positions. For the most part, I wasn't sure about what to expect. So I spent a lot of time Googling 
through "security interview questions", talked to friends who have interviewed for these positions before and created this list of popular
questions and topics you're expected to know about. I have added my own answers to those questions. This is by no means an exhaustive list,
nor are my answers complete. I'm documenting these primarily for my own reference. You'll likely be hired for your actual competence, than 
your ability to regurgitate security jargon. But you don't want to be in a position where you can't recall how an XSS attack works. A shout-out
to @tnballo for helping me compile and clearly express some of these ideas.

#### XSS - Attack, Types and Defenses
XSS stand for Cross-site scripting. An XSS vulnerability allows an attacker to inject malicious Javascript code into a web application and get
it to execute on your browser. This vulnerability typically exists in web applications that will dynamically generate HTML content. The
attacker provides input which results in executable HTML. For example, the `<script>` tag results in scripts being executed. So if the web application provides a way to input the following text,
you could cause an alert window to pop-up.

```
<script>alert(document.cookie);</script>
```
There are two primary types of XSS attacks: Stored and Reflected. A reflected XSS is when
the malicious script is run via 


Defenses include
  * Escaping and sanitizing input
  * Code-reviews and automated detection tools
  * Use of Content Security Policy


#### CSRF - Attack and Defenses
A Cross Site Request Frogery is when an attacker initiates a malicious request to a victim server via
a session that is already authenticated by the user. This request is indistinguishable from
a legitimate request. These requests are forged via XSS, image tags, links, etc and the user
is tricked into performing them. For example, if after authenticating with a bank's website, the URL request to send money from account
A to account B is `www.bank.com/Transfer?amount=500&dest=dest-account`, an attacker could 
get the victim to execute `www.bank.com/Transfer?amount=500&dest=attackers-account`.

Defenses for CSRF are:
  * Use of a one-time, randomly generated CSRF Token (also known as Synchronizer Token). This may
  be sent/embedded by the server each time a page that allows sending a request is served. The server
  expects the client to send the same CSRF Token back when it makes the request. Thus, an attacker will 
  need to guess this token (assuming they have no way of directly accessing this token) for their
  request to be considered legitimate.
  * Re-authenticating the user via password, CAPTCHA, etc.

Warning: If you have an XSS vulnerabilty, it may be possible to use Javascript to read the CSRFToken.
Thus, for CSRF defenses to work, it is usually imperative that you don't have an XSS vulnerbility.

#### SQL Injection

#### Differentiate between symmetric and asymmetric encryption
Symmetric key algorithms use a single key for encryption and decryption. Asymmetric key algorithms use separate keys for 
encryption and decryption. 



#### Validation vs Sanitization vs Escaping
Validation means to ensure you recive the kind of data you expect to receive. For example, if you expect
to receive an integer, you don't receive a string. If a phone number is supposed to be 10 digits
long, the input provided shouldn't exceed 10 digits.

Sanitization means to remove/convert potentially problematic input. This could mean doing things like:
   * Remove all tags
   * Remove spaces, tabs and whitespaces
   * Remove/convert invalid characters

To escape means to replace bad occurences of dangerous character with safer alternatives. So input 
like `<img>` gets replaced with `&lt;img&gt;`.

Languages will typically provide library functions for performing one or more of the three.

#### Useful Links
https://exploit-exercises.com/
https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project
