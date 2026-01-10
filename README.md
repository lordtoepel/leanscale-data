# LeanScale Data Store

This repository serves as the database for the LeanScale Platform.
All data is stored as JSON files and managed via git.

## Structure

```
├── organizations/          # Organization/tenant data
│   └── {org-id}.json
├── users/                  # User profiles
│   └── {user-id}.json
├── members/                # Organization memberships
│   └── {org-id}/
│       └── {user-id}.json
├── clients/                # Client companies
│   └── {org-id}/
│       └── {client-id}.json
├── projects/               # Projects
│   └── {org-id}/
│       └── {project-id}.json
├── tasks/                  # Tasks within projects
│   └── {org-id}/
│       └── {task-id}.json
├── timelogs/               # Time entries
│   └── {org-id}/
│       └── {year-month}/
│           └── {entry-id}.json
├── tags/                   # Tags for categorization
│   └── {org-id}/
│       └── {tag-id}.json
└── schemas/                # JSON Schema definitions
```

## How It Works

1. **Create/Update**: Edit JSON files directly or via API
2. **Commit**: Changes are committed to git
3. **Sync**: Application reads from this repo
4. **Audit**: Full git history = complete audit trail

## Benefits

- Edit data with any text editor
- Full version history
- Branch for bulk changes
- PR review for data changes
- No database hosting costs
- Claude can directly edit files

## Editing Data

### Via GitHub UI
1. Navigate to the file you want to edit
2. Click the pencil icon
3. Make changes
4. Commit with a descriptive message

### Via CLI
```bash
# Clone the repo
git clone https://github.com/lordtoepel/leanscale-data.git

# Edit files
vim projects/org-123/project-456.json

# Commit and push
git add . && git commit -m "Update project deadline" && git push
```

### Via API
The LeanScale Platform provides an API that commits changes automatically.

## Schemas

See `/schemas` directory for JSON Schema definitions that validate all data.
