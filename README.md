# Discordeno Bot Template

This repo is meant as a template which you can use to create a Discord bot very easily using the [Discordeno library](https://github.com/discordeno/discordeno).

[Website/Guide:](https://discordeno.mod.land/)

[Discord Server](https://discord.com/invite/5vBgXk3UcZ)

## Pre-requisites

- [Deno](https://deno.land)

## Optional
- [Docker](https://docs.docker.com)
- [Docker Dompose](https://docs.docker.com/compose)
- [Denon hot reloading](https://deno.land/x/denon@2.4.7)

## Step By Step with Docker Compose


1. Clone the repository
2. Get your discord bot's token (not the application id or key) from your [Discord Developer console](https://discord.com/developers/applications).
3. Create an `.env` file in your project's root directory and add your bot's token with the command `echo TOKEN=123123123 > .env`
4. Install Docker Compose if you haven't already (check with `docker-compose -v`) [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
5. start your container with `docker-compose up -d` 

### How to use docker-compose
   - The flag `-d` runs the container in the background in "Detached mode". If you want to see the console output you can remove the flag or inspect your container using `docker-compose logs mybot`. 
   - The `--build` flag forces a build. If this is left out, and nothing is
   - You can also access your docker container's shell with the command `docker-compose exec mybot sh`  Use `ctrl - d` to quit the session, your container will still run.
   - Inspect your `docker-compose.yml` if you want. This file tells `docker-compose` to load your `.env` and where your `Dockerfile` is located. `docker-compose` uses that buildfile to get the latest version of `deno`, set up the environment, copy files from your local project folder, set permissions and finally start the bot in the docker container.
   - For more information, visit [https://docs.docker.com/compose/reference](https://docs.docker.com/compose/reference)


## Step By Step using Docker (without Docker Compose)
1. Clone the repository
2. Get your discord bot's token (not the application id or key) from your [Discord Developer console](https://discord.com/developers/applications).
3. Create an `.env` file in your root directory and add your bot's token with the command `echo TOKEN=123123123 > .env`
4. Build the container, from the root of your project with the command `docker build -t mybot .`
5. Run the container `docker run --env-file ./env -t mybot`

## Step By Step Without Docker

1. Create your own repo using the template button. It is next to the button where you get the url to clone. It will say `Use this template` This is a template repo.
2. Clone your own repo that Github created for you. `git clone url-here-for-your-repo`
3. Get your discord bot's token (not the application id or key) from your [Discord Developer console](https://discord.com/developers/applications).
4. Create an `.env` file in your root directory and add your bot's token with the command `echo TOKEN=123123123 > .env`
       Or add environment variables in any way you wish. As long as the deno process can access them via `Deno.env.get()`
5. Start the bot `deno run -A --quiet mod.ts`

**Note:** To run the bot with [PM2](https://github.com/Unitech/pm2): `pm2 start mod.ts --interpreter="deno" --interpreter-args="run -A --quiet -r" `

## How to set up hot reloading using denon
1. Install denon [https://deno.land/x/denon](https://deno.land/x/denon)
2. create an `script.js` file with `denon --init` and edit it to look like this:
```json
{
  "scripts": {
    "dev": {
      "cmd": "deno run -A mod.ts",
      "desc": "run my mod.ts file"
    }
  },
  "watcher": {
    "interval": 500,
    "exts": ["js", "jsx", "ts", "tsx", "json"],
    "match": ["**/*.*"],
    "skip": ["*/.git/*", "fileloader.ts", "*/db"],
    "legacy": false
  }
}
```
3. Start the denon server with `denon dev`
4. Enjoy hot reloading anytime you save a file. 🔥
   

## Add your bot to a discord server
1. Visit your discord developer console [https://discord.com/developers/applications](https://discord.com/developers/applications)
2. Click on your application, then `OAuth` in the menu
3. Click the `bot` checkbox for scopes.
4. Select the appropriate permissions. Admin is good for development. You can always change this later.
   Anyone clicking the link will be asked to invite your bot to their server(s) with the specified permissions. 
## Features

## Beginner Developers

Don't worry, a lot of developers start out coding their first projects as a Discord bot(I did 😉) and it is not so easy. With Discordeno, I tried to build it in a way that solved all the headaches I had when first starting out coding bots. If you are a beginner developer, please use this boilerplate.

**Modular commands, arguments, events, inhibitors, monitors, tasks.**

- Clean and powerful commands system
  - Powerful argument handling including validating, parsing and modifications.
  - Easily create custom arguments for your specific needs.
  - Command aliases.
  - Cooldowns and allowed uses before cooldown triggers.
  - Author and bot permission checks in server AND in channel!
- Clean and powerful events system
  - Simple functions that are called when an event occurs.
  - Easily reloadable!
  - No possible memory leaks due to incorrect EventEmitter usage!
  - Useful events available to help debug!
- Clean and powerful inhibitors system
  - Stops a command from running if a requirement fails.
  - Easily add custom inhibitors!
- Clean and powerful monitors system.
  - Runs a function on every message sent. Useful for stuff like auto-moderation or tags.
  - Easily ignore bots, users, edits, dms.
  - Powerful permission checks.
- Clean and powerful tasks system.
  - Runs a function at a certain interval. Useful for things like unmute and updating bot lists etc.
  - Can be used for cache sweeping to keep your cache optimized for exactly what you want.
  - Botlists code already made for most botlists. Just add your api tokens for each site and magic!
- Clean and powerful languages system.
  - Built in multi-lingual support.
  - Uses i18next, one of the best localization tools available.
  - Supports nested folders to keep cleaner translation files

**Hot Reloadable**

- Easily update your code without having to restart the bot everytime.

**Step By Step Guide**

- There is a step by step walkthrough to learn how to create Discord bots with Discordeno on our website! https://discordeno.mod.land/stepbystep
