# API Documentation

This file includes notes on the GitHub API endpoints used in this test, how they work, and what kind of data they return.

## 1. Search Public Repositories

Endpoint:  
GET /search/repositories

Example URL:  
https://api.github.com/search/repositories?q=python&sort=stars&order=desc

What it does:  
Searches public repos that match a keyword. In this case, I searched for "python" and sorted the results by star count.

Parameters:  
- q: the keyword (like "python", "data", etc.)
- sort: how to sort the results (like stars)
- order: asc or desc

## 2. Get Repository Commits

Endpoint:  
GET /repos/{owner}/{repo}/commits

Example URL:  
https://api.github.com/repos/pallets/flask/commits

What it does:  
Gives you the commit history of a specific repo. Each commit includes details like author, date, and message.

Things to know:  
- If the repo doesn’t exist, you’ll get a 404 error.
- Pagination might apply if there are lots of commits.

## 3. Get Repository Contents

Endpoint:  
GET /repos/{owner}/{repo}/contents/{path}

Example URL:  
https://api.github.com/repos/pallets/flask/contents/README.md

What it does:  
Lets you read files from a repo. You need to provide the exact file name (and folder path if it’s not in the root).

Notes:  
- If the file doesn’t exist or the path is wrong, you’ll get a 404.
- The content comes base64-encoded.

## Authentication

All requests used a personal GitHub token for authentication. This helps avoid rate limits and lets you access more data.

Header used:  
Authorization: Bearer {{token}}

Also included the required API version:  
X-GitHub-Api-Version: 2022-11-28

## Rate Limits

Without a token, GitHub limits you to 60 requests per hour. With a token, you can do up to 5000 requests per hour.

To check how many requests you have left, you can look at the headers in the response:
- X-RateLimit-Remaining
- X-RateLimit-Reset

## Common Errors

- 401 Unauthorized: Usually means the token is missing, expired, or copied wrong.
- 404 Not Found: The repo or file path doesn’t exist, or has a typo.
