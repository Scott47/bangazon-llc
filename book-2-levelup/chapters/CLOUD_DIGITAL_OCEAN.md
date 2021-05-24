# Digital Ocean Deploy

> 🧨 Make sure you deploy your Rare React client first, because you will need to get the domain name that Digital Ocean creates for your application in this chapter.

First, if you haven't used Digital Ocean yet, [sign up for $100 credit](https://m.do.co/c/47e5e578d1cd) which is good for 60 days. Deploying your first three static sites is cost free, and deploying a small Django app is only $5.00 per month, so you get two months of having a deployed API on credit.

Your React app is considered a static app, so you won't be charged for it, unless you go over your 3 free static deployed apps.

## Deploy API

1. Fork your team's Rare API project repository to your own account.
1. Add a file in the project directory named `digitalocean.yml` and place the following content in it.

    ```yml
    envs:
    - key: DISABLE_COLLECTSTATIC
      scope: RUN_AND_BUILD_TIME
      value: "1"
    name: rare-api
    region: nyc
    services:
    - build_command: ./seed_data.sh
      environment_slug: python
      github:
        branch: master
        deploy_on_push: true
        repo: your_github_account/repository_name
      http_port: 8080
      instance_count: 1
      instance_size_slug: basic-xxs
      name: rare-api
      routes:
      - path: /
      run_command: gunicorn --worker-tmp-dir /dev/shm rare.wsgi
      source_dir: /
    ```
1. Change the `repo` line to the correct values for your forked repository.
1. If your team did not use a bash script to handle migrations and installing fixture data, create a file in your project directory named `./seed_data.sh`. Then place the following content in it.
    ```sh
    #!/bin/bash

    rm -rf rareapi/migrations
    rm db.sqlite3
    python manage.py makemigrations rareapi
    python manage.py migrate
    ```
1. Open your `settings.py` file and add the domain name to the list of allowed CORS_ORIGIN_WHITELIST. For example, it will look something like this.
    ```py
    CORS_ORIGIN_WHITELIST = (
        'http://localhost:3000',
        'https://levelup-steve-pu92u.ondigitalocean.app',
    )
    ```