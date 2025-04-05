******* SetUP Instructions *******

1. Choose an Uptime Monitoring Tool with GitHub Integration

Upptime: This tool is entirely powered by GitHub Actions, Issues, and Pages. It checks your website's uptime every 5 minutes (by default, but configurable), records response times, and if a site goes down, it automatically opens a GitHub Issue. 
It also generates a status website using GitHub Pages, displaying the live status and historical data.
OpenStatus: Another open-source synthetic monitoring platform that can monitor your websites and APIs globally. It also offers integration with GitHub Actions for running checks and can update status based on the outcomes.

2. Setting up with Upptime (Recommended for direct GitHub integration
Create a new Repository :

Go to the Upptime repository on GitHub: https://github.com/upptime/upptime.
Click on the "Use this template" button and select "Create a new repository".
Give your repository a name (e.g., status).
Important: Make sure to check the box "Include all branches" when creating the repository from the template.
Click "Create repository from template".

Enable GitHub Pages:
In your new repository, go to "Settings".
On the left sidebar, click on "Pages".
Under "Source", select "Deploy from a branch".
In the "Branch" dropdown, choose gh-pages and for the "(root)" directory.
Click "Save". This will make your status website accessible via https://<your-github-username>.github.io/<your-repository-name>/.
Add Repository Secrets: Upptime requires a personal access token (PAT) from GitHub to make commits and manage issues.

Go to your GitHub "Settings" -> "Developer settings" -> "Personal access tokens" -> "Fine-grained tokens".
Click "Generate new token".
Give the token a descriptive name (e.g., "Upptime Token").
Set the "Expiration" as per your preference (e.g., 90 days or longer).
Under "Repository access", choose "Only select repositories" and select the Upptime repository you just created.
In the "Permissions" section, under "Repository permissions", grant read and write access to:
Actions
Contents
Issues
Workflows
Click "Generate token".
Copy the generated token.
In your Upptime repository, go to "Settings" -> "Secrets and variables" -> "Actions".
Click "New repository secret".
Set the "Name" as GH_PAT.
Paste the token you copied into the "Value" field.
Click "Add secret".
Configure Upptime:

Edit the .upptimerc.yml file in your repository. This file controls the behavior of Upptime.

owner and repo: Ensure these are set to your GitHub username and your repository name, respectively.

sites: This is where you list the URLs of your websites hosted on CloudFlair that you want to monitor. For example:

YAML

sites:
  - name: Personal Website
    url: https://yourpersonalwebsite.com
  - name: Hashnode Blog
    url: https://yourhashnodeblog.com
  - name: Open Source Project
    url: https://youropensourceproject.org
You can also configure other settings like notifications (Slack, Telegram, etc.), response time thresholds, and more in this file. Refer to the Upptime documentation for detailed configuration options.

View GitHub Actions Workflows:

After configuring .upptimerc.yml, Upptime will automatically run GitHub Actions workflows.
Go to the "Actions" tab in your repository to see the status of these workflows. The uptime-check workflow will run periodically to check your websites.
Check Status and Issues:

If any of your websites go down, Upptime will automatically create a new Issue in your repository, detailing the downtime.
The README.md file in your repository will be updated with the current status of your websites.
Your status website (on GitHub Pages) will also reflect the live status and historical data.
