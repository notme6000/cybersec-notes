## CSRF (Cross-Site Request Forgery) — Security Notes

### 1. Definition

**CSRF (Cross-Site Request Forgery)** is a web security attack where a malicious website tricks a user’s browser into sending an unauthorized request to another website where the user is already authenticated.

Because the browser automatically includes **cookies, session tokens, or authentication headers**, the target website may process the request as if it came from the legitimate user.



### 2. Key Idea

The attacker **cannot see the response**, but can **trigger actions** on behalf of the victim.

Example actions:

* Change account password
* Transfer money
* Update email
* Delete data



### 3. Basic CSRF Attack Flow

1. User logs into a trusted site (e.g., bank).
2. Server creates a **session cookie** stored in the browser.
3. User visits a **malicious website**.
4. The malicious site sends a **forged request** to the trusted site.
5. Browser automatically includes the **session cookie**.
6. The server processes the request as if the user sent it.



### 4. Example Scenario

User is logged into:

```
https://bank.com
```

A vulnerable request:

```
POST /transfer
amount=10000&to=attacker
```

Attacker creates a malicious page:

```html
<form action="https://bank.com/transfer" method="POST">
  <input type="hidden" name="amount" value="10000">
  <input type="hidden" name="to" value="attacker">
</form>

<script>
document.forms[0].submit();
</script>
```

If the victim visits this page while logged in, the transfer occurs automatically.



### 5. Why CSRF Works

CSRF succeeds because:

* Browsers automatically send **cookies**
* Servers **trust authenticated cookies**
* No verification of **request origin**



### 6. Common Targets

CSRF usually targets **state-changing operations** such as:

* Password change
* Email update
* Financial transactions
* Account deletion
* Profile updates



### 7. CSRF Protection Methods

#### 1. CSRF Token (Most Important)

Server generates a **unique token per session**.

Example:

```html
<input type="hidden" name="csrf_token" value="random123">
```

Server verifies token before processing request.

If token is missing or invalid → request rejected.


### 8. Example with CSRF Token

Form:

```html
<form action="/updateEmail" method="POST">
  <input type="hidden" name="csrf_token" value="xyz987">
  <input type="email" name="email">
  <button>Update</button>
</form>
```

Server validation:

```
if(request.csrf_token != session.csrf_token)
    reject request
```



### 9. CSRF vs XSS

| Feature                 | CSRF                  | XSS               |
| -------------------- | --------------------- | ----------------- |
| Attack type             | Forged request        | Injected script   |
| Requires victim login   | Yes                   | Not always        |
| Attacker reads response | No                    | Yes               |
| Main target             | Authenticated actions | User data/session |






