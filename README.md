# Windows

## Install chocolatey:

1. Open `cmd.exe` as Administrator:
2. Run:
```
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

## Install choco dependencies
Open PowerShell as Administrator and run:

```
.\windows\install-choco-dependencies.bat
```

## Install WSL
Open PowerShell as Administrator and run:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

Now open Microsoft Store and install Ubuntu 20.04

## Git and GitHub
We need to configure git twice, once for Windows apps like VS Code
and another time for the WSL:
1. Open `Git GUI` and generate an SSH key
2. Add to permitted GitHub SSH keys in GitHub settings
3. Open `Git Bash` windows app
4. Configure git:
```
git config --global user.email "email@example.com"
git config --global user.name "Łukasz Komosa"
```
5. Finally add github.com to `known_hosts`:
```
ssh-keyscan -H github.com >> ~/.ssh/known_hosts
```

Now we configure Git for WSL:
1. Open Hyper, which should open `bash.exe` terminal
2. Generate another key `ssh-keygen`
3. Copy `~/.ssh/id_rsa.pub`
4. Add to permitted GitHub SSH keys in GitHub settings
5. Configure git:
```bash