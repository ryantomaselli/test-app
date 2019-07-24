# Git workflow

- Check out local master
- `git fetch` will give us access to changes on the origin
- `git reset --hard` will reset local master to kmatch origin master
- `git checkout -b feature-branch-name` will give us a new branch based on master
- Make whatever changes the feature required
- Check in the feature branch with `git add <files that changed>`
- Commit changes - `git commit -m'some good commit message'`
- Push feature branch to origin - `git push origin`
- Create pull request for our feature on origin
- Before we merge our pull request, lets make sure master has not been updated by someone else or us
- `git checkout master`
- `git fetch origin`
- If origin master has changed, point our local master to the same commit
-`git reset --hard origin/master`
- Update our feature branch with the changes to master
- `git checkout <feature-branch-name>`
- Rebase master to our branch
- `git rebase master`
- If the rebase can't be applied cleanly, make the correct edits
- `git add <file name>
- `git rebase --continue` until the rebase is applied
- Push the updated feature branch + master changes
- `git push origin`
- Merge the pull request as it will now have no conflicts with the master branch

# Deployments

- Master should always be deployable and deployed
- Dont merge to master unless it is ready for prod, do your testing before this step
- Deploy a pull request to a staging server and test there first
- If you want to group several pull requets together for deployment, test each individually on staging;
- Then create a branch and merge each of the pull requests into that integration branch and deploy it to staging
- Do your testing
- If everything is happy, merge the pull requests to master, deploy
- By testing each one seperately if there is a failure you can easily roll back and you know what PR fucked it up.
- If you try to jam a bunch of stuff through the pipeline and it breaks, rolling back is harder and yu have to dig to find out which moving part (pr) broke.
