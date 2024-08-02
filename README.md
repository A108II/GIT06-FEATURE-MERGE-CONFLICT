### Merge conflicts in feature branch workflow
- If two developers, Developer1 and Developer2, are working on different features, they will create branches called feature1 and feature2, respectively. If they change the same file and the same line, a conflict will occur. Developer1 creates a pull request, which gets reviewed and merged into the master branch. When Developer2 tries to merge their feature branch into the master branch, a merge conflict will arise due to the changes on the same file and line.
- Now, to simulate this, we will create feature1 branch feature2 branch.
Create a new branch with `git branch feature1`, check the log with `git log --all —graph`.
- Since we're working on master and we need to switch to the `feature1` branch that we just created with this command: `git checkout feature1`.
- Go to `feature1` file and create a file named `special-feature.js`.
- Now pick the changes with `git add .`, and create a new commit with `git commit -m "feature1"`.
- Now we need to switch back to master and then create a new branch, first switch to master with `git checkout master` and then create a new branch with `git branch feature2`, and then we need to switch to `feature2` branch with `git checkout feature2`. 
- Next, we need to change the same file and the same line, create a file named `special-feature.js`.
- Pick up the changes with `git add .`, and create a new commit with `git commit -m “feature2"`.
- Now since we're in the `feature2` branch, we first want to push master to Github, we use this command: `git push origin master`.
- Next, we need to switch to the `feature1` branch with `git checkout feature1`, check the log with `git log --all --graph`, HEAD must point to the `feature1` branch. Then we need to push this branch to github with `git push origin feature1`.
- Then, we need to switch to the `feature2` branch with `git checkout feature2`, check the log with `git log --all --graph`, HEAD must point to the `feature2` branch. Then we need to push this branch to github with `git push origin feature2`.
- Now go to github and click on `pull requests` tab, click on `New pull request`. choose `base:master` and `compare:feature1` This is gonna request `feature1` to merge into master, and then click on `Create pull request`
- Let's create another pull request for feature2 click on `Code` then click `pull requests` tab, click on `New pull request`. 
- Choose `base:master` and `compare:feature2` This is gonna request `feature2` to merge into master, and then click on `Create pull request`.
- In `Pull requests` Now we have two branches that want to be merged into the master branch. If the review for `feature1` finishes early, then we want to merge this into the master branch. For this click on `feature1` and then `Merge pull request` and then `Confirm merge`.
- Click on `Pull requests`, and then `feature2`, we will see this message: `This branch has conflicts that must be resolved`. This is because we merged the branch that has changed the same file and same line of the code, now a new branch want to change the same thing. To resolve this click `Resolve conflicts` and then remove the part you don't want to be in the merge and then click on `Mark as resolved`, and then `Commit merge`. Then click on `Merge pull request` and `Confirm merge`, this will merge the branch which we picked in the editor into the master branch. 


### Resolve merge conflicts on the computer
- The scenario is gonna be like this: 
1. We're gonna set up the same scenario as we had before, `git checkout master`, `git pull origin master`, this ensures that we have the latest version of the github repository on our local device.
2. Create 2 branches that modify same line, same file. 
3. Push to github & create pull requests, we're gonna name those branches `feature3` and `feature4`. 
- For doing this, first check where the HEAD points to with `git log --all --graph`. 
- Switch to master branch with `git checkout master`.
- `git fetch` to fetch those changes from github and see the changes with `git log --all --graph`. 
-  `git pull origin master` to apply the changes from github to master branch.
-  `git branch feature3` to create a branch.
- `git checkout feature3`.
- In a file named `feature.js`, add some content, pick the changes `git add .`, and commit the changes with `git commit -m “add feature-3"`. 
- Now switch back to master branch with `git checkout master`.
- Create a new branch alled `feature4` with `git branch feature4`.
- In a file named `feature.js`, add some content, pick the changes `git add .`, and commit the changes with `git commit -m “add feature-4"`. 
- Since we're in the `feature4` branch, we push the branch to github by `git push origin feature4`.
- Next, switch to feature3 with `git checkout feature3` and then push it to github with `git push origin feature3`. 
- On github click on `New pull request`. 
- Choose `base:master`, `compare:feature3` and click on `Create pull request`, and then `Merge pull request`. Do the same for `feature4`.
- This will create a conflict on branch `feature4`, click `Pull requests` and click `feature-4` to see it.
- Without using the web editor, this time we want to do this in the local branch. from previous examples we can see that to resolve the merge conflict we need to merge `master` into `feature4`. 
- Because we merged the feature3 branch into the master branch in github, we need to pull those changes back to our local master branch. First we need to switch to master branch in our local machine, with `git checkout master`, then pull the changes back to the local master branch with `git fetch`, and then apply the new changes with `git pull origin master`.
- Then switch to `feature 4` branch with `git checkout feature4`. 
- Since we are in the `feature4` branch, we're gonna merge `master` into the `feature4` branch to resolve the conflict. In order to do this, first `git merge master`.
- We can see this message
```bash
CONFLICT (add/add): Merge conflict in feature.js
Automatic merge failed; fix conflicts and then commit the result.
```

- To resolve the conflict we need to pick the changes with `git add .` and commit with `git commit -m "Merge conflict(v2) resolved"`.
- Now we merge `master` into `feature4`, and we need to push it back to github with `git push origin feature4`.
- Go to github and see the result in the `Pull requests`.
