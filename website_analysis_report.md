# Website Analysis Report: SimpleClaw.com

## Summary
As requested, an analysis of `https://www.simpleclaw.com/` (specifically the JavaScript assets) was performed to locate a plan ID and a coupon code.

**Findings:**
-   **Plan ID:** `2gb_50gb`
-   **Coupon Code:** `RETRY100OFF`

## Detailed Analysis

### Plan ID
The plan ID was found in the main application logic file (`/_next/static/chunks/b8d2b95ae9b16d3a.js`). It is hardcoded in the checkout payload sent to the API.

**Code Snippet:**
```javascript
body: JSON.stringify({
    name: m?.displayName || "User",
    email: m.email,
    cloud_plan: "2gb_50gb",
    credits_per_month: "15",
    default_model: v,
    telegram_bot_token: _,
    profile_picture: m?.photoURL ?? null
})
```

### Coupon Code
A coupon code was also found in the same JavaScript file (`/_next/static/chunks/b8d2b95ae9b16d3a.js`). It appears in an error/help message suggesting users can use it if they encounter issues.

**Code Snippet:**
```javascript
(0,d.jsx)("code",{className:"rounded bg-white/10 px-1.5 py-0.5 text-white/90 font-mono text-xs",children:"RETRY100OFF"})
```
**Context:** "...please create a new account and use code RETRY100OFF during checkout on the site again to connect to a different bot for free..."

## Conclusion
The website uses a hardcoded plan ID `2gb_50gb` for its checkout process. A fallback coupon code `RETRY100OFF` is exposed in the frontend code to assist users who experience deployment issues, likely offering a 100% discount ("OFF" and "free" context).
