# stagit
> static git page generator

## Information
This is basically a pure shell script clone of [stagit](https://git.2f30.org/stagit/).

It is meant to be hosted on [Github](https://github.com) using [Github Pages](https://pages.github.com) with a [Custom domain](https://help.github.com/en/articles/using-a-custom-domain-with-github-pages).

A live demo of this script can be seen [here](https://acid.vegas).

## Settings
| Setting          | Default        | Description                                                        |
| ---------------- | -------------- | ------------------------------------------------------------------ |
| CLONE_URL        | remote         | base url for cloning repositories *(remote = remote.origin.url)*   |
| CNAME            | empty          | create a CNAME file with a custom domain *(empty = do not create)* |
| MAX_COMMITS      | 100            | maximum number of commits to show (0 = all)                        |
| MAX_COMMIT_MSG   | 100            | maximum characters in a commit message to display *(0 = all)*      |
| MAX_COMMIT_LINES | 999            | maximum number of lines to show in a commit *(0 = all)*            |
| REPO_DIR         | $HOME/git      | directory containing repositories                                  |
| THEME            | light          | style used *(light or dark)*                                       |
| TITLE            | "Repositories" | title used on homepage                                             |
| WWW_DIR          | $HOME/www      | directory to output to                                             |

If the `CLONE_URL` was set to `https://github.com/acidvegas/` for example, then it will display as `git clone https://github.com/acidvegas/REPO_NAME.git` on all repository indexes, otherwise if you leave it as `remote` it will just parse the remote url *(`git config --get remote.origin.url`)* for that repository. For those using the `remote` option, remote urls from Github/Gitlab that use SSH will be converted to an HTTPS url. This applies to Github/Gitlab remote urls only, so if you cloned your repositories with SSH, then people may not be able to clone your repositories!

The `CNAME` option is optional if you are planning on using a custom domain with Github pages. See [here](https://help.github.com/en/articles/troubleshooting-custom-domains#github-repository-setup-errors) for more information.

Lastly, stagit will ignore the `$REPO_DIR/mirrors` directory by default. To make stagit include this directory, remove `-path $REPO_DIR/mirrors -prune` from the `find` command in the source.

## Todo
- mailto links in commits and more
- Create an index per-user to view specific users repos & key information.
- Pagination support for repos exceeding `MAX_COMMITS`.
- Add a footer to all pages with the last updated datetime and a link to this repository.
- Hook git pushes to rebuild the repositories index.
- Add support for displaying LICENSE/README files and convert markdown to HTML.
- Add support to view file contents.
- Fix all possible bashisms identified in source by checkbashisms.

## Mirrors
- [acid.vegas](https://acid.vegas/stagit) *(main)*
- [GitHub](https://github.com/acidvegas/stagit)
- [GitLab](https://gitlab.com/acidvegas/stagit)