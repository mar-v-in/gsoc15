---
title: GSoC 2015 started - DNSSEC for the Java world
layout: post
category: weekly-report
---

May 25, 2015, a day most do not realize to be special. 
In some european countries, people will remember the date as a holiday.
For 1,051 students from 73 countries it's the official starting shot for a 13 week period to produce awesome, new, open-source software as part of the Google Summer of Code.

I am happy to be able to say, that I was accepted to participate at Google Summer of Code for the XMPP Standards Foundation.
Beginning May 25, I will add full DNSSEC support to the Java DNS client library [minidns](https://github.com/rtreffer/minidns), which will then be used by leading open source libraries and tools including [smack](https://github.com/igniterealtime/smack) and [OpenKeychain](https://github.com/open-keychain/open-keychain).

What happened?
--------------

Wait. You just realized that May 25 is already one and a half way ago? True thing. And there is already nice progress to report

-	minidns is now able to parse DNSKEY, RRSIG, NSEC and DS resource records from the wire (see [RFC 4034](http://tools.ietf.org/html/rfc4034) for details). 
-	As DNSSEC records might contain longer keys and signatures, they do not fit into classic 512 byte DNS packets. I thus added "support" for EDNS (and the OPT resource record), which is able to handle any size of UDP packets the network supports (which is usually about 1500 byte).
-	Unfortunately, 1500 byte UDP packets are not even enough for all use-cases. And it's worth to note that some firewalls restrict the DNS packet size, which renders EDNS useless. I thus also added support for DNS over TCP, which allows arbitrary packet size and should work on every network.

What will happen?
-----------------

When a Google Summer of Code project starts, people are often curious of what they can expect as a result.
Of course a full featured DNSSEC resolver, including recursive resolving abilities is in the offing, but that's not all.

minidns, as the name suggests, is a very light-weight DNS library. Cross-platform compatibility (including support for Android) is also one of its main features. 
Adding DNSSEC support should not touch these features.

And, as this project adds a security-relevant feature, it will also bring-in a full featured test suite to ensure correctness.
This will not only ensure that [everything is awesome](https://www.youtube.com/watch?v=StTqXEQ2l-Y) inside the DNSSEC implementation, but will also be valueable for the complete minidns library.
