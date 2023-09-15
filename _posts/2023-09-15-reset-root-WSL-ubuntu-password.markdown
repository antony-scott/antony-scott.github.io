---
layout: post
title:  "How to reset WSL Ubuntu root password"
date:   2023-09-15 15:14 +0100
categories: Windows,WSL
---
# How to reset WSL Ubuntu root password

```bash
    ubuntu2204 config --default-user root
    ubuntu2204
    passwd <username>
    ubuntu2204 config --default-user antony
    ubuntu2204
```

Note - to check username, run `ubuntu2204`, then `cd /home` then `ls -l`, you should see a folder for each user.