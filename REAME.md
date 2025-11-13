# Dev Practices Handbooks

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![LaTeX](https://img.shields.io/badge/Made%20with-LaTeX-1f425f.svg)](https://www.latex-project.org/)

A comprehensive collection of professional software development handbooks covering essential practices for building maintainable, scalable, and reliable software systems. These handbooks are written as complete LaTeX books with practical examples, real-world scenarios, and actionable exercises.

## 📚 Available Handbooks

### 🐍 Python Development Best Practices

**A complete guide for intermediate and advanced Python developers**

Transform your Python code from "scripts that work" to production-ready systems that age gracefully. This handbook covers:

- **Code Quality**: Style enforcement, documentation strategies, and readability principles
- **Architecture**: Project structure, dependency injection, and modular design patterns
- **Reliability**: Comprehensive testing strategies, type hints, and error handling
- **Operations**: Configuration management, security practices, and performance optimization
- **Collaboration**: Git workflows, code review culture, and CI/CD best practices
- **Deployment**: Packaging, versioning, and distribution strategies

**Key Features:**

- Python 3.12+ examples with modern idioms
- Real case studies from production systems
- Hands-on exercises for skill reinforcement
- Integration with tools like `ruff`, `mypy`, `pytest`, and `black`

### 🔄 Git and GitHub Best Practices

**Master version control for professional development teams**

Elevate your Git proficiency from basic commands to enterprise-grade workflows. This handbook covers:

- **Mental Models**: Understanding Git's internal structure and operations
- **Workflows**: Branching strategies, merge vs rebase decisions, and conflict resolution
- **Collaboration**: Pull request best practices, code review protocols, and team coordination
- **Automation**: GitHub Actions, CI/CD pipelines, and automated quality gates
- **Security**: Signed commits, secret scanning, and compliance requirements
- **Advanced Topics**: Monorepo strategies, bisecting bugs, and disaster recovery

**Key Features:**

- Command-line examples with explanations
- GitHub API automation scripts
- Incident response playbooks
- Repository hygiene checklists

## 🏗️ Repository Structure

```
dev-practices-handbooks/
├── README.md                          # This file
├── LICENSE                            # MIT License
├── .gitignore                         # LaTeX and build artifacts
│
├── python-best-practices/             # Python handbook
│   ├── main.tex                       # Main LaTeX file
│   ├── chapters/                      # Individual chapters
│   │   ├── ch01_introduction.tex
│   │   ├── ch02_code_style_readability.tex
│   │   ├── ch03_comments_documentation.tex
│   │   ├── ch04_project_structure.tex
│   │   ├── ch05_dependencies_environments.tex
│   │   ├── ch06_type_hints_static_analysis.tex
│   │   ├── ch07_testing_quality.tex
│   │   ├── ch08_error_handling_logging.tex
│   │   ├── ch09_configuration_secrets.tex
│   │   ├── ch10_performance_scalability.tex
│   │   ├── ch11_security.tex
│   │   ├── ch12_packaging_versioning.tex
│   │   ├── ch13_collaboration_git_ci.tex
│   │   ├── ch14_case_studies.tex
│   │   └── ch15_checklists_appendix.tex
│   └── output/                        # Generated PDFs (optional)
│
├── git-github-best-practices/         # Git handbook
│   ├── main.tex                       # Main LaTeX file
│   ├── latex/                         # Chapter files
│   │   ├── 01-introduction-why-version-control-discipline-matters.tex
│   │   ├── 02-mental-models-for-git.tex
│   │   ├── 03-personal-git-hygiene.tex
│   │   ├── 04-commits-units-of-change.tex
│   │   ├── 05-branching-strategies.tex
│   │   ├── 06-merging-rebasing-and-conflict-resolution.tex
│   │   ├── 07-working-with-remotes-and-forks.tex
│   │   ├── 08-github-repository-hygiene.tex
│   │   ├── 09-pull-requests-and-code-review.tex
│   │   ├── 10-continuous-integration-and-github-actions.tex
│   │   ├── 11-release-management-and-tags.tex
│   │   ├── 12-security-secrets-and-compliance.tex
│   │   ├── 13-advanced-workflows-and-troubleshooting.tex
│   │   └── 14-checklists-templates-and-further-reading.tex
│   └── output/                        # Generated PDFs (optional)
```

## 🚀 Quick Start

### Prerequisites

- **LaTeX Distribution**: TeX Live (recommended) or MiKTeX
- **Build Tools**: `pdflatex` and `latexmk`
- **Optional**: VS Code with LaTeX Workshop extension

### Building the Handbooks

#### Python Best Practices Handbook

```bash
cd python-best-practices
pdflatex main.tex

# Or use latexmk for automatic dependency resolution
latexmk -pdf main.tex
```

#### Git & GitHub Best Practices Handbook

```bash
cd git-github-best-practices
pdflatex main.tex

# Or use latexmk
latexmk -pdf main.tex
```

### Using Docker (Alternative)

If you prefer not to install LaTeX locally:

```bash
# Build using Docker
docker run --rm -v $(pwd):/workspace texlive/texlive:latest \
  bash -c "cd /workspace/python-best-practices && pdflatex main.tex"
```

## 🎯 Target Audience

### Python Handbook

- **Intermediate developers** ready to move beyond basic scripting
- **Senior engineers** looking to standardize team practices
- **Technical leads** implementing code quality initiatives
- **DevOps engineers** seeking Python-specific best practices

### Git Handbook

- **Developers** who know basic Git but want to master advanced workflows
- **Team leads** establishing branching strategies and review processes
- **Platform engineers** implementing CI/CD and automation
- **Compliance teams** requiring audit trails and security practices

## 📖 How to Use These Handbooks

### For Individual Learning

1. **Sequential Reading**: Work through chapters in order for comprehensive coverage
2. **Topic-Focused**: Jump to specific chapters addressing current challenges
3. **Hands-On Practice**: Complete exercises at the end of each chapter
4. **Reference Guide**: Use as a lookup resource for specific patterns and solutions

### For Team Adoption

1. **Book Clubs**: Organize chapter-by-chapter discussion sessions
2. **Onboarding**: Include relevant chapters in new hire orientation
3. **Code Review Standards**: Reference handbook patterns in review guidelines
4. **Lunch & Learn**: Present key concepts from individual chapters
5. **Policy Development**: Use checklists and templates for team standards

### For Organizations

1. **Standards Documentation**: Adapt handbook content for internal style guides
2. **Training Curricula**: Structure learning paths around handbook chapters
3. **Quality Gates**: Implement handbook recommendations in CI/CD pipelines
4. **Incident Learning**: Reference relevant sections in post-incident reviews

## 🛠️ Advanced Build Options

### Custom LaTeX Configuration

Create a `.latexmkrc` file for automated builds:

```perl
$pdf_mode = 1;
$pdflatex = 'pdflatex -interaction=nonstopmode -file-line-error';
$clean_ext = 'aux log out toc lot lof';
```

### Continuous Integration

Example GitHub Actions workflow:

```yaml
name: Build Handbooks
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Install LaTeX
      run: sudo apt-get update && sudo apt-get install -y texlive-full
    - name: Build Python Handbook  
      run: cd python-best-practices && latexmk -pdf main.tex
    - name: Build Git Handbook
      run: cd git-github-best-practices && latexmk -pdf main.tex
    - name: Upload PDFs
      uses: actions/upload-artifact@v4
      with:
        name: handbooks
        path: '**/*.pdf'
```

## 🤝 Contributing

We welcome contributions that improve clarity, add relevant examples, or extend coverage to new domains.

### Types of Contributions

- **Content Improvements**: Better examples, clearer explanations, updated practices
- **New Sections**: Additional topics within existing handbooks
- **Case Studies**: Real-world scenarios and solutions
- **Exercises**: Practical activities that reinforce concepts
- **Tools Integration**: Examples using newer tools or updated versions

### Contribution Process

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/improve-testing-chapter`)
3. **Make** your changes following our LaTeX style conventions
4. **Test** by building the affected handbook locally
5. **Submit** a pull request with a clear description of changes

### Style Guidelines

- Use consistent LaTeX formatting and naming conventions
- Include practical, working code examples
- Provide context and motivation for recommendations
- Add exercises that reinforce key concepts
- Reference external tools and resources appropriately

## 📝 Changelog & Versioning

We follow semantic versioning for major content updates:

- **Major** (1.0.0 → 2.0.0): Significant structural changes or new handbooks
- **Minor** (1.0.0 → 1.1.0): New chapters or substantial content additions
- **Patch** (1.0.0 → 1.0.1): Bug fixes, typos, and minor improvements


## 📄 License

This project is licensed under the MIT License – see the LICENSE file for details.

This means you can:

- ✅ Use these handbooks in commercial projects
- ✅ Modify and distribute adapted versions
- ✅ Include content in internal training materials
- ✅ Reference and quote with attribution

## 👨‍💻 Author

**Diogo Ribeiro**

- Lead Data Scientist at [Mysense.ai](https://mysense.ai)
- Researcher & Instructor at ESMAD - Instituto Politécnico do Porto
- Master's in Mathematics | ORCID: [0009-0001-2022-7072](https://orcid.org/0009-0001-2022-7072)

**Connect with me:**

- 🌐 Website: [diogoribeiro7.github.io](https://diogoribeiro7.github.io)
- 💼 GitHub: [@DiogoRibeiro7](https://github.com/DiogoRibeiro7)
- 📧 Email: <dfr@esmad.ipp.pt>

## 🙏 Acknowledgments

These handbooks synthesize knowledge from:

- Years of production software development across multiple industries
- Code review patterns from high-performing engineering teams
- Open source contributions and community best practices
- Academic research in software engineering and computer science
- Field experience with modern development toolchains

Special thanks to the Python and Git communities for building the robust ecosystems these handbooks document.

## 🔗 Related Resources

### External References

- [Python.org Official Documentation](https://docs.python.org/)
- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Documentation](https://docs.github.com/)
- [Pro Git Book](https://git-scm.com/book) by Scott Chacon & Ben Straub
- [Effective Python](https://effectivepython.com/) by Brett Slatkin

### Tool Documentation

- [Ruff Linter](https://docs.astral.sh/ruff/)
- [mypy Type Checker](https://mypy.readthedocs.io/)
- [pytest Testing Framework](https://docs.pytest.org/)
- [GitHub Actions](https://docs.github.com/en/actions)

--------------------------------------------------------------------------------

⭐ **If you find these handbooks useful, please consider starring this repository and sharing it with your team!**
