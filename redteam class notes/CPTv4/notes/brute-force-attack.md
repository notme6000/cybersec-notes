A **brute force attack** is a hacking method where an attacker tries to guess a password, login key, or encryption key by systematically trying **every possible combination** until the correct one is found.

It’s called “brute force” because it relies on raw computing power rather than clever techniques.

---

## 🔐 How a Brute Force Attack Works

### 1️⃣ Target Selection

The attacker chooses a target:

* Website login page
* Wi-Fi network
* Encrypted file
* Password-protected account

---

### 2️⃣ Generate Possible Combinations

The attacker uses software to automatically generate combinations such as:

If password is 4 digits:

```
0000
0001
0002
...
9999
```

If it's letters:

```
aaaa
aaab
aaac
...
zzzz
```

---

### 3️⃣ Automated Testing

A script or tool tries each combination rapidly:

* Sends login attempts
* Checks if access is granted
* Stops when the correct password is found

Computers can try:

* Thousands to billions of attempts per second (depending on system and protection)

---

## 🧠 Example

If a password is:

```
1234
```

An attacker might try:

```
0000
0001
0002
...
1234 ✅
```

Eventually, they guess correctly.

---

## Types of Brute Force Attacks

1. **Simple brute force** – tries every possible combination
2. **Dictionary attack** – tries common passwords (like `password123`, `qwerty`)
3. **Hybrid attack** – combines dictionary words with numbers (`john123`)
4. **Credential stuffing** – uses leaked username/password combos

---

## ⏳ Why It Works (Sometimes)

Brute force attacks succeed when:

* Passwords are short
* Passwords are common or predictable
* No limit on login attempts
* No account lockout system
* No CAPTCHA or 2FA

---

## 🛡️ How to Protect Against It

* Use **long passwords** (12–16+ characters)
* Include **upper/lowercase, numbers, symbols**
* Enable **Two-Factor Authentication (2FA)**
* Set **account lockout after failed attempts**
* Use **CAPTCHA**
* Use **password managers**

---

# TYPES OF BRUTE FORCE ATTACK

## 1️⃣ Simple Brute Force Attack

**What it is:**
The attacker tries *every possible combination* of characters until the correct password is found.

**How it works:**
If a password is 4 digits, the attacker tries from `0000` to `9999`.

**Example:**
Password: `2589`
Attacker tries:

```
0000
0001
0002
...
2589 ✅
```

✔ Works if the password is short
❌ Very slow for long passwords

---

## 2️⃣ Dictionary Attack

**What it is:**
Instead of trying all combinations, the attacker uses a list (dictionary) of common passwords and words.

**How it works:**
Tries passwords like:

```
password
123456
admin
welcome
```

**Example:**
If someone’s password is `football`, the attacker may find it quickly using a dictionary list.

✔ Faster than simple brute force
❌ Fails if password is unique

---

## 3️⃣ Hybrid Brute Force Attack

**What it is:**
Combines dictionary words with numbers or symbols.

**How it works:**
Takes a word like `john` and tries:

```
john123
john@123
john2025
```

**Example:**
Password: `rahul123`
Attacker tries common names + numbers → finds it.

✔ Very common method
❌ Fails against strong random passwords

---

## 4️⃣ Credential Stuffing

**What it is:**
Uses leaked username/password combinations from previous data breaches.

**How it works:**
If someone used the same password on multiple websites, attackers try it everywhere.

**Example:**
Email: `user@gmail.com`
Password leaked from one site: `mypassword1`
Attacker tries it on banking, social media, etc.

✔ Very effective if people reuse passwords
❌ Prevented by 2FA

---

## 5️⃣ Reverse Brute Force Attack

**What it is:**
Instead of trying many passwords on one account, the attacker tries one common password on many accounts.

**How it works:**
Password tried: `Password123`
Attempted on:

```
user1
user2
user3
...
```

**Example:**
If 10 users use `welcome123`, attacker may gain access to several accounts.

✔ Targets weak users
❌ Blocked by account lockout systems

---

## 6️⃣ Rainbow Table Attack

**What it is:**
Uses precomputed tables of hashed passwords to reverse hashes quickly.

**How it works:**
If the attacker steals encrypted (hashed) passwords, they compare them to a rainbow table.

**Example:**
Hash stolen: `5f4dcc3b5aa765d61d8327deb882cf99`
Rainbow table reveals it = `password`

✔ Fast if hashes are unsalted
❌ Fails if salt is used

---

## 🔒 Summary Table

| Type                | Main Idea                  | Example                         |
| ------------------- | -------------------------- | ------------------------------- |
| Simple              | Try all combinations       | 0000 → 9999                     |
| Dictionary          | Try common words           | password, admin                 |
| Hybrid              | Word + numbers             | john123                         |
| Credential Stuffing | Use leaked passwords       | Try same password on many sites |
| Reverse             | One password on many users | Try “welcome123” everywhere     |
| Rainbow Table       | Crack hashed passwords     | Hash → password                 |

---



