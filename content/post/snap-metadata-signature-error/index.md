---
title: "How To Solve An Error in Linux: 'cannot find signatures with metadata for snap'"
description: 
date: 2024-06-29T02:04:19Z
math: 
comments: true
draft: true
tags: 
    - snap
    - linux
    
categories:
    - debugging
---

<br><br>

When I tried to [VoTT](https://github.com/microsoft/VoTT) using snap on Linux, I got an error: 
```
error: cannot find signatures with metadata for snap "vott-2.2.0-linux.snap"
```
...What do you mean "signature"..??
The reason why this error is caused is because [Since I'm installing a local snap, I have no assertions for it, and snap doesn't trust it](https://askubuntu.com/questions/822765/snap-install-failure-error-cannot-find-signatures-with-metadata-for-snap).
OK, not helpful error at all. 
Anyway, the solution is adding @--dangerous@ flag. 

```
snap install --dangerous  vott-2.2.0-linux.snap 
```

it woked!

