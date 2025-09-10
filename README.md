# Test Integration GitHub

A Mule 4 application for testing GitHub integration and collaboration workflows.

## 🚀 Project Overview

This Mule application serves as a template for team collaboration using GitHub's branch protection rules and pull request workflows. It demonstrates best practices for Mule development in a collaborative environment.

## 📋 Prerequisites

- **Mule Runtime**: 4.9.9 or higher
- **Java**: Version 17
- **Maven**: 3.6 or higher
- **Anypoint Studio**: 7.x or higher (recommended)

## 🛠️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/anarumanchi-Sf/test-integration-github.git
cd test-integration-github
```

### 2. Import into Anypoint Studio
1. Open Anypoint Studio
2. File → Import → Existing Maven Projects
3. Select the project directory
4. Click Finish

### 3. Run the Application
```bash
mvn clean package
mvn mule:run
```

## 🏗️ Project Structure

```
test-integration-github/
├── src/
│   ├── main/
│   │   ├── mule/
│   │   │   └── test-integration-github.xml    # Main Mule flow
│   │   └── resources/
│   │       └── log4j2.xml                     # Logging configuration
│   └── test/
│       ├── java/                              # Unit tests
│       ├── munit/                             # MUnit tests
│       └── resources/
│           └── log4j2-test.xml               # Test logging
├── .github/                                   # GitHub workflows and templates
├── pom.xml                                   # Maven configuration
├── mule-artifact.json                        # Mule artifact metadata
└── README.md                                 # This file
```

## 🔧 Configuration

### Mule Artifact
- **Min Mule Version**: 4.9.9
- **Java Specification**: Version 17
- **Packaging**: mule-application

### Logging
Log4j2 configuration is provided for both main application and test environments.

## 🤝 Contributing

This project uses GitHub's branch protection rules to ensure code quality and collaboration. Please read our [Contributing Guidelines](CONTRIBUTING.md) before making changes.

### Quick Start for Contributors
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Create a pull request

## 📝 Branch Protection Rules

The main branch is protected with the following rules:
- ✅ Pull requests required for all changes
- ✅ At least 1 approval required
- ✅ Code owner review required
- ✅ No direct pushes to main
- ✅ Linear history enforced

## 🐛 Issue Reporting

Found a bug or have a feature request? Please use our issue templates:
- [Bug Report](.github/ISSUE_TEMPLATE/bug_report.md)
- [Feature Request](.github/ISSUE_TEMPLATE/feature_request.md)

## 📚 Documentation

### 📖 Project Documentation
- [**GitHub Setup Guide**](GitHub_Setup_Steps.md) - Complete setup documentation for pushing Mule projects to GitHub
- [**Branch Protection Setup Guide**](Branch_Protection_Setup.md) - Comprehensive guide on setting up protected branches and team workflows
- [**Contributing Guidelines**](CONTRIBUTING.md) - How to contribute to this project and team collaboration workflows

### 🔧 Technical References
- [MuleSoft Documentation](https://docs.mulesoft.com/) - Official Mule documentation
- [GitHub Branch Protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches) - GitHub's official branch protection documentation

### 📋 Quick Start Guides
1. **New to this project?** → Start with [GitHub Setup Guide](GitHub_Setup_Steps.md)
2. **Setting up team workflows?** → Read [Branch Protection Setup Guide](Branch_Protection_Setup.md)
3. **Want to contribute?** → Follow [Contributing Guidelines](CONTRIBUTING.md)
4. **Need help with Mule?** → Check [MuleSoft Documentation](https://docs.mulesoft.com/)

## 🔒 Security

- All commits must be signed
- Code owner review required for sensitive files
- No force pushes allowed
- Linear history enforced

## 📞 Support

For questions or support:
- Create an issue in this repository
- Contact the repository owner: @anarumanchi-Sf

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Happy Coding! 🚀**
