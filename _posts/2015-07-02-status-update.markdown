---
title: Status Update - Can you see DNSSEC?
layout: post
category: weekly-report
---

It's again time for a status update, else I got the feeling I will be beaten up and thrown away (or something alike).

What happened?
--------------
`minidns-dnssec` advanced a lot.

- Finally I added support of verifying DNS records.
  This means you can new verify that a record you received is properly signed by the zone owner,
  as long as he as verified ownership to the parent domain zone.
- Support for negative result verification (NSEC) was added as well.
  This feature is used to verify that a record does not exist.
  However most DNS servers implement the successor of NSEC, NSEC3, which is not part of this implementation.
- Obviously fixed a few bugs here and there.

What will happen?
-----------------
The core is done, now we need a huge framework around it:
NSEC3, API stabilization and a lot of tests are still missing to make this project a success.

And finally adding `minidns-dnssec` into applications is also an important part of the project.
We want all this hard work to run in the applications you use everyday, don't we?
