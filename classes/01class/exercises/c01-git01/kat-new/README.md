# c01-git01

## Commands executed

1. Commands typed to solve the "Merging" exercise
``` 
git checkout -b bugFix
git commit
git checkout main
git commit
git merge bugFix

```

2. Commands typed to solve the "Rebasing" exercise
```
git checkout -b bugFix
git commit
git checkout main
git commit
git checkout bugFix
git rebase main

```

3. Commands typed to solve the "Revert and reset" exercise
```
git reset HEAD~1
git checkout pushed
git revert HEAD

```


<!-- Don't change anything below this point-->
<!-- Before commiting, remove both commented lines--> 
***
Answer for exercise [c01-git01](https://github.com/devopsacademyau/academy/blob/23cc1dfa31e85651e3cdc1b0ef38da21518841ba/classes/01class/exercises/c01-git01/README.md)