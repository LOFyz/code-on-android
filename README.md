# Setup NodeJS and VS Code in android and make possible to access in PC

## Termux
It will be our terminal emulator and Linux enviroment.

- Get [Termux](https://termux.dev/) on [F-Droid](https://f-droid.org/en/packages/com.termux/) or [GitHub](https://github.com/termux/termux-app#github)
----
## First Steps
1. Setup storage:
```
termux-setup-storage
```
2. Add the repo that we'll use to install VS Code:
```
pkg install tur-repo
```
3. Update packages:
```
pkg update && pkg upgrade -y
```

----
## NodeJS
We will install NodeJS using pkg along with other dependencies required to code-server
```
pkg install -y \
  build-essential \
  binutils \
  pkg-config \
  python3 \
  nodejs-lts
npm config set python python3
node -v
```


----
## VS Code
Since we can't install VS Code in our android, we have to run Code Server, that will create a VS Code instance that we can access in our web browser.

```
pkg install code-server
```
Now we have to create a file to simplify running the code-server:
```
nano code.sh
```
Now type:
```
code-server --bind-addr 0.0.0.0:8080
```
- Then whe select `ctrl` and press `x` in the keyboard, after this we press `y` to save and `enter↵` to finish.
  * The flag `--bind-addr 0.0.0.0:8080` turn you able to access 
  the code-server in lan, through another pc or android. 
  * To define the password that you will insert when open code-server edit the `password` value with `nano ~/.config/code-server/config.yaml`.
  * If you don't want a password to access your code-server, add the flag `--auth none`.

To make the `code.sh` runnable:
```
chmod 777 ./code.sh
```
Now you can run the file `code.sh` and access VS Code in `localhost:8080`, add to home screen if you want to hide browser UI. To access in a PC on the same network, open in the PC browser `"your_android_ip_address":8080`

----
## Optional
Install git and yarn:
```
pkg install -y \
  yarn \
  git
```

Configure your git:

```
git config --global user.name "your_user_name"
```
```
git config --global user.email "your@email.com"
```
