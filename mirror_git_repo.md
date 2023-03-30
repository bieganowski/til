## Mirror git repository

In order to move the git repository's content to another existing repository,
preserving history:

#### method 1
```bash
cd repo2
git checkout master
git remote add r1remote **url-of-repo1**
git fetch r1remote
git merge r1remote/master --allow-unrelated-histories
git remote rm r1remote
```

#### method 2
```bash
cd original-repository
git push --mirror https://gitsite.com/yourusername/new-repository.git
```

> Note: the above command will push **all** of your local Git code into the new repository.