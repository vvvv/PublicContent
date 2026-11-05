# PublicContent

Content that vvvv loads from this repository: news, library and NuGet listings, help browser content and package
constraints.

## Line endings

Line endings are handled by git through `.gitattributes`, for everyone and independent of personal settings like
`core.autocrlf`: text files are stored with LF, checked out with the platform's native line ending (CRLF on Windows,
LF on Linux/macOS), and normalized again on commit. You (and coding agents) don't need to care about line endings in
editors; diffs never show line ending changes.

Run once per clone, so that `git blame` skips the commit that normalized all files (GitHub does this automatically):

```
git config blame.ignoreRevsFile .git-blame-ignore-revs
```

Before merging or rebasing a branch that was started before the normalization (November 2026), enable renormalizing
merges, otherwise every file the branch touched conflicts over line endings:

```
git config --global merge.renormalize true
```

(or per merge: `git merge -X renormalize <branch>`)
