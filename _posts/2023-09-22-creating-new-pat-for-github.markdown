# Creating a new PAT (Personal Access Token) for github

- Create a new (classic token) here - https://github.com/settings/tokens
- give it a meaningful name
- tick `repo`, `gist` and `workflow` permissions
- Click `Generate token`
- Take a copy of the token before leaving the page
- Open the windows `credential manager`
- Add / Edit the `git:https://github.com` generic credential
  - Internet of network address = `git:https://github.com`
  - Username = `PersonalAccessToken`
  - Password = &lt;token&gt;