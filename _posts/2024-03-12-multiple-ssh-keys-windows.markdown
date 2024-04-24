---
layout:     post
title:      Multiple SSH Keys for git on Windows
date:       2024-03-12
categories: GitHib,SSH
---
### Create SSH key locally
```
    C:\Users\myname> ssh-keygen -t ed25519 -C "my.name@client1.com" -f id_client1
```

### Add SSH key to github
- Go to [SSH and GPG Keys](https://github.com/settings/keys)
- Click `New SSH Key`
  - Title: a meaningful title
  - Key: the contents of `id_client1.pub`
- (optional): Once added, open the `Configure SSO` and authorise for the client's organisation

### Configure git
###### C:\\Users\myname\\.gitconfig
```
[includeif "gitdir/i:C:/Code/"]
path = ../../Code/.gitconfig

[includeif "gitdir/i:C:/Client1/"]
path = ../../Client1/.gitconfig
```

###### C:\\Personal\\.gitconfig
```
[user]
name = My Name
email = 1234567+my-name@users.noreply.github.com

[github]
user = "my-name"

[core]
sshCommand = "ssh -i c:/Users/myname/.ssh/id_github"
```

###### C:\\Client1\\.gitconfig
```
[user]
name = My Name
email = my.name@client1.com

[github]
user = "myname-client1"

[core]
sshCommand = "ssh -i c:/Users/myname/.ssh/id_client1"
```

### Configure ssh
###### C:\\Users\\myname\\.ssh\\config
```
Host github.com
    Hostname github.com
    User git
    AddKeysToAgent yes
    IdentityFile ~/.ssh/id_github
    IdentitiesOnly yes
    
Host github.com.client1
    Hostname github.com
    User git
    AddKeysToAgent yes
    IdentityFile ~/.ssh/id_client1
    IdentitiesOnly yes
```

### End Result
When using git under the `C:\Personal` folder (or any subfolder)
- email will be `1234567+my-name@users.noreply.github.com`
- SSH key `C:\Users\myname\.ssh\id_github` will be used

When using git under the `C:\Client1` folder (or any subfolder)
- email will be `my.name@client1.com`
- SSH key `C:\Users\myname\.ssh\id_client1` will be used
