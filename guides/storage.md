---
layout: default
permalink: /guides/storage
title: Storage Space Fix
---

# Storage Space Fix

At a **Linux terminal prompt** from VSCode (pick any of the following `cs01-cs06`), please run the following commands and make sure to copy and paste the entire command.  


To find and list your VSCode cache files run this:

```shell
find ~ -name '.browse.VC.db' -exec ls -lh "{}" \;
```

To find and delete the cache files run this:

```shell
find ~ -name '.browse.VC.db' -exec rm "{}" \;
```

Then list the file again, you should see a decrease in cache files.

```shell
find ~ -name '.browse.VC.db' -exec ls -lh "{}" \;
```

#### Thank you for your help in freeing up storage space.