CircleCI
===

# Debug SOP

This article is about a collection of self-learned experiences to modify / debug circleci. 

0. Error occured
1. Checkout new branch
2. Mofify .circleci/config.yml: disable outside effects like update / deploy.
3. Comment passed codes of ci config to accerlate mofify-and-test cycle. Focus on the error.
4-1. If has solution to the error: modify config, and rerun.
4-2. If has no solution: run ci in debug mode and ssh into the ci instance. Run the error command.
5. Test driven like debug: redo the modify-test-run step.
6. Complete run: Uncomment commented code. Check the code with outside effects in case an incorrect code is deployed.
7. Merge to master and retest.

# Best practice

Commands and Scripts

Should be as short as possible.
Should be verbose.

Environment Variables

Scope of vars should be as small as possible. Know a variable is consumed by which command in which line.
