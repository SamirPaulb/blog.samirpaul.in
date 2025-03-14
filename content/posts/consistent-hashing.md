---
title: "Consistent Hashing"
description: "Consistent Hashing"
tags: [blog, coding, computer-science, system-design, design-interview, preparation]
date: 2022-10-04T15:58:26+08:00
lastmod: 2022-03-04T15:58:26+08:00
draft: false
author: "Samir Paul"
authorLink: "https://twitter.com/intent/follow?screen_name=SamirPaulb"
license: "CC BY 4.0"
draft: false
---

Consistent Hashing
====

## Simple hashing
Problems of simple hashing function `key % n` (`n` is the number of servers):
- It is not horizontally scalable. Whenever a new cache host is added to the system, all existing mappings are broken.
- It may not be load balanced, especially for non-uniformly distributed data. Some servers will become hot spots.

## Consistent Hashing
- Consistent hashing maps a key to an integer.
- Imagine that the integers in the range are placed on a ring such that the values are wrapped around.
- Given a list of servers, hash them to integers in the range.
- To map a key to a server:
  - Hash it to a single integer.
  - Move clockwise on the ring until finding the first cache it encounters.
- When the hash table is resized (a server is added or deleted), only `k/n` keys need to be remapped (`k` is the total number of keys, and `n` is the total number of servers).
- To handle hot spots, add “virtual replicas” for caches.
  - Instead of mapping each cache to a single point on the ring, map it to multiple points on the ring (replicas). This way, each cache is associated with multiple portions of the ring.
  - If the hash function is “mixes well,” as the number of replicas increases, the keys will be more balanced.

  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-8274401353019049"
     crossorigin="anonymous"></script>
<!-- Display ads -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-8274401353019049"
     data-ad-slot="5522300086"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>