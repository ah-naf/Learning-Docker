# Linux Command (Part - 2)

## Environment Variables
---
| Command | Description |
| ------- | ----------- |
| ***env***| Print all the environment variables |
| ***echo $variable_name***| To see the value of an individual variable |
| ***export VARIABLE_NAME=value***| It creates a new environmental variable for the current session |
| ***unset VARIABLE_NAME***| It destorys a variable |

If we set environment variable using **export** it won't persist after closing the session. To persist environment variable even after closing, we have to execute the following commands
```sh
cd ~
# then
echo DB_USER=ahnaf >> .bashrc
```

## Managing Process
---
| Command | Description |
| ------- | ----------- |
| ***ps***| Shows the process for current shell |
| ***kill PID***| Kill the process of id PID  |

## Managing User
---
| Command | Description |
| ------- | ----------- |
| ***useradd [USERNAME]***| Add a new user |
| ***userdel [USERNAME]***| Remove an existing user |
| ***passwd [USERNAME]***| Change the password of the user |