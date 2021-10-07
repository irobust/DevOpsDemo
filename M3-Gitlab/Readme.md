# Manage Source Code with GitLab
## Installation
1. Start GitLab server with docker
```
docker run --detach \
  --hostname gitlab.example.org \
  --publish 443:443 --publish 80:80 --publish 22:22 \
  --name gitlab \
  --restart always \
  --volume $(pwd)/config:/etc/gitlab \
  --volume $(pwd)/logs:/var/log/gitlab \
  --volume $(pwd)/data:/var/opt/gitlab \
  gitlab/gitlab-ce:latest
```

2. Get password with this command
```
docker exec -it gitlab cat /etc/gitlab/initial_root_password
docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
```

3. Login with root account

4. Create new admin account
* Go to Menu > Admin
* Select Users and create new account
* Update password (We don't set smtp server yet)
* Sign out and Sign in again (Default config is force user to reset password at first time)

## Git Sub-Module
1. Create main module
1. Create sub module
1. Clone main module
```
git clone http://localhost/[USER-NAME]/main-module.git
```
1. Adding a submodule
```
git submodule add http://localhost/[USER-NAME]/sub-module.git [PATH]/[DIRECTORY-NAME]
```
1. Inspect `.gitmodules`
```
[submodule "[PATH]/[DIRECTORY-NAME]"]
    path = [PATH]/[DIRECTORY-NAME]
    url  = http://localhost/[USER-NAME]/sub-module.git
```
1. Initialize submodule
```
git submodule init
```
1. Grab the content of the submodule
```
git submodule update
```
1. Create branch in sub-module(From Gitlab UI)
1. Checkout new branch
```
cd [PATH]/[DIRECTORY_NAME]
git checkout [BRANCH-NAME]
```
1. Show status of submodule
```
git config --global status.submoduleSummary true
git status
```
1. Temorarily remove
```
git submodule deinit [PATH]/[DIRECTORY_NAME]
```
1. Permanently remove
```
git submodule deinit [PATH]/[DIRECTORY_NAME]
git rm [PATH]/[DIRECTORY_NAME]
git commit -m "Remove submodule"
```
