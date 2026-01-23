# Takaya Ebino's Resume

An automated resume management system with multi-format publishing (Markdown, PDF, Web) and quality assurance powered by textlint.

## Published Resume

- [Japanese Version (日本語)](https://takaya787.github.io/resume-for-engineer/)
- [English Version](https://takaya787.github.io/resume-for-engineer/en)

<p>

<a href="https://github.com/takaya787/resume-for-engineer/actions/workflows/lint-text.yml" target="_blank"><img alt="lint_text" src="https://img.shields.io/github/workflow/status/takaya787/resume-for-engineer/lint%20text?label=textlint&logo=github&color=yellow" /></a>

<a href="https://github.com/takaya787/resume-for-engineer/actions?query=workflow%3A%22build+%22" target="_blank" ><img alt="build_pdf" src="https://img.shields.io/github/workflow/status/takaya787/resume-for-engineer/build-pdf?label=build%20pdf&logo=github"/></a>

<a href="https://github.com/takaya787/resume-for-engineer/tags" target="_blank" ><img alt="release" src="https://img.shields.io/github/release-date/takaya787/resume-for-engineer?color=blue&logo=github"/></a>

</p>

## Available Formats

| Format       | Japanese                                                                            | English                                                                                |
| ------------ | ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| **Web**      | [View](https://takaya787.github.io/resume-for-engineer/)                            | [View](https://takaya787.github.io/resume-for-engineer/en)                             |
| **PDF**      | [Download](https://github.com/takaya787/resume-for-engineer/releases/)              | [Download](https://github.com/takaya787/resume-for-engineer/releases/)                 |
| **Markdown** | [View](https://github.com/takaya787/resume-for-engineer/blob/master/docs/README.md) | [View](https://github.com/takaya787/resume-for-engineer/blob/master/docs/en/README.md) |

## Prerequisites

- Node.js v18 or higher
- npm or yarn package manager
- Git

## Getting Started

### Installation

1. Clone the repository:

```bash
git clone https://github.com/takaya787/resume-for-engineer.git
cd resume-for-engineer
```

2. Install dependencies:

```bash
npm install
# or
yarn install
```

3. Set up Git hooks:

```bash
npm run prepare
# or
yarn prepare
```

### Project Structure

```
resume-for-engineer/
├── docs/
│   ├── README.md           # Japanese resume (main content)
│   ├── en/README.md        # English resume
│   └── _config.yml         # Jekyll configuration for GitHub Pages
├── pdf-configs/
│   ├── config.js           # PDF generation settings
│   └── style.css           # PDF styling (fonts, layout)
├── .github/
│   └── workflows/          # CI/CD automation
│       ├── build-pdf.yml   # PDF generation on tag push
│       └── lint-text.yml   # Text linting on push/PR
├── .textlintrc             # Japanese text linting rules
└── package.json            # Project dependencies and scripts
```

## Features

### 💅 Automatic Text Linting

Ensures high-quality Japanese technical writing with [textlint](https://github.com/textlint/textlint).

**Manual linting:**

```bash
npm run lint
# or
yarn lint
```

**Auto-fix issues:**

```bash
npm run lint:fix
# or
yarn lint:fix
```

**Pre-commit hook:**

- Automatically runs textlint before each commit via [husky](https://github.com/typicode/husky)
- Prevents commits with linting errors
- Configure rules in `.textlintrc`

**Supported rules:**

- Japanese technical writing standards
- JTF (Japanese Translation Federation) style guide
- Proper spacing and punctuation
- Typography consistency

### 📝 PDF Generation

Generate professional PDFs from Markdown using [md-to-pdf](https://www.npmjs.com/package/md-to-pdf).

**Generate both Japanese and English PDFs:**

```bash
npm run build:pdf
# or
yarn build:pdf
```

**Generate specific language:**

```bash
npm run build:pdf:ja    # Japanese only
npm run build:pdf:en    # English only
```

**Customization:**

- Edit `pdf-configs/style.css` for styling (fonts, colors, layout)
- Edit `pdf-configs/config.js` for PDF settings (paper size, margins, headers/footers)
- PDFs use Noto Sans Japanese fonts for proper rendering

### 🛠 Automated Release

GitHub Actions automatically builds and publishes PDFs when you create version tags.

**Workflow:**

1. Update resume content in `docs/README.md` or `docs/en/README.md`
2. Commit changes:

```bash
git add docs/README.md
git commit -m "Update job experience"
```

3. Create and push a version tag:

```bash
git tag v1.0.0
git push origin v1.0.0
```

4. GitHub Actions will:
   - Run textlint checks
   - Generate Japanese and English PDFs
   - Create a GitHub Release
   - Upload PDFs as release assets

**Tag naming convention:**

- Use semantic versioning: `v1.0.0`, `v1.1.0`, `v2.0.0`
- Major version: Significant career changes
- Minor version: Adding new experiences or skills
- Patch version: Minor corrections or updates

## Development Workflow

### Editing Resume Content

1. Edit the Markdown files:
   - Japanese: `docs/README.md`
   - English: `docs/en/README.md`

2. Check formatting locally:

```bash
npm run lint
```

3. Fix any linting issues:

```bash
npm run lint:fix
```

4. Preview PDF output:

```bash
npm run build:pdf
```

5. Commit and push:

```bash
git add docs/
git commit -m "Update work experience"
git push origin main
```

### Publishing a New Version

```bash
# Create a release tag
git tag -a v1.2.0 -m "Add new project experience"
git push origin v1.2.0

# View the automated release
# Visit: https://github.com/takaya787/resume-for-engineer/releases
```

## Configuration

### Textlint Rules

Modify `.textlintrc` to customize linting rules:

- Japanese technical writing standards
- Sentence length limits
- Terminology consistency
- Spacing and punctuation rules

### PDF Styling

Customize PDF appearance in `pdf-configs/`:

- `style.css`: Fonts, colors, spacing, table formatting
- `config.js`: Page size, margins, metadata

### GitHub Pages

Modify `docs/_config.yml` for Jekyll theme customization:

- Theme selection
- Site title and description
- Navigation settings

## Available Scripts

| Script                 | Description                                         |
| ---------------------- | --------------------------------------------------- |
| `npm run lint`         | Check text quality with textlint                    |
| `npm run lint:fix`     | Auto-fix linting issues                             |
| `npm run build:pdf`    | Generate both Japanese and English PDFs             |
| `npm run build:pdf:ja` | Generate Japanese PDF only                          |
| `npm run build:pdf:en` | Generate English PDF only                           |
| `npm run prepare`      | Set up Git hooks (runs automatically after install) |

## Troubleshooting

### PDF Generation Issues

If PDF generation fails:

```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install

# Try generating again
npm run build:pdf
```

### Textlint Errors

If textlint reports errors:

1. Review the specific rule violation in the output
2. Fix manually or use `npm run lint:fix` for auto-fixes
3. For false positives, add exceptions in `.textlintrc`

### Git Hooks Not Working

Reinstall hooks:

```bash
npm run prepare
# or
npx husky install
```

## License

This project structure can be freely used as a template for your own resume.

## Acknowledgments

Built with:

- [textlint](https://github.com/textlint/textlint) - Text linting
- [md-to-pdf](https://www.npmjs.com/package/md-to-pdf) - PDF generation
- [husky](https://github.com/typicode/husky) - Git hooks
- [Jekyll](https://jekyllrb.com/) - GitHub Pages publishing
