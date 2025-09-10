# Branch Protection Setup Guide

## Overview
This comprehensive guide explains how to set up branch protection rules for your GitHub repository, ensuring secure team collaboration while maintaining code quality and review processes.

## Table of Contents
1. [Understanding Branch Protection](#understanding-branch-protection)
2. [Step-by-Step Setup](#step-by-step-setup)
3. [Configuration Options Explained](#configuration-options-explained)
4. [Team Workflow Implementation](#team-workflow-implementation)
5. [Troubleshooting Common Issues](#troubleshooting-common-issues)
6. [Best Practices](#best-practices)
7. [Advanced Configuration](#advanced-configuration)

## Understanding Branch Protection

### What is Branch Protection?
Branch protection rules are GitHub features that prevent direct pushes to important branches (like `main` or `master`) and enforce specific workflows for code changes.

### Why Use Branch Protection?
- **Prevents Accidental Changes**: No direct pushes to main branch
- **Enforces Code Review**: All changes must go through pull requests
- **Maintains Code Quality**: Required approvals and status checks
- **Audit Trail**: Complete history of all changes
- **Team Collaboration**: Structured workflow for multiple developers

## Step-by-Step Setup

### Step 1: Access Repository Settings

1. Navigate to your GitHub repository
2. Click on the **"Settings"** tab in the repository navigation
3. In the left sidebar, click on **"Branches"**

### Step 2: Create Branch Protection Rule

1. Click **"Add rule"** or **"Add branch protection rule"**
2. In the **"Branch name pattern"** field, enter: `main`
3. Verify it shows "Applies to 1 branch" and displays "main"

### Step 3: Configure Core Protection Rules

#### ✅ Required Settings (Enable These):

**Require a pull request before merging**
- ✅ **Require approvals**: Set to 1 or more
- ✅ **Dismiss stale PR approvals when new commits are pushed**
- ✅ **Require review from code owners** (if you have a CODEOWNERS file)
- ✅ **Require approval of the most recent reviewable push**

**Require status checks to pass before merging**
- ✅ **Require branches to be up to date before merging**

**Require conversation resolution before merging**
- ✅ **Require conversation resolution before merging**

### Step 4: Configure Security Settings

#### ✅ Security Options (Enable These):

**Require signed commits**
- ✅ **Require signed commits**: Commits must have verified signatures

**Require linear history**
- ✅ **Require linear history**: Prevents merge commits

**Restrict pushes that create files larger than 100 MB**
- ✅ **Restrict pushes that create files larger than 100 MB**

### Step 5: Configure Administrative Settings

#### ⚠️ Important Decisions:

**Do not allow bypassing the above settings**
- ✅ **Recommended**: Check this to ensure even admins follow the rules
- ❌ **Alternative**: Leave unchecked if you want admin override capability

**Allow force pushes**
- ❌ **Recommended**: Leave unchecked for security

**Allow deletions**
- ❌ **Recommended**: Leave unchecked for safety

### Step 6: Save the Rule

1. Click **"Create"** or **"Save changes"**
2. The protection rule will be applied immediately

## Configuration Options Explained

### Pull Request Requirements

| Setting | Purpose | Recommendation |
|---------|---------|----------------|
| Require approvals | Forces code review | 1-2 approvals minimum |
| Dismiss stale approvals | Ensures fresh reviews | Always enable |
| Require code owner review | Expert review for specific files | Enable if using CODEOWNERS |
| Require latest push approval | Prevents self-approval | Always enable |

### Status Checks

| Setting | Purpose | When to Use |
|---------|---------|-------------|
| Require status checks | Enforces CI/CD pipeline | When you have automated tests |
| Require up-to-date branches | Ensures latest code | Always recommended |

### Security Settings

| Setting | Purpose | Security Level |
|---------|---------|----------------|
| Require signed commits | Verifies commit authenticity | High |
| Require linear history | Prevents complex merge history | Medium |
| Restrict large files | Prevents repository bloat | Medium |

## Team Workflow Implementation

### For Repository Owners/Admins

#### Initial Setup Workflow:
1. **Create the repository** with initial files
2. **Set up branch protection** (following this guide)
3. **Temporarily disable protection** for initial setup:
   - Uncheck "Require signed commits"
   - Uncheck "Do not allow bypassing the above settings"
4. **Push initial files** (documentation, templates, etc.)
5. **Re-enable full protection** for ongoing development

#### Ongoing Workflow:
- All changes go through pull requests
- Review and approve team contributions
- Merge approved pull requests
- Monitor repository activity

### For Team Members

#### Getting Started:
1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/repository-name.git
   cd repository-name
   ```
3. **Add upstream remote**:
   ```bash
   git remote add upstream https://github.com/ORIGINAL-OWNER/repository-name.git
   ```

#### Development Workflow:
1. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```
2. **Make your changes** and commit:
   ```bash
   git add .
   git commit -m "Add: Description of changes"
   ```
3. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```
4. **Create a pull request** on GitHub
5. **Address review feedback** if needed
6. **Wait for approval and merge**

## Troubleshooting Common Issues

### Issue: Push Rejected - "Protected branch update failed"

**Error Message:**
```
remote: error: GH006: Protected branch update failed for refs/heads/main.
remote: - Changes must be made through a pull request.
```

**Solution:**
- You cannot push directly to the protected branch
- Create a feature branch and use pull requests instead

### Issue: "Commits must have verified signatures"

**Error Message:**
```
remote: - Commits must have verified signatures.
```

**Solutions:**
1. **Set up GPG signing** (recommended):
   ```bash
   # Generate GPG key
   gpg --full-generate-key
   
   # Configure git to use GPG
   git config --global user.signingkey YOUR_GPG_KEY_ID
   git config --global commit.gpgsign true
   
   # Sign commits
   git commit -S -m "Your commit message"
   ```

2. **Temporarily disable signature requirement** (for setup only):
   - Go to Settings → Branches → Edit rule
   - Uncheck "Require signed commits"
   - Save changes

### Issue: "Required status checks must pass"

**Error Message:**
```
remote: - Required status checks must pass.
```

**Solutions:**
1. **Set up CI/CD pipeline** (GitHub Actions, Jenkins, etc.)
2. **Disable status checks** if not needed:
   - Go to Settings → Branches → Edit rule
   - Uncheck "Require status checks to pass before merging"

### Issue: Merge Conflicts

**Error Message:**
```
CONFLICT (content): Merge conflict in filename
```

**Solution:**
1. **Pull latest changes**:
   ```bash
   git fetch upstream
   git checkout main
   git merge upstream/main
   ```
2. **Resolve conflicts** in your feature branch:
   ```bash
   git checkout feature/your-branch
   git merge main
   # Resolve conflicts manually
   git add .
   git commit -m "Resolve merge conflicts"
   ```

## Best Practices

### Repository Setup
- ✅ **Start with protection disabled** for initial setup
- ✅ **Enable protection gradually** as you add more features
- ✅ **Test the workflow** with a test pull request
- ✅ **Document the process** for your team

### Team Collaboration
- ✅ **Use descriptive branch names**: `feature/user-authentication`, `bugfix/login-error`
- ✅ **Write clear commit messages**: "Add: User authentication module"
- ✅ **Create focused pull requests**: One feature per PR
- ✅ **Request specific reviewers** for relevant changes

### Code Quality
- ✅ **Set up automated testing** and require it to pass
- ✅ **Use CODEOWNERS file** for expert reviews
- ✅ **Require multiple approvals** for critical changes
- ✅ **Use draft pull requests** for work in progress

### Security
- ✅ **Enable commit signing** for all contributors
- ✅ **Use personal access tokens** instead of passwords
- ✅ **Set up two-factor authentication** on GitHub accounts
- ✅ **Regularly review repository access** and permissions

## Advanced Configuration

### CODEOWNERS File
Create `.github/CODEOWNERS` to specify who can review specific files:

```
# Global owners
* @username

# Mule configuration files
src/main/mule/ @mule-expert
pom.xml @mule-expert

# Documentation
*.md @documentation-team
docs/ @documentation-team
```

### Required Status Checks
Set up GitHub Actions or other CI/CD tools to run:
- Unit tests
- Integration tests
- Code quality checks
- Security scans

### Branch Protection for Multiple Branches
You can protect multiple branches:
- `main` - Production-ready code
- `develop` - Integration branch
- `release/*` - Release preparation branches

### Custom Roles and Permissions
- Create custom roles with specific permissions
- Assign different access levels to team members
- Use organization-level permissions for enterprise setups

## Verification Checklist

After setting up branch protection, verify:

- [ ] Direct pushes to main are blocked
- [ ] Pull requests are required for all changes
- [ ] Required approvals are enforced
- [ ] Status checks run and must pass
- [ ] Code owner reviews are required (if configured)
- [ ] Commit signing is enforced (if enabled)
- [ ] Team members can fork and create branches
- [ ] Pull request workflow works end-to-end

## Support and Resources

### GitHub Documentation
- [About protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches)
- [Managing a branch protection rule](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule)
- [CODEOWNERS file](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)

### Git and GitHub CLI
- [Git documentation](https://git-scm.com/doc)
- [GitHub CLI](https://cli.github.com/)
- [GPG signing setup](https://docs.github.com/en/authentication/managing-commit-signature-verification)

---

**Document created**: January 2025  
**Project**: Mule Integration with GitHub  
**Last updated**: January 2025
