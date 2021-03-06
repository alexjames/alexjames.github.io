---
layout: default
title:  "Security Properties and Mechanisms"
date:   2017-12-11 12:50:00
categories: cs
---

# Security Properties and Mechanisms
Security properties are fundamental properties that are used to reason about and analyze the security characteristics of computer 
systems. You will come across them pretty often, especially in academic literature. What a property entails is a loosely defined term.
Different people may choose to define these properties to encompass different things. Here I'll describe some generally accepted definitions
for some of these properties. It is good practice to document your definitions for security properties when using them in your own work, so
there is no ambiguity.

### Secrecy/Confidentiality/Privacy
Privacy means to keep your own information secret. For example, I want to keep my age private and never share it with anybody
else. I will never provide any mechanism for anyone other than me to ever have access to this information. Per this example, a 
system that stores my age and never allows anyone other than me from accessing it provides me "privacy".

Confidentiality is the obligation to keep someone else's information secret. For example, if X tells me their phone number,
and I'm in an agreement with X to maintain confidentiality, I cannot reveal their phone number to anyone else. Likewise, an attorney
maintains the confidentiality of their clients.

Secrecy is limiting the number of "principles" who can access some information. This can be thought of as a more general
property protecting information on both ends. For example, if X and Y are communicating, and the secrecy of their communication
is being maintained, then no one other than X and Y can decipher what is being communicated.

### Integrity
Ensuring integrity means to assure that information has not been altered by unauthorized or unknown means. This doesn't necessarily
mean that the information itself cannot be tampered with. It only means that if the information were to be tampered with, we have a
mechanism to determine that the tampering has occurred. That the "integrity" of the message has bee lost.

It's important to note here that integrity has nothing to do with secrecy. We may have systems where both properties hold, but
they are by themselves, mutually exclusive. You could maintain the integrity of the string "TARTAN" such that if even a single
character was modified, we would know that it has changed. But the string itself does not need to be a secret. Similarly, a hard-disk may
employ bit parity checks to ensure that data corruption is detectable.

### Availability
Availability is the ability of a system to perform its functions. If a system is under more load than it can handle, it may
stop functioning correctly and we have the loss of availability. Attacks such as DOS (denial of service) target the availability
property of a system.

### Identification
Identification means corroborating the identity of an entity. For example, your driver's license is used to identify you at the airport.

### Authentication
The authentication security property stands for "message-origin" authentication. i.e. validating that a message has come
from a particular principle. This is a little different from the common use of the term "authentication". The colloquial usage
involves corroborating both authentication and identity. For example, if Alex sends you a message, you verify that the message has 
in-fact come from Alex and Alex is who he says he is. 

An example would be that you could verify the origin of a phone call by checking the person's caller ID. You "authenticate" Alice
by verifying her caller ID. You "identify" Alice by the sound of her voice, or by asking the person on the line a question whose answer only
Alice would know like - "What movie did we go to last week?". It's possible for me to take Alice's phone and call you. You'll still see 
Alice's caller ID on your phone. But it's not Alice who is calling you. This is an example of authentication without identification. The
difference between authentication and identification is subtle. Identification and "message-origin" authentication are both same sides of
the authentication coin (quote courtesy: Nicholas Cristin). In the context of data communication, one usually does not make sense without
the other.

### Authorization
This is granting an entity the ability to perform an action. For example, Alice is only authorized to access the first and second
floors of a building.

### Non-repudiation
Repudiation means "the rejection of an idea or proposal". The non-repudiation property ensures that a principle cannot deny an action
after having performed it. For example, if Bob signs a contract, they cannot later claim that they did not sign the contract. A
mechanism that provides non-redupidation will ensure that if Bob denies having performed an action, the fact can be verified.

### Anonymity
Anonymity conceals the identity of a participant in a protocol. For example, if you write an anonymous review about a course
at university, there is no way for your professor to figure out the review was by you. Neither should the mechanism of providing
the review reveal your identity in any way, nor should the review that you wrote provide an indication as to who you really
are by itself. The onus of the second part completely lies on you. This is why anonymity in a system can be hard to maintain. Users of the
system themselves might provide hints that could single them out. For example, if you're discussing your salary details in an anonymous
forum, and you mention the company/organization/manager you work for, it might become possible for someone to figure out who you are.

### An analogy
Let's try to formulate a small analogy to tie all these properties together. Let's assume that the system is fool-proof for 
simplicity. You are trying to enter a super secret government base. At the gate, the guard asks you for papers. You show them
a document saying that you've been authorized to enter the base for a day by the General. The document is completely written in some secret
code so that the purpose of the document and who it belongs to is unknown. This maintains secrecy. 

The guard says "I'll have that" and passes the paper into a scanner. The scanner verifies the integrity of the document so that the 
guard knows that the document was not tampered with. An example of what tampering here might look like would be that you try to change
your visit date to the base to be the 15th of December, instead of the 17th. So if you tried modifying the document to refer to an earlier
date than was originally intended when the document was handed to you, the scanner would detect this. The scanner now decrypts the document
contents to reveal the un-encrypted plaintext. The guard recognizes a seal in the contents as coming from the administrative office within
the base. The document is now authenticated. The scanner itself is "available" so you can't jam the scanner and make it unusable.

But anyone from the administrative office could have created this document, even someone not
allowed to grant you access. How do we know that the General specifically oversaw this document? This is because the guard
sees the General's signature on it. This authenticates the document. The guard knows that when the
General signed the document, the event was logged on an internal ledger. The General cannot later deny having granted you access. This is
how non-repudiation is provided. "Hmmnnn" says the guard. 

The document has your name and government ID number on it. The guard asks you for your ID card. You show it to them and they
use it to verify your identity. You picture matches the picture in your ID card and your ID number matches that on the paper. 
The guard finally breathes a sigh of relief, says "Mr. X, you are now clear to enter our super-secret base to do super-secret things" and
lets you through.
