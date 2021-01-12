<h2 align="center">
    <img alt="Logo" src="https://github.com/Kraymer/brack/raw/master/docs/logo.png" width=400></img><br>
    BRACK: The Relentless Git Branch Name Acknowledger
</h2>


<p align="center">
<a href="https://github.com/kraymer/brack/blob/master/LICENSE"><img alt="License: MIT" src="https://github.com/kraymer/brack/raw/master/docs/license.svg"></a>
<a href="https://ko-fi.com/kraymer"><img alt="Donate" src="https://img.shields.io/badge/-%E2%99%A1%20Donate%20-ff69b4"></img></a>
</p>

> **/bɹək/** :
>
> 1.  *n.* efficient tracking dog of the foxhound family. Friendly and not very intelligent.
> 2.  *n.* git pre-commit hook to enforce a branch naming policy across your project. Portmanteau word for **Br**anch **Ack**nowledger. 

`brack` is a plugin for [pre-commit](https://github.com/pre-commit/pre-commit) that rejects commits when branch name does not validate a predefined format.


### Installation

Copy `pre_commit_hooks/brack` to your `.git/hooks/` folder and rename it as `pre-commit`.

Or if you use [pre-commit](https://github.com/pre-commit/pre-commit) framework, add this to your `.pre-commit-config.yaml` :

```yaml
-   repo: https://github.com/kraymer/brack
    rev: main
    hooks:
    -   id: brack  

```

### Configuration

By default branch name must match the regex `"^(feature|bugfix|improvement|library|prerelease|release|hotfix)\/[a-z0-9._-]+$"`.

If you prefer to use a custom regex, edit your `.pre-commit-config.yaml` to give it as argument to the script :

~~~
    -   id: brack
        args: [-r, "<YOUR_REGEX>"]
~~~

Beware that regex must be compliant with [POSIX Basic Regular Syntax](https://en.wikipedia.org/wiki/Regular_expression#POSIX).

### Alternative

[no_commit_to_branch](https://github.com/pre-commit/pre-commit-hooks/blob/master/pre_commit_hooks/no_commit_to_branch.py) is a hook provided with pre-commit that accomplishes the same thing but the logic is reversed : you define a regex that matches the branches you want NOT authorize commit to.  
Depending on your usage, picking one or the other might facilitate maintenance of the regex.
