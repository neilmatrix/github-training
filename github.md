github platform
- copilot
- collaboration
  - pr, projects, issues, discussion, marge queue, search
- develop
  - ci/cd, automation, copilot, codespaces, runners, npm, mobile
- security
- scale

use cases across your SDLC
plan - triage issues, project boards
code - code review, auto merge, auto labelling
build - compile and build, store artifacts
test - unit/integration test, linters, codeQL, consume packages
release - publish release, release notes, upload artifacts
deploy - deploy app
monitor - not suitable


- jfrog stores the artifacts when you build the packages
- it could be a docker container also


plan - projects, issues
build - codespaces, repo, packages,
continous - secret scanning, 
integration - insight, OSS scanning, scanning
deploy - actions, mobile
operate - apps


github enterprise available in 2 flavours
- cloud - SaaS, OSS, private with EMU(Enterprise managed users)
- server - ha capable, private, self hosted


heirarchy
- organisations(different verticals) => repositories



## collaboration features
- issues, pr, discussions, notifications, wikis
- start with an issue
  - track requirements, track action items
- link issues with pr
=> we can track these issues in project boards
=> at pr we can add lot of automations. e.g. - number of reviewers, ci/cd etc
- code governance - repository rules(messaging formats, etc), repository properties. e.g. - protect branches
- dicusssions - discuss ideas, q&a
issues vs discussions vs pr

- prs => directly linked to code changes



wikis and pages
wikis
- can host documentations
- simple markdown
pages
- static hosting services

## productivity features
- actions, copilot, codespaces, mobile
- actions => create artifacts
  - yaml files
  - secrets and environment variable store
  - live logs and visualised workflow execution
  - respond to github events
- ci workflow - create artifact, do checks
- cd workflow - deploy to cloud, kubernetes services etc. pull artifacts from artifactory storage, check artifacts, etc. 
  - separate test pipeline, load testing (using jMeter), etc.

automated delivery
- automating workflows from code to cloud
- approval incorporated in actions itself


github actions marketplace

github copilot
- ai assitant
- grab the context
- proxy sitting between your prompt and llm (removes privacy related code)
- takes inpsiration from public repositories
- inline suggestions
- copilot chat (chagGPT experience)
- document generation
- comments to code
- tests
- generate ideas
- initial skeleton
- generate UML diagrams
- series of actions
- code refactoring
- code explanation


codespaces
- dev environment in the browser
- open a virutal env, with vscode as IDE

github advanced security (GAS)
- alternatives - parasoft
- secret scanning - connections string, api token, env variable
  - potential credential leaks in source code
- code scanning - static analysis using codeQL
  - CID/CD SARIF output
  - repo ruleset
  - code standards
- supply chain
  - dependency graph
  - dependecy insights
  - software bill of materials
  - looks at package.json files etc => understand vulnerabilities of packages


security overview dashboard
- overview
- coverage
- risk
- code scanning results
- secret scanning results


other features
- github packages - inbuilt package manager like maven, npm, gradle, docker, nuget, etc
- github mobile - available as app
- github cli
- github rest apis
- scalability
  - SaaS


## demo
if certain github apps are installed, you can add them while creation of your repo like docker, azure, etc

- under enterprise, you can create multiple organistions.
- inside organisations you have multiple repos
- inform someone with @ in discussion. it is a markdown format.
- we have projects at organisations and repo levels
- at organisations level we have packages. these are stored in jfrog artifacts.
- create team for organisation. add users. (not available for free account)
- at repo level
  - read, write, triage, maintain, admin roles
- add security data, pull request managers etc at repo levels
- we also have people's section. understanding in a nutshell what roles and access to repos individuals have.



### repo level
- code
  - metadata
  - commit history
  - branches
  - tags(tags available at repo level)
  - licensing policeis
  - custom properties
  - releases (upload via rest apis)
  - packages (publish package to github packages)
  - clone repo
    - https
    - ssh
    - github cli
    - download zip
- issues
  - track your work
  - feature, bugs, etc
  - assign to developers
  - 2 options
    - labels
    - milestones
      - track issues and pr based on deadline dates
  - under each issue, you can create sub-issue
- pr
- actions
- projects
  - you can filter out issues based on iterations
  - 
- wiki
  - high quality information about your project
- security
- discussions
  - annoucements
  -  general
  -  ideas
  -  polls
  -  q&a
  -  show and tell
- insights
  - collaborators and their collaborations
  - traffic
  - commits
  - code frequency
- settings





## what is version control
- centralised vs distributed
  - no branching

git
- snapshots, not deltas
- a git commit is a node in a graph
- every commit has a pointer ot its parent
- references makes commits reachable
- head, tag, branch

3 different settings git config
- system - all users, all repos
- global - all repo of current users
- local - specific directory
`git config --global user.name "firstname"`
`git config --global user.email "user@email"`

viewing your configurations
`git config --list`
`git config --global --list`

extract specific property of config
`git config --get user.name`



git restore
- used to discard changes in the working directory
- can also unstage files from the staging area
use cases
1. Undo local changes (before staging):
`git restore myfile.txt`
1. unstage a file
`git restore --staged myfile.txt`
1. Restore a file to its last committed version:
`git restore --source=HEAD myfile.txt`


git reset - move head
- moves head to an earlier commit
- different modes
  - `--soft` - Moves HEAD but keeps staged & working directory changes.
  - `--mixed (default)` - Moves HEAD, unstages changes but keeps them in working directory.
  - `--hard` - Moves HEAD, deletes everything (staged & working changes).
1. reset branch to previous commit
`git reset --soft HEAD~1`
1. reset branch and unstage changes
`git reset --mixed HEAD~1`
1. reset branch and delete all changes
`git reset --hard HEAD~1`


git rebase - rewriting history
- You want to rewrite history cleanly or move commits to another base.
- Unlike merging, which preserves the entire history of both branches, rebase rewrites history by placing your commits on top of another branch’s commits.
- Moves or combines commits onto another branch.
- Used to clean up commit history (linear history).
- Can be interactive `(git rebase -i)` to modify, squash, or reorder commits.
- modify last 3 commits
`git rebase -i HEAD~3`
```bash
git checkout feature-branch
git rebase main       # Now, to rebase your feature-branch onto the latest main, you would use:
```






git revert - undo a commit but keep history
- Creates a new commit that undoes a previous commit.
- unlike revert, it does not remove history
revert a specific commit
`git revert <commit-hash>`


git checkout
- create new branch
`git checkout -b feature-1`



git log
- commit history
- online summary per commit - `git log --oneline`


git status
- current state of working directory
- Displays unstaged, staged, and untracked files.
`git status`


git merge
- combining two merges into one
- fast forward merge - If the target branch hasn't diverged and there are no conflicting changes, Git just "moves" the target branch pointer forward
- three-way merge - If both branches have unique changes (i.e., they've diverged), Git will create a new merge commit to combine the changes.


```bash
git checkout target-branch
git merge source-branch
```




git fetch
- pull from github but don't add to working directory



git pull
- git fetch + git merge




origin
- In Git, origin is the default name given to the remote repository that you cloned from or the default remote for a local repository. It’s essentially a shorthand or alias for the full URL of the remote repository.
- view remote repos
`git remote -v`
- fetch all the changes from remote repo
`git fetch origin`
- push local main to origin main
`git push origin main`
- if remote repo is moved to some other url
`git remote set-url origin <new-url>`



git cherry-pick
- In Git, cherry-pick is a command used to apply a commit from one branch onto another branch. It allows you to pick a specific commit (or multiple commits) from one branch and apply them to another branch, without merging the entire branch.
- `git cherry-pick <commit-hash>`



code governance on github
- protected branch
  - settings => branches => branch protection rule
  - enter brnach name
  - check - require a pull request before merging
  - check - require number of approvals
  - check - require review from the code owners
  - check - require conversation resolution before merging


- settings => ruleset
  - restrict creation
  - restrict deletions
  - block force pushes
  - restrict commit metadata


- in organisation we have
  - team and
  - collaborators