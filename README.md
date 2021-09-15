# Publish website on Github Pages with MKDocs

1. Create Github repository, for example `gokb-website`.
2. Create a branch `gh-pages`
3. Enable "GitHub Pages" under "Settings".

    Source: 
    - Branch: `github-pages`
    - Folder: `(root)`

4. Add content, see [MKDocs](https://www.mkdocs.org/user-guide/writing-your-docs/).
5. Add "Github Action" to `.github/workflows/ci.yml`, see [MKDocs-Material](https://squidfunk.github.io/mkdocs-material/publishing-your-site/#github-pages). Add `pip install ...` for custom plugins:

    ```yml
    name: ci 
    on:
    push:
        branches: 
        - master
        - main
    jobs:
    deploy:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - uses: actions/setup-python@v2
            with:
            python-version: 3.x
        - run: pip install mkdocs 
        - run: pip install mkdocs[i18n]
        - run: pip install mkdocs-static-i18n
        - run: pip install mkdocs-material 
        - run: pip install mkdocs-localsearch 
        - run: mkdocs gh-deploy --force
    ```

## Adding new pages and categories

You can add new pages by adding new Markdown files to the `docs/` folder.

To add new categories create a new folder in `docs/` and insert Markdown files. You have to define the new category in the configuration `mkdocs.yml`:

```yml
nav:
  - Home: index.md
  - News: news.md
  - Documentation:
    - KBART introduction: documentation/kbart-introduction.md
    - Registration and login: documentation/registration-and-login.md
    - Create and edit provider: documentation/create-and-edit-provider.md
    - Create and edit packages: documentation/create-and-edit-packages.md
    - Guidelines for package names: documentation/guidelines-for-package-names.md
  - Presentations: presentations.md
  - Publications: publications.md
  - Get involved: get-involved.md
  - Contact: contact.md
```

To edit files you can use the ["Gihub Web Editor"](https://github.dev/github/dev) and/or the Chrome browser extension ["Github Web IDE"](https://chrome.google.com/webstore/detail/github-web-ide/adjiklnjodbiaioggfpbpkhbfcnhgkfe/related).

Store images in `docs/assets/`.

## Multilingual site

A multilingual website can be created with help of the MKDocs plugin [mkdocs-static-i18n](https://github.com/ultrabug/mkdocs-static-i18n). Add the plugin to the configuration `mkdocs.yml`:

```yml
plugins:
  - i18n:
      default_language: en
      languages:
        en: EN
        de: DE
      nav_translations:
        de:
          Presentations: Präsentationen
          Publications: Publikationen
```

Add the language names, like `en` or `de` to the file names of your Markdown files:

```terminal
├── docs
│   ├── index.de.md
│   ├── index.en.md
│   ├── news.en.md
│   ├── presentations.de.md
│   ├── presentations.en.md
│   ├── publications.de.md
│   └── publications.en.md
```

## Local search plugin

See https://github.com/wilhelmer/mkdocs-localsearch#installation-material-v5

## To Do
- Translate EN content to DE
- Add DE documentation
- Add impressum and data protection declaration
- Configure custom domain, see https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site
