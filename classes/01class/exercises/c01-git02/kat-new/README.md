# c01-git02

## Answers

1. Is it possible to see the inner commit of squashed commit with `git rebase`?
```
Using `git reflog` will list all the historical changes made. Checkout the commit required and branch out from there.

```

2. How to compare two different local branches using `git diff`? 
How about remote ones, can you do the same?
```
Use `git diff <branch> <branch>` to compare different branches, likewise you can compare remote branches by providing the remote path:- `git diff <local branch> <remote>/<remote branch>`

```

<!-- Don't change anything below this point-->
<!-- Before commiting, remove both commented lines--> 
***
Answer for exercise [c01-git02](https://github.com/devopsacademyau/academy/blob/5e1ec235517f206c8d4a11a37388fcfd0220d194/classes/01class/exercises/c01-git02/README.md)