# Jira TODO

Create issue for TODO comments

> ##### Only supports Jira Cloud. Does not support Jira Server (hosted)

## Usage

> ##### Note: this action requires [Jira Login Action](https://github.com/marketplace/actions/jira-login)

Create Jira issue from TODO comments in pushed code.
Example workflow:

```yaml
- name: Create TODO
  uses: MickCoelho/jira-todo-action@main
  with:
    project: MC
    issuetype: Task
    description: Created automatically via GitHub Actions
    labels: from-todo,needs-triage
    customfield_10184: "Brand Studio"
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} # https://help.github.com/en/articles/virtual-environments-for-github-actions#github_token-secret
```

---

## Action Spec:

### Environment variables

- `GITHUB_TOKEN` - GitHub secret [token](https://developer.github.com/actions/creating-workflows/storing-secrets/#github-token-secret) is used to retrieve diffs

### Inputs

- `project` - Key of the project
- `issuetype` - Type of the issue to be created. Example: 'Task'
- `description` - Issue description
- `customfield_10184` - Fio squad
- `labels` - Comma separated array

### Outputs

- `issues`: Well-formed JSON array containing keys of all newly created issues
