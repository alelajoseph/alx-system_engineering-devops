**Postmortem**

![post-mortem-meetings](https://github.com/alelajoseph/alx-system_engineering-devops/assets/109358699/3b763a21-3962-4798-b36d-91fb6857fe5e)

**Issue Summary**

After releasing a new feature on our Ruby on Rails site, we received complaints from users unable to sign in or sign up, despite it working on our local machines. 127 emails flooded our inbox, highlighting the issue. Realizing the impact on user retention, we investigated further. Cloning the repository, we discovered the site failed to start due to outdated project requirements, causing a malfunction from 9:55 AM GMT+1 to 11:20 AM GMT+1.

**Timeline**

05-02-2022 9:55 AM GMT+1 - Initial user complaint about signing in.
05-02-2022 10:20 AM GMT+1 - Backend developer Winus faced the same issue.
05-02-2022 10:35 AM GMT+1 - Investigation into controllers and views for inconsistencies.
05-02-2022 10:40 AM GMT+1 - Focus on potential issues with the bcrypt gem, detecting errors in hash verification.
05-02-2022 10:42 AM GMT+1 - Checking view bindings, disproving field-model mismatches.
05-02-2022 10:45 AM GMT+1 - False assumption about controllers creating different hashes.
05-02-2022 10:50 AM GMT+1 - Suspected password hashing issue.
05-02-2022 11:00 AM GMT+1 - Escalation to backend development team.
05-02-2022 11:20 AM GMT+1 - Resolution by updating the bcrypt gem version for the backend server.

**Root Cause And Resolution**

An outdated bcrypt gem version caused errors with valid hashes. Winus manually updated the gem version in Gemfile.lock, ensuring compatibility and resolving the issue effectively.

**Corrective And Preventative Measures**

Implement continuous integration pipeline for pull requests to verify build success pre-merge.
Setup monitoring for databases and application servers.
Enforce testing for new features before merging into the deployment branch.
