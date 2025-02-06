flaws in applications are consistently #1 attack vector for breaches
80% stolen credentials
lack of knowledge
takes 6 months to fix

stolen credentials - # 1 breach pattern
application vulnerabilities - # 3 breach pattern


security action
- integrated
- focused and actionable
- automated


before shipping, do security audit
- have security tools once you commit and after PR


pr
- secrets management
- SAST
- SCA

ci testing
- DS

cd testing
- policies

qa integration testing
- auto
  - secret scanning
- policies





github advanced security
- supply chain
- GHE license
  - dependency graph
- GHAS license
- secret scanning
- code scanning



dependency graph
- summary of manifest and lock files
- dependices
  - direct
  - trandue dependency


github advisory db
- secruity advisories reported on github
- package managers report vulnerabilities from differet db

manage your env
- a dependabot alert is generated when vulnerability or malware is detected in a repo on the default branch
- dependabot version updates - enabled through dependabot.yml

publishing vulnerability
- security.md
- security advisories
  - don't report to world. 

secret scanning
- credentials or tokens we are using
- partnered with 60+ products - know the pattern of the token
- custom pattern
- push protection


code scanning
- static analysis CodeQuery language
- parasoft/sonarqube
- autofix ai


security overview dashboard
- overview
- coverage
- risk
- shows how many repos are activated