# generator-latex-template ![Tests](https://github.com/latextemplates/generator-latex-template/workflows/Tests/badge.svg) [![npm version](http://img.shields.io/npm/v/generator-latex-template.svg?style=flat)](https://npmjs.org/package/generator-latex-template "View this project on npm")

> Generates latextemplates (e.g., for thesis, workshops, conferences, IEEEtran, LNCS, ...) out of "micro-templates"

See the **[Talk about the generator](https://github.com/dante-ev/Vortraege_Tagungen/blob/master/2019-Herbst/Oliver%20Kopp%20-%20The%20LaTeX%20Template%20Generator%20-%20dante2019-herbst.pdf)** for an overview on the aims and the general concept.

## Background information

There are many latex templates out there.
All of them make use of certain packages such as [hyperref], [listings], or [minted].
The packages have to be a) included in the `.tex` file somehow and b) configured.
Moreover, some packages offer interfaces (such as new commands or new environments) to users.
Minimal examples help to understand how a package works.

The aim of the repository is to provide for each common latex package

1. Configuration
2. Usage example

and a generation into templates:

1. Support for LNCS, IEEE, KOMA-Script
2. Support for separate documents which require `--shell-escape` and not.
3. Support for integrated pdflatex and lualatex documents

## Talks

- [Oliver Kopp - The LaTeX Template Generator](https://github.com/dante-ev/Vortraege_Tagungen/blob/master/2019-Herbst/Oliver%20Kopp%20-%20The%20LaTeX%20Template%20Generator%20-%20dante2019-herbst.pdf) - a talk on the motivation, user experience, and the contribution

## Usage

### Installing `generator-latex-template`

You can install `generator-latex-template` using following command:

```bash
npm install -g generator-latex-template
```

### Using the generator

You can run the generator by invoking this command on a command prompt:

```bash
yo latex-template
```

## How to update the document

⚠️ The template generator overwrites `main.tex` on each run. This will destroy your work. ⚠️

You can use the magic of `git` to prevent that:

1. After repository initialization:

   - `git commit` to save your work
   - `git checkout -b template` - to create a branch with initial template (required for updating)
   - `git checkout master` switch back to your thesis

2. Work on the `master` branch
3. In case an update comes in, update the `template` branch

   - `git checkout template` - switch to the `template` branch
   - `yo latex-template` - generate new template
   - `git commit` - save the new template
   - `git checkout master` - switch to your work
   - `git merge template` - merge in the template changes
   - resolve conflicts ^^ (Hint: IntelliJ Community Edition has a [great conflict resolving tool](https://www.jetbrains.com/help/idea/resolving-conflicts.html#))

## Resources

- [IEEE](https://latextemplates.github.io/IEEE/) - example: [paper-conference-minted.tex](https://github.com/latextemplates/IEEE/blob/master/paper-conference-minted.tex)
- [LNCS](https://latextemplates.github.io/LNCS/) - example: [paper.tex](https://github.com/latextemplates/LNCS/blob/master/paper.tex)
- [scientific-thesis-template](https://latextemplates.github.io/scientific-thesis-template/) - example: [latexhints-english.tex](https://github.com/latextemplates/scientific-thesis-template/blob/master/latexhints-english.tex)
- [alpenwasser/TeX](https://github.com/alpenwasser/TeX)

## Development roadmap

- [x] Create directory structure
- [ ] Sort in examples from the [scientific-thesis-template](http://latextemplates.github.io/scientific-thesis-template/)
- [ ] Have scientific-thesis-template generated completely.
- [ ] Have LNCS generated completely.
- [ ] Have [uni-stuttgart-dissertation-template](https://github.com/latextemplates/uni-stuttgart-dissertation-template) generated automatically.

In the long run, the contents of the `paper.tex` (and similar) files in repositories of the [latextemplates](https://latextemplates.github.io/) organization should be generated automatically.

## Development hints

- Templating language: <https://ejs.co/>
- Conditional questions: <https://stackoverflow.com/a/18706640/873282>.
- Types of prompts: <https://github.com/SBoudrias/Inquirer.js#prompt-types>
  - E.g,. [Question](https://github.com/SBoudrias/Inquirer.js#question)
- Add a new question
  - Also adapt `__tests__/app.js`
  - Execute tests with `npx jest`
- Test locally
  - Create empty directory ("target directory")
  - Change to the target directory
  - Run `npx yo <path-to-git-repository>`
    - Windows: `npx yo c:\git-repositories\latextemplates\generator-latex-template`
  - Parameters can be set using command line
    - Windows: `npx yo c:\git-repositories\latextemplates\generator-latex-template --texlive=tl2020 --documentclass=scientific-thesis --latexcompiler=lualatex --bibtextool=biblatex --language=en --font=arial --listings=listings --cleveref=true --enquotes=csquotes --tweak_outerquote=babel --todo=pdfcomment --examples=true`
    - Windows automatic generation of a LNCS template (with lualatex and bibtex): `npx yo c:\git-repositories\latextemplates\generator-latex-template --documentclass=lncs --latexcompiler=lualatex --bibtextool=bibtex --texlive=tl2020 --language=en --font=default  --listings=listings --cleveref=true --enquotes=csquotes --tweak_outerquote=babel --todo=pdfcomment --examples=true`
  - Run `latexmk` to build the PDF
- Update npm dependencies: `npx npm-update-all`. See [FreeCodeCamp](https://www.freecodecamp.org/news/10-npm-tricks-that-will-make-you-a-pro-a945982afb25/) for more details.
  - See <https://github.com/yeoman/generator/releases> for changes in the generator.

### Releasing a new version

1. Update `CHANGELOG.md`
2. Update `package.json`, publish to [npmjs](https://www.npmjs.com/package/generator-latex-template), create GitHub release.
   Use [release-it](https://www.npmjs.com/package/release-it) (do not create a release on GitHub) and [github-release-from-changelog](https://www.npmjs.com/package/github-release-from-changelog).

   - `npx release-it`
   - `npx github-release-from-changelog`

## License

The code is licensed MIT, the snippets (both LaTeX and text) [CC0](https://creativecommons.org/share-your-work/public-domain/cc0/).

[hyperref]: https://ctan.org/pkg/hyperref
[listings]: https://ctan.org/pkg/listings
[minted]: https://ctan.org/pkg/minted

<!-- markdownlint-disable-file MD013 -->
