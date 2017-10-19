---
explains: How to suggest changes and how to review them
---

# Pull requests

Pull requests (as they are named on GitHub) or Merge requests (as they are named on GitLab) are proposed changes to a codebase. They are submitted by a contributor to a project and accepted or rejected by a repository's maintainers. Pull requests each have their own discussion forum enabling a collaborative review of the committed code. 

For a basic guide on how PRs work read GitHub's excelent guide [Using pull requests](https://help.github.com/articles/using-pull-requests/.)

## What needs to be reviewed with a PR

The goal of a PR is to discuss proposed changes to the code and check whether it is good enough to merge.

These are some main points to review code on:

- Style: identify discrepancies from the style that is mentioned in the projects readme or in our general style guides.
- Potential Bugs: try to think about what might break.
- Error Handling: if something external can cause an exception, how will the user experience it?
- Efficiency: will things scale and still be responsive?
- Readability: can you understand what's going on?
- Requirements: does the commit fulfill the requirements of the ticket or issue?
- Does-what-it-says-on-the-tin: run the code, does it do weird things like downloading (random kung-fu gifs) from the internet?
- Tested: are there a minumal amount of health checks?
- Healthy: Are common security mistakes checked?
- Maintainable: could you maintain and bugfix the code you see?

## Looks Good To Merge (LGTM)

If the code looks good to merge to you you can let your collaborators know by mentioning `LGTM` in the Pull Request so that other contributors see that it has your sign of approval.