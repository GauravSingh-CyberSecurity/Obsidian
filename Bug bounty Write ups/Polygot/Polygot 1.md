
Drop your fav polyglot

Mine is simple and does not test all contexts but is effective:
```
'"><img src=x>${{7*2}}
```

**Explanation**:

- '" : JS injection
- `'">` : html tag attribute
- `<img src=x>` : brokenimage html injection
- '" : SQLi 
- `${{7*2}}` : CSTI and SSTI

This won't give you an XSS or SQLi ... but it might give you an injection point


----
---
---



Chatgpts reply:-

I like your polyglot — it’s elegant, lightweight, and _very effective for context discovery_. Let's break it down:

---

### 💡 Your Polyglot:

```html
'"><img src=x>${{7*2}}
```

---

### 🧠 **Context & Purpose**:

This payload **does not directly exploit** XSS or SQLi or SSTI, but it’s meant to **test whether an injection is possible and _where_**.

It helps in:

- **Discovering injection points**
- **Breaking out of HTML/JS/SQL contexts**
- **Triggering template engines or rendering behavior**

---

### 🔍 **Component-by-Component Breakdown**:

|Part|Purpose|
|---|---|
|`'`|Breaks out of single-quoted strings (often SQL or HTML attributes)|
|`"`|Breaks out of double-quoted contexts|
|`>`|Closes current HTML tag, opens up for HTML injection|
|`<img src=x>`|Inserts a broken image; useful for visual confirmation in reflected responses|
|`${{7*2}}`|Triggers **SSTI/CSTI** template rendering in engines like Jinja2, Handlebars, AngularJS|

---

### 🔥 Why It Works:

This payload is like a **universal probe**. You’re not trying to exploit — you’re **fishing for feedback**.

If the app:

- **Reflects** it back → test for **XSS**
- **Evaluates `${{7*2}}` as `14`** → **CSTI/SSTI** present
- **Breaks HTML layout** → you may have **HTML injection**
- **Logs or crashes** → **error-based SQLi** or server-side processing

---

### ✅ When to Use:

Use it when:

- You're just starting recon on a form, URL, or header
- You want to quickly determine: _What kind of injection am I dealing with?_
- You want to check server-side rendering behavior

---

### 🧪 Tip for Testing:

Use it with:

- Burp Suite Repeater
- Intercepted parameters in POST/GET
- Custom headers (User-Agent, Referer, etc.)
- HTML forms & URL params

---

### 📌 Bonus – A Slightly Enhanced Version:

```html
'"><img src=x onerror=alert(1)>{{7*2}}<svg onload=confirm(1)>
```

> This one actually **executes** basic XSS and still checks SSTI. But your original is better for clean _injection point discovery_.

---

Let me know if you'd like a full set of polyglots for different contexts (XSS, SQLi, SSTI, etc.) or a Burp Intruder wordlist.