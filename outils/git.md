
# Git

## Setting up Git

1. Update the system
```bash
sudo apt update && sudo apt upgrade -y
```

2. Install Git
```bash
sudo apt install git
```

3. Setup Git
```bash
git config --global user.name "Name here"
git config --global user.email "email@address.com"
```

4. Enable colored output,
```bash
git config --global color.ui auto
```

5. Generate a SSH key,
```bash
ssh-keygen -t ed25519 -C "email@adress.com"
```

6. Copy the `.pub` SSH key and paste into Github' Settings >> SSH key tab.
```bash
cat ~/.ssh/id_ed25519.pub
```