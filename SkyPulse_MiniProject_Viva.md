# 🌤️ SkyPulse Weather Dashboard — Complete Viva Preparation Guide
### Mini Project | CSL605 Cloud Computing | Mumbai University Sem VI

> **This file is 100% focused on your mini project.**
> Every question here is what an external examiner WILL ask when they look at your project.
> Read it like a conversation — question → your answer → the "why" behind it.

---

## 📌 QUICK PROJECT IDENTITY CARD
*(Memorise this — this is your opening statement)*

| Field | Detail |
|---|---|
| **Project Name** | SkyPulse — Live Weather Dashboard |
| **Type** | Real-time web application deployed on AWS |
| **Frontend** | HTML5 + Vanilla CSS (Glassmorphism) + Vanilla JavaScript |
| **Backend** | AWS Lambda (Python 3.12) |
| **API** | Amazon API Gateway (REST) |
| **Storage / Hosting** | Amazon S3 (Static Website Hosting) |
| **External Data** | OpenWeatherMap API (free tier) |
| **Security** | IAM Role for Lambda, Environment Variable for API key, CORS headers |
| **Monitoring** | AWS CloudWatch (auto-logs every Lambda invocation) |
| **Cost** | Rs.0 — Entirely within AWS Free Tier |
| **Region** | ap-south-1 (Mumbai) |
| **Lambda function name** | `skypulse-weather` |
| **API Gateway name** | `skypulse-api` |
| **API Endpoints** | `/weather?city=` and `/forecast?city=` |

---

## TABLE OF CONTENTS

1. [Opening Questions — Project Overview](#overview)
2. [Architecture Deep Dive](#architecture)
3. [AWS Services — Detailed Q&A](#aws-services)
4. [The Lambda Function — Code Questions](#lambda)
5. [The Frontend — Code Questions](#frontend)
6. [Security Questions](#security)
7. [Cloud Concepts Demonstrated](#cloud-concepts)
8. [Limitations & Improvements](#improvements)
9. [Tough / Tricky Questions](#tough)
10. [Your 60-Second Pitch (Memorise This)](#pitch)
11. [Quick Facts Revision Table](#facts)

---

## SECTION 1 — OPENING QUESTIONS (Project Overview) {#overview}

### Q1. What is your mini project? Explain it in simple terms.

**Answer:**
SkyPulse is a real-time weather dashboard web application. A user visits the website, types in any city name — say "Mumbai" or "London" — and the app instantly shows:
- Current temperature (with degree C / degree F toggle)
- Weather condition (clear sky, rain, clouds, etc.)
- Humidity, wind speed, visibility, pressure, cloud cover
- Sunrise and sunset times
- A 5-day daily forecast
- A 12-hour hourly outlook

The entire application is hosted on **Amazon Web Services (AWS)** using only the **Free Tier** — meaning it costs Rs.0 per month. The design uses a **glassmorphism** style with a dark background that changes colour based on the weather condition.

---

### MOST LIKELY Q2. Which cloud services did you use and why?

| AWS Service | Role in Project | Why this service? |
|---|---|---|
| **S3** | Hosts the frontend (HTML, CSS, JS) | S3 can serve static files as a website — no web server needed |
| **API Gateway** | Creates the REST API endpoint | Managed, scalable HTTP endpoint that triggers Lambda |
| **Lambda** | Backend logic — calls OpenWeatherMap API | Serverless, zero cost for light use, keeps API key secret |
| **IAM** | Gives Lambda permission to run and log | Security best practice — least privilege |
| **CloudWatch** | Logs every Lambda call automatically | Monitoring and debugging |

---

### MOST LIKELY Q3. Why did you choose AWS for this project?

**Answer:**
1. **Free Tier** — S3, Lambda, and API Gateway are all free for student project usage levels (1M Lambda invocations/month, 5GB S3 storage, 1M API Gateway calls/month)
2. **Mumbai Region (ap-south-1)** — Low latency for Indian users
3. **Best documentation and tutorials** — Largest community
4. **Real-world relevance** — AWS has 33% cloud market share
5. **Covers all syllabus concepts** — IaaS, PaaS, Storage, Security, Serverless

---

### MOST LIKELY Q4. Which real-world cloud concepts does your project demonstrate?

| Concept | Where in your project |
|---|---|
| **IaaS** | EC2 compute powers Lambda underneath (abstracted) |
| **PaaS** | Lambda + API Gateway = managed platform, zero server config |
| **SaaS** | SkyPulse itself is software delivered as a service |
| **Storage as a Service** | S3 stores and serves the entire frontend |
| **Serverless / FaaS** | Lambda — no server provisioning |
| **Security as a Service** | IAM roles, CORS, API key protection via env variable |
| **Measured Service** | Pay per Lambda invocation, tracked usage |
| **On-demand** | Any user anywhere can instantly access it |
| **Broad Network Access** | Accessible from any browser, any device |
| **Elasticity** | Lambda auto-scales from 0 to millions with zero manual effort |

---

## SECTION 2 — ARCHITECTURE DEEP DIVE {#architecture}

### MOST LIKELY Q5. Draw and explain the architecture of your project.

**Architecture (speak this while drawing):**

```
USER'S BROWSER
      |
      | Step 1: User visits S3 website URL
      v
AMAZON S3 — Static Website Hosting
  Bucket: skypulse-weather-dashboard
  Files: index.html, style.css, app.js
      |
      | Step 2: JS runs in browser, user types city and clicks Search
      | Step 3: JS fires two parallel fetch() calls to API Gateway
      v
AMAZON API GATEWAY — REST API (prod stage)
  GET /weather?city={city}
  GET /forecast?city={city}
  Integration: Lambda Proxy
      |
      | Step 4: API Gateway triggers Lambda
      v
AWS LAMBDA — skypulse-weather (Python 3.12)
  Reads city from query params
  Reads API key from environment variable (never from code)
  Calls OpenWeatherMap API
      |
      | Step 5: Calls external weather API
      v
OPENWEATHERMAP API (external)
  Returns JSON with temperature, humidity, wind, forecast, etc.
      |
      | Data flows back: Lambda -> API Gateway -> Browser
      v
Browser renders weather data on screen
```

**In one sentence:** Browser gets the HTML/CSS/JS from S3, then JavaScript calls API Gateway which triggers Lambda, which securely calls OpenWeatherMap and returns weather JSON.

---

### MOST LIKELY Q6. Why is this called a 3-tier architecture?

| Tier | Component | What it does |
|---|---|---|
| **Presentation Tier** (Front-end) | S3 (HTML + CSS + JS) | What the user sees and interacts with |
| **Application / Logic Tier** (Back-end) | API Gateway + Lambda | Processes requests, calls external API, applies logic |
| **Data Tier** | OpenWeatherMap API | Provides the actual weather data |

This is classic **3-tier web architecture**, implemented fully on AWS cloud services instead of traditional servers.

---

### Q7. What is a "serverless" approach? Why is Lambda serverless?

**Answer:** Serverless means **you don't manage any server**. AWS handles:
- Provisioning servers
- OS installation and patching
- Scaling (automatically runs more copies when traffic increases)
- Fault tolerance

Lambda is serverless because:
- No EC2 to launch, no OS to configure
- You just upload the Python file
- It runs on demand — only when called via API Gateway
- You pay per 100ms of execution time (not 24/7)

**Important**: "Serverless" doesn't mean no server exists — it means YOU don't see or manage any server.

---

### Q8. What is the region ap-south-1?

**Answer:** `ap-south-1` is the AWS region code for **Asia Pacific (Mumbai)**. We chose it because:
- Lowest latency for Indian users (data stays geographically close)
- Compliance — data stays within India
- All needed services (S3, Lambda, API Gateway) are available here
- Same region for all services = no cross-region data transfer costs

---

### Q9. What happens if OpenWeatherMap API is down?

**Answer:** The Lambda function uses `try-except` error handling:
```python
try:
    with urllib.request.urlopen(req, timeout=8) as resp:
        data = resp.read()
    return {"statusCode": 200, ...}
except urllib.error.HTTPError as e:
    return _error(e.code, msg)   # e.g., 404 city not found
except Exception as e:
    return _error(500, f"Internal error: {str(e)}")
```

The frontend catches the error in `fetchWeather()` and shows a **red error banner** to the user. The app never crashes — it handles failures gracefully at every layer.

---

## SECTION 3 — AWS SERVICES DETAILED Q&A {#aws-services}

### MOST LIKELY Q10. Explain exactly what you did in Amazon S3.

**Answer — Exact steps we performed:**
1. Created bucket named `skypulse-weather-dashboard` in `ap-south-1`
2. **Unchecked "Block all public access"** — so the public can view the website
3. Uploaded 3 files: `index.html`, `style.css`, `app.js`
4. Went to **Properties → Static website hosting → Enable**
5. Set `index.html` as the **Index document**
6. Added a **Bucket Policy** to allow `s3:GetObject` for `Principal: "*"` (everyone)
7. Got the **website endpoint URL** — this is the app's public address

**Bucket Policy we used:**
```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Sid": "PublicReadGetObject",
    "Effect": "Allow",
    "Principal": "*",
    "Action": "s3:GetObject",
    "Resource": "arn:aws:s3:::skypulse-weather-dashboard/*"
  }]
}
```

**Key point**: With Static Website Hosting enabled, S3 acts as a web server — serving `index.html` when someone hits the URL. **No Apache, Nginx, or EC2 needed.**

---

### MOST LIKELY Q11. Explain exactly what you did in AWS Lambda.

**Answer — Exact steps we performed:**
1. AWS Console > Lambda > **Create Function**
2. Name: `skypulse-weather`, Runtime: **Python 3.12**, Architecture: x86_64
3. Pasted the code from `lambda/weather_lambda.py`
4. Clicked **Deploy** to save the code
5. Went to **Configuration > Environment variables > Edit**
6. Added: Key = `OWM_API_KEY`, Value = [the actual OpenWeatherMap API key]
7. Lambda auto-created an **IAM execution role** with CloudWatch Logs permissions

**What does Lambda do?**
Receives HTTP request from API Gateway → reads `city` param → appends secret API key → calls OpenWeatherMap → returns JSON response with CORS headers.

---

### MOST LIKELY Q12. Explain exactly what you did in API Gateway.

**Answer — Exact steps we performed:**
1. Console > API Gateway > **REST API > Build**
2. Created API named `skypulse-api`

3. **Created `/weather` resource:**
   - Actions > Create Resource > name: `weather`
   - With `/weather` selected > Create Method > `GET`
   - Integration type: **Lambda Function** > `skypulse-weather`
   - Enabled **Lambda Proxy Integration**

4. Created `/forecast` resource — same steps

5. **Enabled CORS** on both resources:
   - Actions > Enable CORS > Replace existing CORS headers

6. **Deployed the API:**
   - Actions > Deploy API
   - Stage: `prod`
   - Got the **Invoke URL**: `https://kf7n4k0a4d.execute-api.ap-south-1.amazonaws.com/prod`

7. **Updated `app.js`** with this Invoke URL in `CONFIG.LAMBDA_BASE_URL`

---

### Q13. What is "Lambda Proxy Integration" in API Gateway?

**Answer:** When Proxy Integration is ON, API Gateway passes the **entire HTTP request** to Lambda as a JSON event object, and Lambda returns the **entire HTTP response** (status code + headers + body).

Lambda receives:
```json
{
  "httpMethod": "GET",
  "path": "/weather",
  "queryStringParameters": { "city": "Mumbai" }
}
```

Our Lambda reads: `params = event.get("queryStringParameters") or {}`, then `city = params.get("city", "")`.

---

### Q14. What is a "Stage" in API Gateway?

**Answer:** A Stage is a **named snapshot of your deployed API** — like a version label. You can have `dev`, `test`, `prod` stages.

We deployed to `prod` — this generated the invoke URL ending in `/prod`. This stage path is part of every API call URL.

---

### Q15. What is AWS CloudWatch and how does it link to your project?

**Answer:** CloudWatch is AWS's monitoring service. For our project, every Lambda invocation is **automatically logged** to CloudWatch Logs (Log group: `/aws/lambda/skypulse-weather`).

Logs include: which city was searched, how long Lambda ran, memory used, any errors. This was automatically set up when Lambda's IAM role had the `AWSLambdaBasicExecutionRole` policy — we didn't configure it manually.

---

## SECTION 4 — THE LAMBDA FUNCTION (Code Questions) {#lambda}

### MOST LIKELY Q16. Explain your Lambda function code.

**(Walk through this file: `lambda/weather_lambda.py`)**

```python
import json        # For JSON encoding error responses
import os          # To read environment variables
import urllib.request  # Built-in HTTP client
import urllib.parse    # URL encoding city names (spaces etc.)
import urllib.error    # For catching HTTP errors

OWM_BASE = "https://api.openweathermap.org/data/2.5"
API_KEY  = os.environ.get("OWM_API_KEY", "")
# API_KEY is read from Lambda environment variables — NEVER hardcoded in code

CORS_HEADERS = {
    "Access-Control-Allow-Origin":  "*",
    "Access-Control-Allow-Headers": "Content-Type",
    "Access-Control-Allow-Methods": "GET,OPTIONS",
    "Content-Type": "application/json",
}

def lambda_handler(event, context):
    # Handle CORS preflight (browser sends OPTIONS before GET)
    if event.get("httpMethod") == "OPTIONS":
        return {"statusCode": 200, "headers": CORS_HEADERS, "body": ""}

    path   = event.get("path", "/weather")   # /weather or /forecast
    params = event.get("queryStringParameters") or {}
    city   = params.get("city", "").strip()  # e.g., "Mumbai"

    if not city:
        return _error(400, "Missing 'city' query parameter")

    if not API_KEY:
        return _error(500, "API key not configured.")

    # Route to correct OWM endpoint
    if "/forecast" in path:
        owm_path = f"/forecast?q={urllib.parse.quote(city)}&appid={API_KEY}&cnt=40"
    else:
        owm_path = f"/weather?q={urllib.parse.quote(city)}&appid={API_KEY}"

    url = OWM_BASE + owm_path
    req = urllib.request.Request(url, headers={"User-Agent": "SkyPulse/1.0"})

    try:
        with urllib.request.urlopen(req, timeout=8) as resp:
            data = resp.read().decode("utf-8")
        return {"statusCode": 200, "headers": CORS_HEADERS, "body": data}
    except urllib.error.HTTPError as e:
        body = e.read().decode("utf-8")
        msg = json.loads(body).get("message", str(e))
        return _error(e.code, msg)
    except Exception as e:
        return _error(500, f"Internal error: {str(e)}")

def _error(code, message):
    return {
        "statusCode": code,
        "headers": CORS_HEADERS,
        "body": json.dumps({"error": message}),
    }
```

---

### MOST LIKELY Q17. Why did you use `urllib` instead of `requests` in Lambda?

**Answer:** `urllib` is part of Python's **standard library** — it is available in every Python environment without any installation. Using `requests` in Lambda requires packaging it as a **Lambda Layer** or zipping it with the function code — extra complexity. For a simple HTTPS call, `urllib` works perfectly and keeps the Lambda **zero-dependency**.

---

### Q18. Why do you use `urllib.parse.quote(city)`?

**Answer:** City names can contain spaces or special characters. `quote()` converts them to URL-safe format:
- `"New York"` becomes `"New%20York"`
- `"Sao Paulo"` becomes `"Sao%20Paulo"`

Without this, the URL would be malformed and OpenWeatherMap would reject the request.

---

### MOST LIKELY Q19. What is `os.environ.get("OWM_API_KEY", "")` doing?

**Answer:**
- `os.environ` is Python's dictionary of **environment variables** (key-value pairs set at the OS level)
- `os.environ.get("OWM_API_KEY", "")` reads the variable named `OWM_API_KEY`
- If it is not set, it returns `""` as default
- The actual API key is injected **at runtime by Lambda** from its encrypted environment variable store
- Even if someone reads the code, they cannot see the API key — it is never in the source

---

### Q20. What does the `_error` helper function do?

**Answer:** It creates a **standardized error response** that:
1. Returns the right HTTP status code (400, 404, 500, etc.)
2. Always includes CORS headers — so even error responses don't break the browser
3. Returns the error as `{"error": "message"}` JSON — consistent format

This is good API design principle: **consistent response format for both success and failure**.

---

### Q21. What is `cnt=40` in the forecast URL?

**Answer:** `cnt` = count. It tells OpenWeatherMap to return **40 data points** of 3-hourly forecast data.

40 points × 3 hours = 120 hours = exactly **5 days** of data.

The free OWM plan supports a maximum of 40 data points. We use this data for both the 5-day daily forecast (aggregated) and the 12-hour hourly display (first 12 points).

---

## SECTION 5 — THE FRONTEND (Code Questions) {#frontend}

### MOST LIKELY Q22. Explain the CONFIG block in app.js.

```javascript
const CONFIG = {
  USE_LAMBDA: true,           // true = production (AWS), false = local dev
  OWM_API_KEY: '...',         // Used only for local testing (not AWS)
  LAMBDA_BASE_URL: 'https://kf7n4k0a4d.execute-api.ap-south-1.amazonaws.com/prod',
  OWM_BASE_URL: 'https://api.openweathermap.org/data/2.5', // For local testing
};
```

**Answer:** This is a **dual-mode switch** for the app:
- `USE_LAMBDA: true` — Production mode: all calls go through API Gateway to Lambda
- `USE_LAMBDA: false` — Local dev mode: calls go directly to OWM (key in JS file — only for local testing, never pushed to production)

**Why is this useful?** We can test the frontend locally without needing AWS at all. One config change switches the entire app between environments.

---

### MOST LIKELY Q23. How does `fetchWeather()` work?

```javascript
async function fetchWeather() {
  const city = input.value.trim();
  if (!city) { showError('Please enter a city name.'); return; }

  showLoading(true);
  closeError();

  try {
    [current, forecast] = await Promise.all([
      apiFetch(`${CONFIG.LAMBDA_BASE_URL}/weather?city=${encodeURIComponent(city)}`),
      apiFetch(`${CONFIG.LAMBDA_BASE_URL}/forecast?city=${encodeURIComponent(city)}`),
    ]);

    weatherData = current;
    forecastData = forecast;
    renderAll(current, forecast);
    showMain(true);
  } catch (err) {
    showError(err.message || 'City not found.');
    showMain(false);
  } finally {
    showLoading(false);  // Always hide loader — success or failure
  }
}
```

**Key points:**
- Uses `async/await` — modern JavaScript async pattern
- `Promise.all()` fires **both API calls in parallel** — roughly 2x faster than sequential
- `try/catch/finally` handles errors gracefully — app never crashes
- `encodeURIComponent(city)` — URL-encodes city name for safe transmission

---

### Q24. What is `Promise.all()` and why is it important?

**Answer:** `Promise.all([p1, p2])` runs multiple async operations **simultaneously** and waits for ALL to complete.

Without `Promise.all`:
- Request 1 takes 300ms → then Request 2 takes 300ms → Total: **600ms**

With `Promise.all`:
- Both requests run at the same time → Total: **~300ms** (limited by the slower one)

For user experience, this means weather data appears nearly **twice as fast**.

---

### Q25. Explain the temperature conversion in your code.

```javascript
function toDisplay(kelvin) {
  return currentUnit === 'C'
    ? Math.round(kelvin - 273.15)           // Kelvin to Celsius
    : Math.round((kelvin - 273.15) * 9/5 + 32);  // Kelvin to Fahrenheit
}
```

**Answer:** OpenWeatherMap returns temperatures in **Kelvin** (SI unit).

Formulas:
- **Kelvin to Celsius**: K - 273.15
- **Kelvin to Fahrenheit**: (K - 273.15) x 9/5 + 32

`currentUnit` (either `'C'` or `'F'`) is toggled by the header buttons. When toggled, we **re-render** using the original Kelvin data stored in `weatherData` — **no re-fetch needed**.

---

### Q26. What is Glassmorphism? How did you implement it?

**Answer:** Glassmorphism is a modern UI design trend mimicking frosted glass. The key CSS property:

```css
.glass-card {
  background: rgba(255,255,255,0.07);        /* Nearly transparent white */
  border: 1px solid rgba(255,255,255,0.15);  /* Semi-transparent border */
  backdrop-filter: blur(18px);               /* THE KEY — blurs content behind */
  -webkit-backdrop-filter: blur(18px);       /* Safari support */
  border-radius: 20px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.35);
}
```

`backdrop-filter: blur(18px)` is what creates the frosted glass look — it blurs everything **behind** the element. Combined with a semi-transparent background, it looks like frosted glass.

---

### Q27. How does the dynamic background colour change work?

In `app.js`:
```javascript
function updateBackground(condition) {
  document.body.className = '';  // Clear all CSS classes
  const map = {
    Clear: 'weather-clear', Clouds: 'weather-clouds',
    Rain: 'weather-rain', Snow: 'weather-snow',
    Thunderstorm: 'weather-thunderstorm', Mist: 'weather-mist',
    // etc.
  };
  document.body.classList.add(map[condition] || 'weather-clear');
}
```

In `style.css`:
```css
body {
  background: var(--bg-clear);
  transition: background 1.2s ease;  /* Smooth 1.2 second transition */
}
body.weather-rain { background: linear-gradient(135deg, #0a0a1a 0%, #1a2744 40%, #0d1b2a 100%); }
```

**The `transition: background 1.2s ease`** on the body element makes the colour change happen smoothly — not an instant jump. The body's CSS class changes, which triggers a new gradient, which transitions over 1.2 seconds.

---

### Q28. How do the progress bars on stat cards animate?

```javascript
// In renderStats() — called after weather data arrives
setTimeout(() => {
  setBarWidth('bar-humidity', main.humidity);       // 0–100 directly
  setBarWidth('bar-wind', Math.min(wind.speed / 20, 1) * 100);  // normalize
  setBarWidth('bar-cloud', clouds.all);             // 0–100 directly
  setBarWidth('bar-pressure', Math.min((main.pressure - 950) / 100, 1) * 100);
}, 300);  // 300ms delay so card entrance animation plays first

function setBarWidth(id, pct) {
  document.getElementById(id).style.width = Math.max(0, Math.min(100, pct)) + '%';
}
```

CSS:
```css
.stat-bar {
  width: 0%;
  transition: width 1.2s cubic-bezier(0.4, 0, 0.2, 1);
}
```

**How it works:**
1. Bar starts at `width: 0%` when the card renders
2. After 300ms, JavaScript sets the width to the data value (e.g., `width: 78%` for 78% humidity)
3. CSS `transition` animates it smoothly from 0% to 78% over 1.2 seconds
4. The `cubic-bezier` easing gives a "ease-out" feel (fast start, slow finish)

---

### Q29. What is `debounceTimer` and why is it used?

```javascript
let debounceTimer = null;
function handleInputChange() {
  clearTimeout(debounceTimer);
  debounceTimer = setTimeout(() => {
    filterAndShowSuggestions();
  }, 220);
}
```

**Answer:** **Debouncing** limits how often a function executes when events fire rapidly.

Without debounce: Typing "Mumbai" fast fires the filter function 6 times in <100ms.
With 220ms debounce: Filter runs only **once** — 220ms after the last keystroke.

This improves performance and prevents the suggestions dropdown from flickering on every keystroke.

---

### Q30. What is the `mode()` function used for?

```javascript
function mode(arr) {
  const freq = {};
  arr.forEach(v => { freq[v] = (freq[v] || 0) + 1; });
  return Object.keys(freq).reduce((a, b) => freq[a] > freq[b] ? a : b);
}
```

**Answer:** `mode()` finds the **most frequently occurring value** in an array.

**Why we need it**: The `/forecast` API gives 8 data points per day (3-hourly). For a day's card we need ONE representative icon. If a day has icons `['03d', '03d', '10d', '03d', '02d', '03d']`, mode returns `'03d'` (the most common). The forecast card shows the dominant weather condition for that day.

---

## SECTION 6 — SECURITY QUESTIONS {#security}

### MOST LIKELY Q31. How did you secure the OpenWeatherMap API key?

**Answer:** The API key is stored as a **Lambda environment variable** — never in any source code file.

**Why this is secure:**
1. `weather_lambda.py` only contains: `API_KEY = os.environ.get("OWM_API_KEY", "")` — no actual key value
2. The real key is stored in **Lambda's encrypted environment variable store** (encrypted at rest with AWS KMS automatically)
3. The browser (JavaScript) **never receives the API key** — it only sees our API Gateway URL
4. Even if someone does "View Source" in the browser, they see `amazonaws.com` URLs — not the OWM key

**What would happen if we put the key in app.js?**
Anyone can open DevTools > Sources > app.js > copy the key → use our API quota → we get blocked.

---

### MOST LIKELY Q32. What is the IAM Role used by your Lambda?

**Answer:** When we created the Lambda, AWS automatically created an **IAM Execution Role**. We kept the default policy `AWSLambdaBasicExecutionRole`, which allows only:
- `logs:CreateLogGroup` — create CloudWatch Log Group
- `logs:CreateLogStream` — create log streams
- `logs:PutLogEvents` — write log entries

Lambda does NOT have permissions to access S3, DynamoDB, or any other service. This is the **Principle of Least Privilege** — give only what is needed.

---

### MOST LIKELY Q33. What is CORS and why did you have to handle it?

**Answer:** CORS = **Cross-Origin Resource Sharing** — a browser security mechanism that blocks JavaScript from calling a different domain than the one that served the page.

**Our situation:**
- Page loads from: `http://skypulse...s3-website.ap-south-1.amazonaws.com`
- API is at: `https://kf7n4k0a4d.execute-api.ap-south-1.amazonaws.com`

These are different origins (domains) → browser blocks the call by default.

**How we solved it:**
Lambda returns CORS headers in every response:
```python
"Access-Control-Allow-Origin": "*"   # Allow any origin
```

Also handled **OPTIONS preflight** — the browser sends OPTIONS before the real GET request to check CORS safety:
```python
if event.get("httpMethod") == "OPTIONS":
    return {"statusCode": 200, "headers": CORS_HEADERS, "body": ""}
```

API Gateway also has CORS enabled at the resource level as a second layer.

---

### Q34. Is your API secure from abuse?

**Answer:** Our API is publicly accessible (no authentication), which means anyone could call our API Gateway URL directly. 

**Current limitation:** No rate limiting, no API key required to call API Gateway.

**How we could improve it:**
1. **API Gateway Usage Plans + API Keys** — only requests with a valid key accepted
2. **AWS WAF rate-limiting rules** — block IPs making too many requests
3. **CloudFront + WAF** in front of everything

For a student project, the risk is minimal — worst case is Free Tier Lambda quota gets used up. Our OWM API key behind Lambda remains safe regardless.

---

## SECTION 7 — CLOUD CONCEPTS DEMONSTRATED {#cloud-concepts}

### MOST LIKELY Q35. How does your project demonstrate PaaS?

**Answer:** PaaS = Provider manages OS, runtime, middleware — you manage only application code.

In our project:
- **Lambda** — We only wrote `weather_lambda.py`. AWS managed the Python 3.12 runtime, OS, compute, scaling, fault tolerance. We never touched a server.
- **API Gateway** — We configured routes. AWS manages HTTP servers, TLS certificates, load balancing.
- **S3 Static Website Hosting** — We uploaded files. AWS manages the web server.

We never installed Apache, Nginx, set up a runtime, or configured an OS.

---

### Q36. How does your project demonstrate Elasticity?

**Answer:** Lambda is **inherently elastic**:
- 1 person searches → 1 Lambda invocation
- 1000 people search simultaneously → 1000 concurrent Lambda invocations spin up automatically
- Traffic drops → Lambda scales to 0 — zero cost

No manual intervention, no pre-provisioning needed. This is **perfect elasticity**.

---

## SECTION 8 — LIMITATIONS & IMPROVEMENTS {#improvements}

### MOST LIKELY Q37. What are the limitations of your project?

| Limitation | Description |
|---|---|
| **No database** | No search history saved; refresh = data gone |
| **No user authentication** | Anyone can use it, no personalisation |
| **Static suggestions** | Autocomplete list is hardcoded, not real geocoding |
| **HTTP, not HTTPS** | S3 static website URL is HTTP only (CloudFront adds HTTPS) |
| **No geolocation** | Cannot auto-detect user's city via GPS |
| **Lambda cold start** | First request after inactivity may be 200ms slower |
| **No caching** | Same city searched 100 times = 100 Lambda invocations |
| **No rate limiting** | API endpoint is publicly accessible |

---

### MOST LIKELY Q38. How would you improve this project?

**Answer:**

1. **Add HTTPS via CloudFront** — CDN in front of S3 — gets free SSL certificate via AWS ACM, faster globally

2. **Add Caching** — Enable API Gateway caching — same city response cached for 60 seconds, reduces Lambda calls

3. **Add DynamoDB for search history** — Store recent searches, trending cities globally

4. **Add user authentication via Cognito** — Login to save favourite cities

5. **Add Geolocation** — Auto-detect city via `navigator.geolocation.getCurrentPosition()`

6. **Add Air Quality Index (AQI)** — OWM has a free AQI API

7. **Make it a PWA** — Add `manifest.json` + service worker for offline support and phone install

8. **API Gateway Rate Limiting** — Usage Plans to prevent abuse

---

### Q39. What is a Lambda "cold start"? Does it affect your project?

**Answer:** A cold start happens when Lambda receives a request but no warm environment exists — it needs to provision a container, load the Python runtime, then run your code. This adds ~200–500ms on the **first request** after a period of inactivity.

Subsequent requests reuse the warm environment and have no cold start overhead.

**For our project:** If nobody searches for 15 minutes, the next search is slightly slower. Users typically don't notice 200ms. It is a known Lambda trade-off — the cost of being truly serverless.

---

## SECTION 9 — TOUGH / TRICKY QUESTIONS {#tough}

### MOST LIKELY Q40. Why didn't you use EC2 for the backend?

| Aspect | EC2 | Lambda |
|---|---|---|
| Running when idle | Yes — costs money 24/7 | No — free when unused |
| Server management | Full OS, updates, security | None — AWS manages everything |
| Scaling | Need to configure Auto Scaling | Instant, automatic |
| Best for | Long-running servers | Short, event-driven functions |

Lambda is perfect for our use case — each request runs for ~300ms. Paying for an EC2 instance running 24/7 for a function that runs 300ms on demand is wasteful.

---

### MOST LIKELY Q41. Why didn't you use Elastic Beanstalk?

**Answer:** Elastic Beanstalk runs **EC2 instances** (always on). Even on the Free Tier, you use EC2 hours from the 750 hours/month limit.

Lambda is better for this project because:
- **cost:zero when idle** (no EC2 running)
- **simpler** — just upload one Python file, no env config, no app server setup
- **automatically elastic** — scales instantly without Beanstalk's auto-scaling configuration

Elastic Beanstalk is better when you have a long-running web server, complex middleware, or persistent background jobs.

---

### Q42. What happens step by step when a user types "Mumbai" and presses Enter?

**Full flow:**
1. User types `Mumbai`, presses Enter
2. `fetchWeather()` is called in `app.js`
3. `showLoading(true)` — spinning loader appears
4. `Promise.all()` fires two parallel requests:
   - `GET /weather?city=Mumbai` → API Gateway → Lambda → OWM
   - `GET /forecast?city=Mumbai` → API Gateway → Lambda → OWM
5. Lambda reads `city = "Mumbai"` from query params
6. Lambda constructs: `https://api.openweathermap.org/data/2.5/weather?q=Mumbai&appid=[KEY]`
7. OWM responds with JSON weather data
8. Lambda adds CORS headers and returns JSON to API Gateway
9. API Gateway returns response to browser
10. JavaScript calls `renderAll(current, forecast)`:
    - `renderCurrentWeather()` — city name, temperature, description
    - `renderStats()` — 6 stat cards with animated bars
    - `renderForecast()` — 5 forecast day cards
    - `renderHourly()` — 12-hour horizontal scroll
    - `updateBackground('Clear')` — background transitions to clear sky colours
11. `showMain(true)` — main content visible, empty state hidden
12. `showLoading(false)` — loader hidden

---

### Q43. What data does the `/weather` endpoint return?

OWM `/weather` response (key fields we use):
```json
{
  "name": "Mumbai",
  "sys": {
    "country": "IN",
    "sunrise": 1712550000,   // Unix timestamp
    "sunset":  1712595000    // Unix timestamp
  },
  "main": {
    "temp":       303.15,   // Kelvin
    "feels_like": 306.2,    // Kelvin
    "humidity":   78,        // %
    "pressure":   1008       // hPa
  },
  "weather": [{"main": "Clear", "description": "clear sky", "icon": "01d"}],
  "wind":    {"speed": 4.5},   // m/s
  "clouds":  {"all": 5},       // % cloud cover
  "visibility": 10000          // metres
}
```

---

### Q44. What is a Unix timestamp? How do you convert it?

**Answer:** A Unix timestamp = number of **seconds since January 1, 1970 00:00:00 UTC** (the "epoch").

OWM sends `sunrise` and `sunset` as Unix timestamps. To display in JavaScript:
```javascript
const sunrise = new Date(sys.sunrise * 1000);  // Multiply by 1000 (JS uses milliseconds)
sunrise.toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit', hour12: true });
// Output: "06:12 AM"
```

---

### Q45. What is `pop` in the forecast data?

**Answer:** `pop` = **Probability of Precipitation**. A number from 0.0 to 1.0 indicating the chance of rain/snow.

In the hourly cards, we display it as a percentage:
```javascript
const rain = item.pop ? `${Math.round(item.pop * 100)}%` : '';
// pop = 0.45 → "45%"
```

We only show the rain indicator if `item.pop` is non-zero — clean display.

---

### Q46. Why does the stat bar for pressure use a formula?

```javascript
setBarWidth('bar-pressure', Math.min((main.pressure - 950) / 100, 1) * 100);
```

**Answer:** Pressure in hPa typically ranges from **950 to 1050 hPa** for normal weather. Simply using the raw value (e.g., 1008) on a 0–100% bar makes no sense (it would always be >100%).

So we **normalise** it:
- Subtract 950 (the lower bound) → range becomes 0–100
- Divide by 100 (the range) → normalises to 0.0–1.0
- `Math.min(..., 1)` clamps at 1.0 max (for extreme pressure values)
- Multiply by 100 → gets percentage for CSS width

This maps 950 hPa to 0% and 1050 hPa to 100% on the progress bar.

---

### Q47. How did you test locally before deploying to AWS?

**Answer:** We used the dual-mode CONFIG:

```javascript
// Local testing:
USE_LAMBDA: false,
OWM_API_KEY: 'real_key_here',
```

Open `index.html` directly in browser or VS Code Live Server. All API calls go directly to OpenWeatherMap — no AWS needed.

**Demo mode** (no real key needed): Set `OWM_API_KEY: 'YOUR_KEY'` — app detects the placeholder and uses `getMockCurrent()` and `getMockForecast()` — fake data so the entire UI can be tested and demonstrated without any live API.

Before AWS deployment: flip the switch back to `USE_LAMBDA: true, LAMBDA_BASE_URL: 'https://...'`

---

## SECTION 10 — YOUR 60-SECOND PITCH {#pitch}

### MOST LIKELY Q48. How do you introduce your project? (Memorise this)

> **"Sir/Ma'am, I built SkyPulse — a real-time weather dashboard deployed entirely on the AWS Free Tier. The frontend is HTML, CSS, and JavaScript hosted on Amazon S3 as a static website. When a user searches for a city, JavaScript makes an API call to Amazon API Gateway, which triggers an AWS Lambda function written in Python. Lambda securely calls the OpenWeatherMap API using a key stored as an environment variable — the key is never exposed to the browser. Lambda returns weather data with CORS headers back to the browser, which renders current weather, a 5-day forecast, a 12-hour hourly outlook, with a glassmorphism dark UI that dynamically changes its background to match the weather condition. This project demonstrates IaaS, PaaS, Storage as a Service, Serverless computing, IAM roles, CORS security — all on AWS at zero cost."**

---

### Q49. If the examiner asks to show the project running:

**Be ready to:**
1. Open the S3 website URL in browser
2. Search for **Mumbai** (safe bet — large, always works)
3. Show: temperature, forecast cards, stat bars animating, sunrise/sunset
4. Toggle **degrees C / degrees F** — show temperature changing instantly (no re-fetch)
5. Click **London** or **Tokyo** chip — show background colour changing with weather
6. Click the **SkyPulse logo** — show home reset, empty state with city chips
7. (*Optional, impressive*) Open DevTools > Network tab — show the two parallel API Gateway calls

---

## SECTION 11 — QUICK FACTS REVISION TABLE {#facts}

| Question | Answer |
|---|---|
| Backend language | Python 3.12 |
| HTTP library in Lambda | `urllib` (Python standard library) |
| Why not `requests`? | Needs a Lambda Layer; `urllib` is built-in, zero dependency |
| Temperature unit from OWM | Kelvin |
| Kelvin to Celsius | K minus 273.15 |
| Kelvin to Fahrenheit | (K minus 273.15) x 9/5 + 32 |
| How many forecast data points | 40 (`cnt=40`) |
| Frequency of forecast data | Every 3 hours |
| Total forecast coverage | 5 days (40 x 3hrs = 120 hours) |
| Hourly cards shown | First 12 data points |
| What is `pop`? | Probability of precipitation (0.0 to 1.0) |
| What is `dt`? | Unix timestamp in seconds |
| Why multiply dt x 1000 in JS? | JavaScript Date uses milliseconds not seconds |
| CSS design style | Glassmorphism |
| Font used | Outfit (Google Fonts) |
| Key CSS for glass effect | `backdrop-filter: blur(18px)` |
| Background changes smoothly via | `transition: background 1.2s ease` on body |
| Stat bars animate via | CSS `transition: width 1.2s cubic-bezier(...)` |
| What is debouncing? | Delay function execution until user stops typing |
| Debounce delay in project | 220ms |
| Why `Promise.all()`? | Runs two API calls in parallel — 2x faster |
| CORS header for all origins | `Access-Control-Allow-Origin: *` |
| Preflight request method | OPTIONS (handled by Lambda: returns 200 + CORS headers) |
| S3 bucket region | ap-south-1 (Mumbai) |
| Lambda function name | `skypulse-weather` |
| API Gateway name | `skypulse-api` |
| API endpoints | `/weather?city=` and `/forecast?city=` |
| API Gateway stage | `prod` |
| urlopen timeout in Lambda | 8 seconds |
| IAM policy on Lambda role | AWSLambdaBasicExecutionRole |
| CloudWatch log group | `/aws/lambda/skypulse-weather` |
| Monthly cost | Rs. 0 (Free Tier) |
| S3 Free Tier | 5 GB storage, 20,000 GET requests/month |
| Lambda Free Tier | 1 million requests + 400,000 GB-seconds/month |
| API Gateway Free Tier | 1 million calls/month for 12 months |

---

*Mini Project Viva Guide | SkyPulse Weather Dashboard*
*CSL605 Cloud Computing | Mumbai University | Semester VI | AWS Platform*
