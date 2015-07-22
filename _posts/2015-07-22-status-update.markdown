---
title: Status Update - Finished yet?
layout: post
category: weekly-report
---

It was some work, but finally we reached a state, where DNSSEC in `minidns` is fully usable[*](#what-is-to-be-done).

What happened?
--------------
Summarizing everything done as part of the Google Summer of Code so far gives us a pretty long list of features:

- A full recursive resolver (not only stub resolving)
- TCP and EDNS(0) usage
- Support of a total of 9 new record types: DS, RRSIG, DNSKEY, OPT, NSEC, NSEC3(PARAM), TLSA<sup>NEW</sup>, OPENPGPKEY<sup>NEW</sup>
- Verification of DNSKEY entries using DS
- Verification of RSA signatures using RRSIG
- Verification of negative responses using NSEC and NSEC3<sup>NEW</sup>
- RFC compatible output format (like `dig`)

What is to be done?
-------------------
Testing. Yes that's a main thing to do. 
As announced in this blogs first post, we want our DNSSEC implementation to be fully tested. 
Until now our test coverage is still less than 60%.

Another feature that is missing in the current implementation of `minidns-dnssec`, is verification signatures made using DSA or ECDSA keys.
Currently this is done by a small number of DNSSEC systems and the feature is marked as optional, none the less it is an interesting feature.

Google Summer of Code is still a month to go, so I am certain these problems can be tackled in time and we can see DNSSEC used in `smack` and OpenKeychain until then.
