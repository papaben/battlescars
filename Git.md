# Commit messages

> Commit messages are our chance to leave nuggets of wisdom for our future selves. 
> To provide the most value, they should be easy to read and consistently formatted
> across a project.

## The Goal of a Commit Message

To provide an elucidating summary that is searchable

## The commit messages's friend
Bear in mind that as wonderful as a commit message may be, it is only useful if the reader 
knows to look at the commit message. In light of that, a far more useful location for insights 
is the code itself in the form of comments. 

Side-note: The structure of a well-formed code comment is the subject of an entire other page! =)

## Jargon

| Term | Meaning |
| --- | --- |
| `Subject` | The first line of a commit message | 
| `Body` | All text of the commit message other than the first line | 


## Recommendations

### Content

1. Capture the most critical characteristic of the change in the Subject
1. Use the body to add any details to communicate what the author might say to a project contributor when asked to describe why the commit was made or what critical detail influenced the change
1. Do not use the Body to rehash what can be easily observed from the code diff
1. Include the Ticket Tracking Issue ID (e.g. Jira, Asana) and any links to external docs
    1. It's also sometimes a good idea to put these links directly in code comments
1. Leave out the Body when it would be redundant

### Format

1. Limit the Subject line to 65 characters
1. Wrap the Body at 72 characters (similar to PEP8 on comments)
1. Blank line between Subject and Body
1. Capitalize the Subject line
1. Not end the Subject line with a period

### Keep in mind...

Sometimes the most important remarks to make may refer to what's been removed 
from the code, and not what's been added.


## Some Examples

### Example 1

In this example, the `Body` could provide more crumbs.

Original <------------
```
    We're on an outdated version of zenpy that requires us to 
    use epoch seconds
``` 

------------------> Improved 
```
                         Bugfix: old zenpy package expects epoch seconds

                         See documentation for our current version,
                         https://github.com/facetoe/zenpy/tree/0.0.22
```

### Example 2

In this example, the message could expand on changes external to code

Original <------------
```
Updates for bootstrapping the Elastic Search proxy

This commit introduces `devDependencies` when configuring nodejs
dependencies so that production servers won't be cluttered with
unused packages.
```

------------------> Improved 
```
                         Add npm dependencies for Elasticsearch proxy

                         The ES proxy is used only in dev, and this change takes advantage
                         of the npm `devDependencies` feature to prevent these packages
                         from being installed in prod. Here is a good explanation of the
                         relationship between the different types of node dependencies,
                         http://stackoverflow.com/questions/18875674/
```

## Attribution
Inspired by
 * http://chris.beams.io/posts/git-commit/
 * https://git-scm.com/book/ch5-2.html
 * http://stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting

# Working with Git logs

| Task | Command |
| --- | --- |
| Edit your commit message | `git commit --amend` |
| Add staged changes to last commit | `git commit --amend -C HEAD` |
| Show your last commit message | `git show -s` |
| Search commit logs for messages mentioning "columns" | `git log --grep=columns` |
| Search for messages mentioning an Asana task | `git log --grep="https://app.asana.com/0/144820974567760/149030287274142/f"`  |
| Search for changes in the *code* to `MyClass` | `git log -S"MyClass"` |
| Search for changes in code with a regex | `git log -G"/pattern/"` |


