Got it 👍 This is a **very common GitHub SSH issue**, nothing wrong with your commands.
The error is clear:

> **`git@github.com: Permission denied (publickey)`**

👉 GitHub is **not able to find your SSH key** on your system or in your GitHub account.

Let’s fix it step-by-step (simple + safe).

---

## ✅ Why this error happens

You’re using this remote:

```bash
git@github.com:saikishore8106/MLProjects.git
```

That means GitHub expects **SSH authentication**, but:

* SSH key is **not created**, or
* SSH key is **not added to GitHub**, or
* SSH agent is **not running**

---

## ✅ Step 1: Check if SSH key already exists

Run:

```bash
ls ~/.ssh
```

If you see files like:

* `id_rsa` & `id_rsa.pub` **OR**
* `id_ed25519` & `id_ed25519.pub`

👉 Skip to **Step 3**

If folder is empty or not found → go to Step 2.

---

## ✅ Step 2: Create a new SSH key

Run this (recommended):

```bash
ssh-keygen -t ed25519 -C "your_email@gmail.com"
```

Press **Enter** for all questions (don’t add password unless you want).

This creates:

```
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

---

## ✅ Step 3: Start SSH agent & add key

Run:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

You should see:

```
Identity added
```

---

## ✅ Step 4: Add SSH key to GitHub

Copy your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Now:

1. Open **GitHub**
2. Go to **Settings → SSH and GPG keys**
3. Click **New SSH key**
4. Title: `My Laptop`
5. Paste the copied key
6. Save

---

## ✅ Step 5: Test SSH connection

Run:

```bash
ssh -T git@github.com
```

Expected output:

```
Hi saikishore8106! You've successfully authenticated.
```

---

## ✅ Step 6: Push again

Now retry:

```bash
git push -u origin main
```

✅ This time it will work.

---

## 🔁 Quick alternative (HTTPS – easiest)

If you don’t want SSH at all:

```bash
git remote remove origin
git remote add origin https://github.com/saikishore8106/MLProjects.git
git push -u origin main
```

GitHub will ask for:

* **Username**
* **Personal Access Token** (not password)

---
