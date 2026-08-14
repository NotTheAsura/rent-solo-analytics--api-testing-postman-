# RentSolo Agent Analytics - API Test Automation

## Overview
This repository contains an automated API testing suite built with Postman and Newman. It validates the backend REST APIs that power the Agent Analytics Dashboard for the RentSolo platform.

## Technical Scope
The test suite validates 9 `POST` endpoints, covering:
- Data aggregation (overview, widget clicks, booked tours, completion rate)
- Search & pagination (renters list with page/limit/sort/search)
- File exports (Excel reports, weekly exports)
- Event tracking (public endpoint for widget event action codes)

## Tools Used
- Postman — build requests and maintain environments
- Newman — CLI execution for local and CI runs
- Git/GitHub — repository and CI integration

## How to Run Locally
1. Clone this repository.
2. Install Newman:
   npm install -g newman
3. Run the collection (file is at the repo root):
   newman run RentSolo_Analytics_Postman_Collection.json \
     --env-var "baseUrl=http://localhost:9090" \
     --env-var "token={{your_token_here}}"

Notes:
- The collection in this repo contains a placeholder token value: `{{your_token_here}}` in the Postman `auth` section. Do NOT commit real tokens.
- Prefer using a Postman environment file or runtime env-vars to inject secrets instead of editing the collection.

## Example GitHub Actions CI step
Store your token in GitHub Actions secrets (Repository -> Settings -> Secrets) as `RENTSOLO_API_TOKEN` and the base URL as `BASE_URL`. Add a workflow step like:

```yaml
- name: Run RentSolo API tests with Newman
  run: |
    npm install -g newman
    newman run RentSolo_Analytics_Postman_Collection.json \
      --env-var "baseUrl=${{ secrets.BASE_URL }}" \
      --env-var "token=${{ secrets.RENTSOLO_API_TOKEN }}" \
      --reporters cli,junit \
      --reporter-junit-export reports/junit.xml
```

## Security & Cleanup (Important)
If a real token was previously committed and exposed in this repository:
1. Revoke or rotate the token immediately — assume it is compromised.
2. Remove the secret from the repository history (history rewrite required):
   - Recommended: use git filter-repo (https://github.com/newren/git-filter-repo) or BFG Repo-Cleaner to remove the token from all commits, then force-push.
   - After history rewrite, tell all collaborators to reclone the repository — old clones will contain the secret.
3. Search the repo and branches for other potential secrets (`Bearer`, `token`, long base64 strings) and remove as needed.
4. Add prevention: enable GitHub secret scanning, add a pre-commit secret checker (e.g., detect-secrets or pre-commit hooks), and avoid committing credentials in any files.

If you want, I can prepare the exact git filter-repo or BFG commands (you will paste the actual secret when running them) and/or scan the repository for other potential exposures.

## Author
QA / Software Testing Portfolio Project
