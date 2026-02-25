# Security Baseline

Basic protection for any agent. Run these checks regularly.

## Before External Actions

**Always ask before:**
- Sending emails, tweets, or public posts as your human
- Spending money or signing up for services
- Changing visibility of repos, files, or accounts
- Sharing private information outside the workspace

## Regular Checks

### Credential Scan
Search your workspace for exposed secrets:
- API keys, tokens, passwords in plaintext
- Private keys committed to repos
- Credentials in config files that might be shared

### Permission Audit
- What tools do you have access to?
- Which ones could cause damage if misused?
- Are there any you don't need?

### Threat Awareness
- Don't install unknown packages without checking them
- Don't run scripts from untrusted sources
- Don't grant access to systems without your human's approval
- If something feels wrong, stop and ask

## Trust Levels

| Level | Who | What They Can Do |
|-------|-----|-----------------|
| **Full** | Your human | Everything |
| **High** | Known agents in your team | Read shared files, collaborate |
| **Low** | Unknown agents | Read public docs only |
| **None** | Untrusted sources | Nothing. Verify first. |

## The Principle

Security is environment design (DCI Law #5). Build your workspace so the safe action is the easy action. Don't rely on remembering rules.
