## Test Details
-  There are two branches "main" and "master". 
- I have kept different versions in both so that we can confirm the update branch is being rebased onto new base branch. 
 
- With Renovate's current logic when I update the baseBranch from "main" to "master" in renovate-config, 
   the PR is marked edited as shown in https://github.com/RahulGautamSingh-testing/repro-21206

- With new logic the PR should be rebase onto "master" shown here: https://github.com/RahulGautamSingh-testing/fix-21206/pull/1

## Debug Log

```log
DEBUG: syncBranchState() 
DEBUG: syncBranchState(): update baseBranch name 
DEBUG: syncBranchState(): update baseBranchSha 
DEBUG: branch.isUpToDate(): needs recalculation  // new changes invalidate branch fingerprint when base branch changes
...
DEBUG: Checking if PR has been edited 
DEBUG: branch.isModified(): using git to calculate 
DEBUG: branch.isModified() = false 
DEBUG: Found existing branch PR 
...
DEBUG: Base branch changed by user, rebasing the branch onto new base // rebasing onto new base
DEBUG: Using reuseExistingBranch: false        
DEBUG: Setting current branch to master        
DEBUG: latest commit 
       "branchName": "master",
       "latestCommitDate": "2023-04-28T04:50:21+05:30"
DEBUG: manager.getUpdatedPackageFiles() reuseExistingBranch=false 
DEBUG: Starting search at index 0 (repository=RahulGautamSingh-testing/fix-21206, baseBranch=master, packageFile=.nvmrc, branch=renovate/node-18.x)
       "depName": "node"
DEBUG: Found match at index 0 (repository=RahulGautamSingh-testing/fix-21206, baseBranch=master, packageFile=.nvmrc, branch=renovate/node-18.x)
       "depName": "node"
DEBUG: Contents updated (repository=RahulGautamSingh-testing/fix-21206, baseBranch=master, packageFile=.nvmrc, branch=renovate/node-18.x)   
       "depName": "node"
DEBUG: Updated 1 package files 
DEBUG: No updated lock files in branch         
DEBUG: isBranchConflicted(master, renovate/node-18.x) 
DEBUG: branch.isConflicted(): using git to calculate 
DEBUG: Setting git author name: Renovate Bot 
DEBUG: Setting git author email: renovate@whitesourcesoftware.com 
DEBUG: branch.isConflicted(): true 
DEBUG: 1 file(s) to commit 
DEBUG: Preparing files for committing to branch renovate/node-18.x 
DEBUG: git commit 
       "deletedFiles": [],
       "ignoredFiles": [],
       "result": {
         "author": null,
         "branch": "renovate/node-18.x",
         "commit": "3881970571f0907ed7d7c251a2f199e655f610d0",
         "root": false,
         "summary": {"changes": 1, "insertions": 1, "deletions": 1}
       }
DEBUG: Pushing refSpec renovate/node-18.x:renovate/node-18.x 
DEBUG: git push 
       "result": {
         "pushed": [],
         "ref": {"local": "refs/remotes/origin/renovate/node-18.x"},
         "remoteMessages": {"all": []}
       }
DEBUG: Setting current branch to master 
DEBUG: latest commit 
       "branchName": "master",
       "latestCommitDate": "2023-04-28T04:50:21+05:30"
 INFO: Branch updated 
       "commitSha": "3881970571f0907ed7d7c251a2f199e655f610d0"
DEBUG: Ensuring PR 
```
