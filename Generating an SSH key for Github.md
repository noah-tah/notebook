## 1. Generate an SSH key

ssh-keygen -t ed25519 -C "your_email@example.com"
- Use your GitHub email for -C.
- Press Enter to accept the default path (~/.ssh/id_ed25519).
- Optionally set a passphrase.

---

## 2. Start the SSH agent and add the key

eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519

---

## 3. Copy the public key

cat ~/.ssh/id_ed25519.pub

Copy the full line (starts with ssh-ed25519).

---

## 4. Add the key in GitHub

1. Open GitHub → Settings → SSH and GPG keys.

2. Click New SSH key.

3. Set a title (e.g. "Arch Linux").

4. Paste the public key.

5. Click Add SSH key.

---

## 5. Test the connection

ssh -T git@github.com

You should see something like: Hi username! You've successfully authenticated...

---

## 6. Use SSH for your repo

If the repo was cloned with HTTPS, switch to SSH:

git remote set-url origin git@github.com:USERNAME/REPO.git

Replace USERNAME and REPO with your GitHub username and repo name.

---

## Quick reference

|Step|Command / action|
|---|---|
|Generate key|ssh-keygen -t ed25519 -C "your_email@example.com"|
|Add key|ssh-add ~/.ssh/id_ed25519|
|Show public key|cat ~/.ssh/id_ed25519.pub|
|Test|ssh -T git@github.com|

You currently have ~/.ssh/known_hosts but no key files, so you’ll need to run step 1 first.