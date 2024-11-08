Modify File Content
===

[![Buy me a coffee](https://img.shields.io/badge/Buy%20me%20a%20coffee-048754?logo=buymeacoffee)](https://idimetrix.github.io/#/sponsor)
[![test](https://github.com/idimetrix/github-action-modify-file-content/actions/workflows/ci.yml/badge.svg)](https://github.com/idimetrix/github-action-modify-file-content/actions/workflows/ci.yml)

Replace text content and submit content

Here is the example: update time <!--GAMFC-->2024-06-25 15:56:51<!--GAMFC-END-->

Here is the different delimiter example: <!--GAMFC_TABEL-->different `GAMFC_TABEL` & `GAMFC_TABEL-END` (test)<!--GAMFC_TABEL-END-->

## Inputs

- `token` Your `GITHUB_TOKEN`. This is required. Why do we need `token`? Read more here: [About the GITHUB_TOKEN secret](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/authenticating-with-the-github_token#about-the-github_token-secret). Default: `${{ github.token }}`
- `body` what needs to be replaced
- `path` file to be replaced
- `branch` The branch where the files are committed. Default: `${{ github.ref_name }}`
- `ref` The name of the commit/branch/tag. Default: the repository’s default branch (usually `master`)
- `overwrite` Overwrite the entire file content, by default `false`
- `sync_local_file` Sync local file content, by default `true`
- `message` The commit message. by default `doc: update <file path>.`
- `committer_name` The name of the author or committer of the commit. by default `github-actions[bot]`
- `committer_email` The email of the author or committer of the commit. by default `github-actions[bot]@users.noreply.github.com`
- `openDelimiter` Character to use for opening delimiter, by default "<\!--GAMFC-->"
- `closeDelimiter` Character to use for closing delimiter, by default "<\!--GAMFC-END-->"

## Outputs

- `content` text file content

## Example Usage

```yml
- name: Modify README.md
  uses: idimetrix/github-action-modify-file-content@main
  with:
    path: README.md
```

`README.md` file content

```markdown
update time <!--GAMFC-->2024-06-25 15:56:51<!--GAMFC-END-->
```

Replace the content between `<!--GAMFC-->2024-06-25 15:56:51<!--GAMFC-END-->`.

### format date

```yml
- name: Modify README.md
  uses: idimetrix/github-action-modify-file-content@main
  with:
    path: README.md
    body: "{{date:YYYY-MM-DD HH:mm:ss}}"
```

### overwrite file

```yml
- name: Modify README.md
  uses: idimetrix/github-action-modify-file-content@main
  with:
    path: README.md
    body: "overwrite file content {{date:YYYY-MM-DD HH:mm:ss}}",
    overwrite: 'true'
```

### specify branch changes

```yml
- name: Modify test test/overwrite.file.md
  uses: idimetrix/github-action-modify-file-content@main
  with:
    branch: test
    path: test/overwrite.file.md
    body: "{{date:YYYY-MM-DD HH:mm:ss}}"
    overwrite: 'true'
```

## See Also

- [Github Release Changelog Generator](https://github.com/idimetrix/changelog-generator) A GitHub Action that compares the commit differences between two branches
- [Create Tags From](https://github.com/idimetrix/create-tag-action) Auto create tags from commit or package.json.
- [Github Action Contributors](https://github.com/idimetrix/github-action-contributors) Github action generates dynamic image URL for contributor list to display it!
- [Generated Badges](https://github.com/idimetrix/generated-badges) Create a badge using GitHub Actions and GitHub Workflow CPU time (no 3rd parties servers)
- [Create Coverage Badges](https://github.com/idimetrix/coverage-badges-cli) Create coverage badges from coverage reports. (no 3rd parties servers)
- [Github Action package](https://github.com/idimetrix/github-action-package) Read and modify the contents of `package.json`.
- [Github Action EJS](https://github.com/idimetrix/github-action-package) A github action to render a ejs template using github context.
- [Github Action Read File Content](https://github.com/idimetrix/github-action-read-file) 
Read file contents. You can also get the file content in the branch.

## License

Licensed under the MIT License.
