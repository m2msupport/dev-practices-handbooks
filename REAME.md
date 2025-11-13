# Dev Practices Handbooks

This repository collects a series of LaTeX handbooks about professional software
engineering practices. The focus is on concrete habits that help teams keep
their projects readable, maintainable, and easy to evolve.

Right now the repo includes:

* **Python Development Best Practices**
* **Git and GitHub Best Practices**

Both are written as books in LaTeX and are intended to be built into PDF.

> ⚠️ Note
> If you are using a `.gitignore` that ignores everything except `*.tex` and
> `*.pdf`, you will need to whitelist `README.md` (and any other metadata files)
> to keep this file under version control.

---

## Repository layout

A suggested layout is:

```text
dev-practices-handbooks/
  python-best-practices/
    main.tex           # Python best practices book
    chapters/          # Optional: split chapters
    output/            # Optional: generated PDFs
  git-github-best-practices/
    main.tex           # Git & GitHub best practices book
    chapters/
    output/
  README.md
  .gitignore
```

You can adapt the structure, but the idea is that each handbook lives in its own
subdirectory with its own LaTeX sources and outputs.

---

## Books in this repository

### 1. Python Development Best Practices

A handbook for intermediate and advanced Python developers who want to:

* Move from “scripts that work” to **projects that age well**
* Standardise **style, structure, and testing** across a team
* Use **type hints, logging, configuration, and packaging** in a disciplined way
* Integrate Python projects with **CI/CD, observability, and release processes**

The book is written in LaTeX (`book` class) and includes:

* Explanations of common practices and trade–offs
* Realistic Python 3.12 examples with type hints and docstrings
* Short project scenarios based on real-world patterns
* Exercises at the end of each chapter

Typical entry point: `python-best-practices/main.tex`.

---

### 2. Git and GitHub Best Practices

A handbook for developers who already use Git every day but want to:

* Keep histories **clean and understandable**
* Use **branches, merges, and rebases** without fear
* Make **pull requests** easier to review and safer to merge
* Configure **GitHub repositories, branch protection, and Actions** sensibly
* Handle **releases, tags, and hotfixes** in a predictable way

The book focuses on mental models and workflows rather than memorising all
commands. It includes:

* Shell listings for Git workflows
* Examples of `.gitconfig`, GitHub Actions workflows, and repository settings
* “Bad vs good” history and pull request patterns
* Exercises to practise on real or toy repositories

Typical entry point: `git-github-best-practices/main.tex`.

---

## Building the PDFs

You need a LaTeX toolchain installed (for example TeX Live or MiKTeX).

From the root of the repo, you can build each book separately.

### Python book

```bash
cd python-best-practices

# Simple pdflatex run (may need multiple runs for references)
pdflatex main.tex

# or use latexmk to manage multiple passes
latexmk -pdf main.tex
```

The resulting PDF will usually be `main.pdf` in the same directory (or in a
configured `output/` directory if you use `latexmk` options).

### Git & GitHub book

```bash
cd git-github-best-practices

pdflatex main.tex
# or
latexmk -pdf main.tex
```

Again, the output will be a single PDF containing the full handbook.

---

## .gitignore and tracked files

If you want this repository to only track LaTeX sources and PDFs, a minimal
`.gitignore` could look like:

```gitignore
# Ignore everything by default
*

# Keep the gitignore itself
!.gitignore

# Keep LaTeX sources and generated PDFs
!**/*.tex
!**/*.pdf

# (Optional) Keep the README as well
!README.md
```

If you later add CI configs, Makefiles, or other support files, you may want to
whitelist them too.

---

## How to use these handbooks

Some ideas:

* As internal material for onboarding new team members
* As a basis for **lunch-and-learn** sessions or study groups
* As reference documents you link from other repos (e.g. CONTRIBUTING guides)
* As a starting point for specialised variants (data platforms, ML projects, etc.)

You can read them linearly as books, or dip into specific chapters when you want
to improve a particular area (e.g. testing, releases, or branching strategies).

---

## Contributing

This repository is structured so that each handbook can evolve independently.

Typical contributions:

* Fixing typos or unclear explanations
* Adding or improving examples and exercises
* Proposing new sections or case studies based on real incidents
* Updating recommendations to match current tooling (e.g. new Git features,
  GitHub Actions changes, or Python versions)

If you plan to make bigger structural changes, it is useful to open an issue
first to discuss the direction.

---

## License

Add your preferred license here (for example MIT, Apache-2.0, or CC BY-SA)
and include the matching `LICENSE` file in the repository.

