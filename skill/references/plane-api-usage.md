# Plane API usage for DERRR Plane Full

Use this reference when the control surface is Plane Full and you need the exact API surface instead of guessing.

## Official docs

Start from Plane's official developer docs:
- Introduction / auth / pagination: `https://developers.plane.so/api-reference/introduction`
- Work item overview: `https://developers.plane.so/api-reference/issue/overview`
- Create a work item: `https://developers.plane.so/api-reference/issue/add-issue`
- Add an issue comment: `https://developers.plane.so/api-reference/issue-comment/add-issue-comment`
- List module work items: `https://developers.plane.so/api-reference/module-issue/list-module-issues`

## Base URL

Official cloud base URL:
- `https://api.plane.so/`

For self-hosted Plane, replace that with the deployment base URL, for example:
- `https://plane.example.com/api/v1/...`

## Authentication

Plane's official docs use the header:
- `X-API-Key: <token>`

For DERRR work, prefer `X-Api-Key` / `X-API-Key` consistently on every request and verify with a cheap probe first:
- `GET /api/v1/users/me/`

## Core DERRR endpoints

### Create a slice / issue

Official family:
- `POST /api/v1/workspaces/{workspace_slug}/projects/{project_id}/issues/`

Typical payload keys used by DERRR:
- `name`
- `description_html`
- `state`
- `priority`
- `parent`

Important:
- do not assume module assignment in the create payload is authoritative
- after creation, verify module membership separately

### Update state / priority / parent

Official family:
- `PATCH /api/v1/workspaces/{workspace_slug}/projects/{project_id}/issues/{issue_id}/`

Use this for:
- moving to In Progress / Done / Backlog
- setting priority
- changing `parent`

### Add proof comments

Official endpoint:
- `POST /api/v1/workspaces/{workspace_slug}/projects/{project_id}/issues/{issue_id}/comments/`

Minimal body:
```json
{"comment_html": "<p>proof</p>"}
```

Use comments for:
- review proof
- deploy proof
- closure proof
- restart notes

### Verify module membership

Official endpoint family:
- `GET /api/v1/workspaces/{workspace_slug}/projects/{project_id}/modules/{module_id}/module-issues/`

Deployment-proven write path:
- `POST /api/v1/workspaces/{workspace_slug}/projects/{project_id}/modules/{module_id}/module-issues/`

Working body shape:
```json
{"issues": ["<issue-id>"]}
```

Treat this as the authoritative membership surface for Plane Full.
If ordinary issue reads do not echo module linkage, trust `module-issues/`, not hopeful PATCH responses.

## Relations and links

Plane has two different concepts here. Do not confuse them.

### URL links

Deployment-proven and doc-shaped endpoint:
- `GET/POST /api/v1/workspaces/{workspace_slug}/projects/{project_id}/issues/{issue_id}/links/`

This endpoint is for external URL links and expects link fields such as `url`.
It is **not** the issue-to-issue relation endpoint.

### Issue relations

Deployment-proven endpoint:
- `GET/POST /api/v1/workspaces/{workspace_slug}/projects/{project_id}/issues/{issue_id}/relations/`

Working create body:
```json
{
  "relation_type": "relates_to",
  "issues": ["<other-issue-id>"]
}
```

Use this for DERRR lineage such as:
- `relates_to`
- other true sequencing or dependency relations when the deployment supports them

Important local lesson:
- `/issues/{issue_id}/links/` returning `400 {"url": ["This field is required."]}` means you hit the URL-link endpoint by mistake
- for ticket-to-ticket relations, use `/relations/`

## Cheap verification checklist

Before assuming a Plane write worked:
1. auth probe succeeds
2. issue create/update returns 200/201
3. module membership is visible through `module-issues/`
4. relation appears through `relations/`
5. proof comment exists on the ticket

## DERRR-specific rule of thumb

For Plane Full, prefer this sequence:
1. create slice issue
2. set/verify parent if needed
3. bind module via `module-issues/`
4. do the work
5. add proof comment
6. update state
7. add successor relation only if it improves audit clarity

That order avoids most of the easy Plane API footguns.
