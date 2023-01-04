# Using GitHub Issues for Help Requests 

Throughout Tier 3, we’ll use the Issues workflow on GitHub to manage Help Requests. 


## Set-up 
You'll use GitHub Issues on your `cohort-syllabus` repo.

You need to set up an Issue Template for GitHub by adding certain folders and files to your `cohort-syllabus` repo.

You need the following folders/files:

```js
[]- .github (folder)
    |
    []- ISSUE_TEMPLATE (folder)
        |
        - tier-3-support.md

```

COPY the `/.github/ISSUE_TEMPLATE/tier-3-support.md` file FROM THIS VERY REPO!

With this in place, any new Issue created on this Repo will pre-fill the GitHub UI with those questions.

### You need to teach your students to use it!

- Add an example issue post on your cohort-syllabus GitHub Repo
- Show students how to use it and be clear on what you are expecting

Good student example: https://github.com/PrimeAcademy/gemini-syllabus/issues/7

---

## Slack and GitHub Integration
To better monitor requests across instructors, set up Slack to get notifications of when issues are opened, what their details are, and when they are closed:

**In your Slack cohort-instructors channel**

- Give Github persmissions to slack > Go to [Github App Settings](https://github.com/organizations/PrimeAcademy/settings/installations), select _Slack_, add your syllabus repo to the list.
- Invite @GitHub >  `/invite @GitHub `to the channel you want to receive notifications
- Subscribe > `/GitHub subscribe REPO_URL` need to have the url. No trailing `/`
- It may have you connect your GITHUB and SLACK, follow prompts
- It may have you enter a code
- The Slack App must be added to the repo as well as an Integration  follow the slack prompts. 
