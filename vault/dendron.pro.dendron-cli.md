---
id: 8b03ed06-4f46-46e0-8652-c6abf2266a79
title: Dendron-cli
desc: ''
updated: 1609784186517
created: 1599709645355
stub: false
---

# Dendron CLI 🚧

The Dendron CLI exposes Dendron's functionality via the command line. 

## Installation
```
npm install -g @dendronhq/dendron-cli
```

## Engine Commands

### doctor 🚧

Use doctor to perform specific fixes over your notes. 
- NOTE: the functionality here is different from what is available in the plugin version of [[Doctor|dendron.topic.commands#doctor]]. 

```bash
doctor helps you fix your notes

Options:
  --version     Show version number                                    [boolean]
  --help        Show help                                              [boolean]
  --wsRoot      location of workspace                                 [required]
  --enginePort  If set, connecto to running engine. If not set, create new
                instance of Dendron Engine
  --     what actions the doctor should take
                            [array] [choices: "h1ToTitle", "h1ToH2"]
  --query       run doctor over a query                                 [string]
  --limit       limit num changes                                       [number]
  --dryRun      dry run                                                [boolean]
```

#### available actions
- h1ToTitle: remove initial `h1` header and use it to replace contents of `title` field in frontmatter
- h1ToH2: convert all initial `h1` header to `h2` header

#### examples

- convert all `h1` tags to frontmatter `title` values for the `readings` hiearchy
```bash
dendron-cli doctor --wsRoot . --action h1ToTitle --limit 10 --query "readings.*" 
```

- see log
```bash
LOG_LEVEL=info LOG_DST=stdout dendron-cli doctor --wsRoot . --action h1ToTitle --limit 10 
```

### launchEngineServer

Launch the [[dendron server|dendron.roadmap.project.n.2020.server-migration]]. Useful for development purposes or to launch the server in a specified port

The CLI will also write out `.dendron.*` [[metadata files|dendron.ref.layout#file-tree]] in the workspace root just the same as the Dendron plugin. 

```
dendron-cli launchEngineServer --wsRoot ~/Dendron/ --vaults ~/Dendron/vault --port 3005
```

## Publishing Commands

### buildSite

Build dendron site. 

```
dendron-cli buildSite

build notes for publication

Options:
  --version      Show version number                                   [boolean]
  --help         Show help                                             [boolean]
  --wsRoot       location of workspace                                [required]
  --vault        location of vault                                    [required]
  --writeStubs   writeStubs                                      [default: true]
  --incremental  use rsync to only copy files that changed
                                                      [boolean] [default: false]
  --dryRun       don't actually build                 [boolean] [default: false]
```

- eg
```
dendron-cli buildSite --wsRoot . --vault ./vault 
```

### publishNotes

Publish a dendron site

```
dendron-cli publishNotes

Build, commit, and push your notes for publication

Options:
  --version         Show version number                                [boolean]
  --help            Show help                                          [boolean]
  --wsRoot          location of workspace                             [required]
  --vault           location of vault                                 [required]
  --writeStubs      writeStubs                                   [default: true]
  --incremental     use rsync to only copy files that changed
                                                      [boolean] [default: false]
  --dryRun          don't actually build              [boolean] [default: false]
  --noPush          don't push the result                              [boolean]
  --publishRepoDir  repo to publish from. default is same as `wsRoot`
```

- eg:
```
dendron-cli publishNotes  --wsRoot . --vault ./vault 
```

### BuildSiteV2

```bash
dendron-cli buildSiteV2

build notes for publication using 11ty

Options:
  --version     Show version number                                    [boolean]
  --help        Show help                                              [boolean]
  --wsRoot      location of workspace                                 [required]
  --enginePort  If set, connecto to running engine. If not set, create new
                instance of Dendron Engine
  --serve       serve over local http server          [boolean] [default: false]
  --stage       serve over local http server
                                       [choices: "dev", "prod"] [default: "dev"]
  --servePort   port to serve over                             [default: "8080"]
  --output      if set, override output from config.yml                 [string]
```

#### Connect to Open Workspace

Normally, this command will spawn a new Dendron Engine that indexes your notes before building them for publication. You can skip this initial indexing if you have a current Dendron workspace running. 

In that case, the CLI can connect to the current engine instead of starting a new one using the following command. 

```bash
cd {root/of/workspace}
# .dendron.port has the port of the current running workspace
npx dendron-cli buildSiteV2 --wsRoot . --stage dev --serve --enginePort `cat .dendron.port`
``` 

## Pod Commands
- NOTE: you can find pod ids in the [[pods|dendron.topic.pod]] page. Just add a `.import|.export` to the end of the id (eg. `dendron.pod.json.import`)

### Export Pod
- export a pod

- eg: Export notes to JSONPod
```
dendron-cli exportPod --podId dendron.json --wsRoot . --vault "vault" 
```

### Import Pod

- eg: Import notes from FilePod
```
dendron-cli importPod --podId dendron.markdown --vault "/Users/kevinlin/Dendron-es/vault" --podsDir /Users/kevinlin/Dendron-es/pods
```

### Publish Pod

- eg: Publish a note as regular markdown
```bash
dendron-cli publishPod --wsRoot . --vault ./vault --podId dendron.markdown --noteByName dendron
```
