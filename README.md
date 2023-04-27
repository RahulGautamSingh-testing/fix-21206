## Test Details
-  There are two branches "main" and "master". 
- I have kept different versions in both so that we can confirm the update branch is being rebased onto new base branch. 
 
- With Renovate's current logic when I update the baseBranch from "main" to "master" in renovate-config, 
   the PR is marked edited as shown in https://github.com/RahulGautamSingh-testing/repro-21206

- With new logic the PR should be rebase onto "master" shown here: https://github.com/RahulGautamSingh-testing/fix-21206/pull/1
