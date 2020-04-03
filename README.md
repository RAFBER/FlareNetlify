# Flare Netlify

Deploy a webhelp built with MadCap Flare to Netlify.

Preview the output of this repo at https://flare-netlify.netlify.com.

## Why Netlify?

- A generous free hosting tier.
- You don't have to think about server configuration and maintenance.
- All the benefits of their global CDN, designed for performance and scale.
- Automatic deploy previews on pull requests. This means you (and reviewers) can view a preview of the site before merging and deploying your changes.
- Super-simple [redirects](https://docs.netlify.com/routing/redirects/#syntax-for-the-redirects-file).

## Prerequisites

1. An existing Flare project with an HTML5 target that you want to deploy. We won't walk through creating and editing a project here.
2. Your Flare project should be under git version control and stored in GitHub, GitLab or Bitbucket. The following instructions assume you are using the cloud versions. If you are using self-hosted version control, it should still be possible to set up a Netlify integration, but there'll be a few more steps. Talk to your devops team.

## Steps

1. In your Flare project, create a folder to store the built output. In the example project in this repo, it's called `_site`.
2. Log in to [Netlify](https://www.netlify.com/) and go through the steps to create a new site from git. There's a video [here](https://docs.netlify.com/site-deploys/create-deploys/#deploy-with-git) in the Netlify docs. Unfortunately the material is only available as video, but it's less than two minutes and has closed captions. Make sure to set the **Publish directory** to the name of the directory you created in step one.
3. In your Flare project, modify the HTML5 target so that the **Output File** is `index.htm`.
4. Build the HTML5 target.
5. Copy the files from `Output` to `_site`. If you're going to do this often, you should automate this step with a post-build script. [Flare's help](https://help.madcapsoftware.com/flare2017r3/Content/Flare/Targets/More/Creating-Pre-Post-Build-Events.htm) has more info.
6. Push the changes to your remote repo, including the contents of `_site`. If you push directly to master, Netlify will automatically start a build. If you are working on a branch, submit a pull request. Netlify will create a preview build and add a link to the pull request.

By default, Netlify serves the site at a randomly generated URL so you can view it immediately. For information on adding your own custom domain, refer to the [Netlify documentation](https://docs.netlify.com/domains-https/custom-domains/#definitions).