# Multiple SSH Keys for git on Windows

*Note: Feel free to replace "client" with a more meaningful name*

### Create SSH key locally
```
    C:\Users\antony> ssh-keygen -t ed25519 -C "antony@client.com" -f id_client
```

### Add SSH key to github
- Go to [SSH and GPG Keys](https://github.com/settings/keys)
- Click `New SSH Key`
  - Title: a meaningful title
  - Key: the contents of `id_client.pub`
- (optional): Once added, open the `Configure SSO` and authorise for the client's organisation

### Configure git
###### C:\Users\antony\.gitconfig
```
[user]
    name = Antony Scott
    email = 1767144+antony-scott@users.noreply.github.com
[includeif "gitdir/i:C:/Work/Client/"]
    [user]
        name = Antony Scott
        email = antony.scott@client.com
    [url "github.com.client:"]
        insteadOf = git@github.com:
    [core]
        sshCommand = "ssh -i c:/Users/antony/.ssh/id_client"
```

### Configure ssh
###### C:\Users\antony\.ssh\config
```
Host github.com.client
    Hostname github.com
    User git
    AddKeysToAgent yes
    IdentityFile ~/.ssh/id_client
    IdentitiesOnly yes
```

### Summary
The above will have the effect of using the `id_client` SSH key whenever you are
operating in the `C:\Users\antony\Work\Client` folder (or deeper). 

I have combined this with a "personal" SSH key which is stored against my personal github profile, this SSH key will be used whenever I am not under the `C:\Work\Client` folder.

*Note: I have also customised the user email based on the folder location*