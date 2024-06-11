This guide provides instructions on how to use the GitHub CLI https://cli.github.com

# Useful Commands
---
## View Status 
```sh
gh status
```
## Viewing PR's
```sh
gh search prs --state=open --review-requested=@me
gh pr view <pr-number>
gh pr list
```
## Reviewing PR's
```sh
gh pr checkout <pr-number>
gh pr view <pr-number>
gh pr diff 

gh pr review --request-changes <pr-number> -b "please adddress issues"
gh pr review --comment <pr-number> -b "Looks good, but I have some questions."

gh pr review -a (approve)
gh pr review -F (view body)
```