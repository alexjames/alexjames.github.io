---
layout: default
title:  "Security properties and primitives"
date:   2017-12-11 12:50:00
categories: cs
---

# Security Properties
These are fundamental properties that are used to reason about and analyze higher level constructs. They form the core
principles of security. These definitions are generally accepted. However, some people may choose to define these properties
to mean something completely different. It is good practice to document these definitions when using them in your own work, 
so there is no ambiguity.

### Secrecy/Confidentiality/Privacy
Privacy means to keep your own information secret. For example, I want to keep my age private and never share it with anybody
else. I will never provide any mechanism for anyone other than me to ever have access to this information. A 
system that protects my age from other's accessing it provides me "privacy".

Confidentiality is the obligation to keep someone else's information secret. For example, if X tell's me their phone number,
and I'm in an agreement with X to maintain confidentiality, I cannot reveal their phone number to anyone else.

Secrecy is keeping limiting the number of "principles" who can access some information. This can be thought of as a more general
property protecting information on both ends. For example, if X and Y are communicating, and the secrecy of their communication
is being maintained, then no one can decipher what X and Y are talking about.

### Integrity
Ensuring integrity means to assure that information has not been altered by unauthorized or unknown means. This doesn't necessarily
mean that the information itself cannot be tampered with. It only means that if the information were to be tampered with, we had a
mechanism to determine that this has occured.

It's important to note here that integrity has nothing to do with secrecy. We may have systems where both properties hold, but
they are by themselves, mutually exclusive. You could maintain the integrity of the string "TARTAN" such that if even a single
character were modified, we would know that it has changed. But the string itself does not need to be a secret. 

### Availability

### Anonymity
Anonymity conceals the identity of a participant in a protocol. For example, if you write an anonymous review about a course
at university, there is no way for your professor to figure out the review was by you. Neither should the mechanism of providing
the review reveal your identity in any way, nor should the review that you wrote itself provide an indication as to who you really
are. The onus of the second part completely lies on you. Thus, anonymity in a system can be hard to maintain if the user of the
system themselves provide hints that could single them out.
