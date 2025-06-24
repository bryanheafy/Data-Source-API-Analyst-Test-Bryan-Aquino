# Data-Source-API-Analyst-Test-Bryan-Aquino
Homework assignment for Data Source API Analyst role.

# Data Source API Analyst Test

This repository contains my solution for the API Analyst test assignment.

## Purpose

The goal was to work with the GitHub public API to:
- Search for public repositories using a keyword
- Get a list of commits from a specific repository
- Access files inside a repository

## Folder Structure

/Content  
  - API_Documentation.md  
  - Troubleshooting_Guide.md  
  - Reflections.md  

/Postman_Collection  
  - github_api_collection.json  

README.md

## Tools Used

- Postman for sending and testing API requests
- GitHub REST API
- Environment variables for easier token and version handling

## What I Did

1. `GET /search/repositories`  
   I used this to search public repos by keyword, like "python".

2. `GET /repos/{owner}/{repo}/commits`  
   This helped me get the commit history of a repo (I used pallets/flask).

3. `GET /repos/{owner}/{repo}/contents/{path}`  
   I used this to view files inside a repo, like the README file.

## Testing Process

All the tests were done in Postman.  
I organized the requests in folders:
- Repositories
- Commits
- Contents

I also used environment variables so I didn’t have to rewrite the token or API version for every request.

## Output

The full Postman collection is included here:  
`/Postman_Collection/github_api_collection.json`

## Authentication

To avoid request limits, I used a personal GitHub token.  
It was included in the request headers like this:

Authorization: Bearer {{token}}

## Final Thoughts

This exercise helped me get more comfortable working with APIs.  
I learned how to set up authenticated requests, handle common errors like 401 or 404, and keep things organized using folders and variables in Postman.
