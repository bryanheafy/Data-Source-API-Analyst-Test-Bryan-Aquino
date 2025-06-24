# Troubleshooting Guide

This guide lists the most common problems I ran into while using the GitHub API, and how I solved them. It’s meant to help if something breaks or doesn’t return the expected result.

## 1. Error 401 - Unauthorized

What it means:  
The request isn’t properly authenticated.

Things to check:
- Make sure you're using a personal access token.
- Check that the token hasn’t expired or been deleted.
- In Postman, make sure the Authorization header looks like this:  
  Authorization: Bearer {{token}}
- If you're using environment variables, confirm both Initial Value and Current Value are set.
- Make sure your environment is selected in the top-right dropdown in Postman.

## 2. Error 404 - Not Found

What it means:  
The endpoint is valid, but the resource you're trying to get doesn’t exist.

Possible causes:
- A typo in the repo name or file path.
- Trying to access a file that doesn’t exist or has a different extension (like `README.md` vs `README.rst`).
- Using an extra space in the URL (Postman sometimes shows a space at the end and it breaks the request).

How I fixed it:
- Double-checked the actual file name in the GitHub repo.
- Removed any accidental spaces from the URL bar in Postman.
- If in doubt, I used the `/contents/` endpoint without a file to list everything in the repo root.

## 3. Rate Limit Reached

What it means:  
You’ve sent too many requests in a short amount of time.

How to know:
- The response will have a 403 status and mention "rate limit" in the message.
- The headers will include:  
  - X-RateLimit-Remaining: number of requests you have left  
  - X-RateLimit-Reset: timestamp of when the limit resets

How I handled it:
- Waited a few minutes and tried again.
- Used a personal access token to unlock the higher limit (5000 requests/hour instead of 60/hour).
- Spread out the requests instead of spamming them.

## 4. No Response or Timeout

What it means:  
Sometimes the server takes too long to reply or you lose connection.

What to do:
- Retry the request later.
- Check your internet connection.
- Restart Postman.

## Other Tips

- Use Postman’s Console (View > Show Postman Console) to debug when things go wrong.
- Always check if the environment is selected. If it’s not, variables like `{{token}}` won’t work.
- If something doesn’t return what you expect, test it directly in the browser to confirm it’s a real issue and not a setup problem.

