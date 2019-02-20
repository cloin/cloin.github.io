---
layout: post
title: Ansible from my phone
---

*A walkthrough of an experiment running Ansible Tower jobs from an iPhone*

I was looking for a neat way to demonstrate using the Tower API to run existing job templates and I thought that authenticating to Tower to start a job from my phone would be an interesting demo experience.

In order to do this from iOS, I needed to find an app that is capable of making the requests to Tower. I settled on [Workflow](https://itunes.apple.com/us/app/workflow/id915249334?mt=8) which is an iOS automation app picked up by Apple some time ago. It's free and is the only requirement on the iOS side.

On Tower, I first needed to get a signed SSL cert and swap out the default cert and key created at Tower installation. [Let's Encrypt](https://letsencrypt.org/) makes this a 3 minute endeavor. Once the certs are generated on the server, swap them in for `/etc/tower/tower.cert` and `/etc/tower/tower.key` on the Tower server. Make sure to keep the same names.

Making the API calls is simple.
* POST credentials to `https://tower.example.com/api/v1/authtoken/` using `username` and `password` in the request body
* Pull the token id from the response
* POST token id to `https://tower.example.com/api/v1/job_templates/<template id>/launch` where `Authentication: Token <token id>` is provided in the header

My Workflow redirects to another app to copy my Tower password from, but this step can be removed. 

Prompts for username, password and job template id. Responds with job template name, playbook, created time, and job id.

[Get the Workflow](https://workflow.is/workflows/3f25b544e6bb4a2aafa262708db7586e)
