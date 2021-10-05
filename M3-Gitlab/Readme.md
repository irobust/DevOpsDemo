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

## Create Group and Project
