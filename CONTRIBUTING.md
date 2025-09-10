# Contributing to Test Integration GitHub

Thank you for your interest in contributing to this Mule project! This document provides guidelines for contributing to the repository.

## Getting Started

### 1. Fork the Repository
- Click the "Fork" button on the GitHub repository page
- This creates your own copy of the repository

### 2. Clone Your Fork
```bash
git clone https://github.com/YOUR-USERNAME/test-integration-github.git
cd test-integration-github
```

### 3. Add Upstream Remote
```bash
git remote add upstream https://github.com/anarumanchi-Sf/test-integration-github.git
```

### 4. Create a Feature Branch
```bash
git checkout -b feature/your-feature-name
# or
git checkout -b bugfix/issue-description
```

## Development Workflow

### 1. Keep Your Fork Updated
```bash
git fetch upstream
git checkout main
git merge upstream/main
```

### 2. Make Your Changes
- Write clean, well-documented code
- Follow Mule best practices
- Test your changes thoroughly
- Update documentation if needed

### 3. Commit Your Changes
```bash
git add .
git commit -m "Add: Brief description of changes"
```

### 4. Push to Your Fork
```bash
git push origin feature/your-feature-name
```

### 5. Create a Pull Request
- Go to your fork on GitHub
- Click "New Pull Request"
- Select your feature branch
- Fill out the pull request template
- Request review from @anarumanchi-Sf

## Code Standards

### Mule Configuration
- Use descriptive names for flows and components
- Add proper documentation to complex logic
- Follow Mule naming conventions
- Use DataWeave for transformations when possible

### Java Code
- Follow Java naming conventions
- Add Javadoc comments for public methods
- Use meaningful variable and method names
- Handle exceptions appropriately

### Documentation
- Update README.md if adding new features
- Document any new configuration requirements
- Add comments to complex code sections

## Pull Request Guidelines

### Before Submitting
- [ ] Code follows project standards
- [ ] All tests pass (if applicable)
- [ ] Documentation is updated
- [ ] No merge conflicts with main branch
- [ ] Commit messages are descriptive

### Pull Request Template
- Use the provided pull request template
- Describe what changes were made
- Explain why the changes were necessary
- Reference any related issues
- Include screenshots if UI changes

## Branch Protection Rules

The main branch is protected with the following rules:
- ✅ Pull requests required for all changes
- ✅ At least 1 approval required
- ✅ Code owner review required
- ✅ No direct pushes to main
- ✅ Linear history enforced

## Getting Help

- Create an issue for questions or problems
- Use GitHub Discussions for general questions
- Contact @anarumanchi-Sf for urgent matters

## License

By contributing to this project, you agree that your contributions will be licensed under the same license as the project.

---

Thank you for contributing! 🚀
