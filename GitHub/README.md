# GITHUB

# How configure SSH Key
1. Open terminal
2. Paste the code below, changing the address e-mail for your GitHub.

`$ ssh-keygen -t ed25519 -C "your_email@example.com"`

# How to push project and working in this
1. Open which project your is worked
2. Click in `code` and click in `copy``
3. In your terminal, paste the project
`$ git clone git@github.com:rhavistech/DevOpsTeams.git`
4. Rigth now is very important you create a new branch
`$ git branch -m "name_of_branch"`
5. Could you please to test if created of new branch
`$ git branch`
6. When you to finish the project, could you to use git add, commit and push, how? Let's go.
`$ git status` to see you all files changed
`$ git add .` to add all files
`$ git commit -m 'write about your project'` to add commit about your project
`$ git push origin 'the name your branch here'`
