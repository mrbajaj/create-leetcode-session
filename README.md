# Guide to Using the cURL Command for LeetCode Creating Leetcode Session

## Overview

This guide explains how to use the following cURL command to create a new LeetCode session programmatically:

```sh
curl -X PUT "https://leetcode.com/session/" \
     -H "Content-Type: application/json" \
     -H "x-csrftoken: {CSRF_TOKEN}" \
     -H "User-Agent: Mozilla/5.0" \
     -H "x-requested-with: XMLHttpRequest" \
     -H "Cookie: LEETCODE_SESSION={LEETCODE_SESSION}" \
     -d '{"func":"create","name":"{NEW_SESSION_NAME}"}'
```

## Prerequisites

To successfully execute this command, you need two key authentication tokens from LeetCode:

1. **LEETCODE_SESSION**
2. **CSRF_TOKEN**

## How to Obtain LEETCODE_SESSION and CSRF_TOKEN

### Step 1: Open LeetCode in Your Browser

- Visit [LeetCode](https://leetcode.com/) and log into your account.

### Step 2: Open Browser's Developer Tools

- Press `F12` or `Ctrl + Shift + I` (`Cmd + Option + I` on macOS) to open Developer Tools.

### Step 3: Navigate to the Application Tab

- In the Developer Tools panel, go to the **Application** tab.
- Under **Storage**, find and expand the **Cookies** section.
- Select `https://leetcode.com` from the list.

### Step 4: Find and Copy Required Tokens

- Look for a cookie named **LEETCODE_SESSION** and copy its value.
- Look for another cookie named **csrftoken** and copy its value (this is your **CSRF_TOKEN**).

## Using the cURL Command

Replace the placeholders in the command with the actual values:

- `{CSRF_TOKEN}` → Replace with the copied **csrftoken** value.
- `{LEETCODE_SESSION}` → Replace with the copied **LEETCODE_SESSION** value.
- `{NEW_SESSION_NAME}` → Replace with your desired session name.

Example:

```sh
curl -X PUT "https://leetcode.com/session/" \
     -H "Content-Type: application/json" \
     -H "x-csrftoken: abc123xyz" \
     -H "User-Agent: Mozilla/5.0" \
     -H "x-requested-with: XMLHttpRequest" \
     -H "Cookie: LEETCODE_SESSION=def456uvw" \
     -d '{"func":"create","name":"MyNewSession"}'
```


## Verifying the Response

After running the command, you should receive a JSON response. If successful, it will confirm the creation of the new session.
```
{"sessions": [{"id": 9815627, "is_active": true, "total_acs": 304, "name": "Apr2023", "ac_questions": 199, "submitted_questions": 215, "total_submitted": 424}, {"id": 17740681, "is_active": false, "total_acs": 0, "name": "Mar2025", "ac_questions": 0, "submitted_questions": 0, "total_submitted": 0}], "is_full": false}
```

## Troubleshooting

- If you receive a `403 Forbidden` error, check that:
  - The **CSRF token** and **LEETCODE_SESSION** are correct and not expired.
  - You are logged into LeetCode in your browser.
- If the session is not created, ensure the `{NEW_SESSION_NAME}` does not contain invalid characters.

## Conclusion

This guide helps you authenticate and create a new session on LeetCode using `cURL`. Follow the steps carefully to extract the necessary tokens and execute the command correctly.



Credits: https://github.com/kkuchar2/leetcode_session_creator
