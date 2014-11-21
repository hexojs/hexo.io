title: Deployment
---
To deploy your site with Hexo, you only need one command.

``` bash
$ hexo deploy
```

## GitHub Pages

Edit `_config.yml`.

``` yaml
deploy:
  type: github
  repo: <repository url>
  branch: [branch]
  message: [message]
```

Option | Description
--- | ---
`repo`, `repository` | GitHub repository URL (Better to use HTTPS)
`branch` | The deployer will detect the branch to use automatically. You can also customize it on your own.
`message` | Customize commit message (Default is `Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}`)

### Remove

Remove `.deploy` folder.

``` bash
$ rm -rf .deploy
```

### Custom Domain

Create a file named `CNAME` in `source` folder with the following content.

``` plain
example.com
```

- **Top-level Domain:** Add A records: `192.30.252.153`, `192.30.252.154`.
- **Subdomain**: Add a CNAME record `blog.example.com`.

Check [GitHub Pages](https://help.github.com/articles/setting-up-a-custom-domain-with-pages) for more info.

## Heroku

Edit `_config.yml`.

``` yaml
deploy:
  type: heroku
  repo: <repository url>
  message: [message]
```

Option | Description
--- | ---
`repo`, `repository` | Heroku repository URL
`message` | Customize commit message (Default is `Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}`)

### Remove

Remove `.git`, `app.js` & `Procfile`.

## Rsync

Edit `_config.yml`.

``` yaml
deploy:
  type: rsync
  host: <host>
  user: <user>
  root: <root>
  port: [port]
  delete: [true|false]
  verbose: [true|false]
  ignore_errors: [true|false]
```

Option | Description | Default
--- | --- | ---
`host` | Address of remote host |
`user` | Username |
`root` | Root directory of remote host |
`port` | Port | 22
`delete` | Delete old files on remote host | true
`verbose` | Display verbose messages | true
`ignore_errors` | Ignore errors | false

## OpenShift DIY Cartridge

Edit `_config.yml`.

``` yaml
deploy:
  type: openshift
  remote: <upstream git remote>
  branch: [upstream git branch] # Default is master
```

Option | Description | Default
--- | --- | ---
`remote` | Upstream Git remote |
`branch` | Upstream Git branch | master

## Git

Edit `_config.yml`.

``` yaml
deploy:
  type: git
  message: [message]
  repo:
    github: <repository url>,[branch]
    gitcafe: <repository url>,[branch]
```

Option | Description
--- | --- | ---
`repo`, `repository` | Repository URL and branch. Separated with a comma (`,`). The branch is `master` by default.
`message` | Customize commit message (Default is `Site updated: {{ now('YYYY-MM-DD HH:mm:ss') }}`)

## Batch Deploy

You can deploy your site to multiple destinations.

``` yaml
deploy:
- type: github
  repo: ...
- type: heroku
  repo: ...
```

## Commit message

You can customize commit message in **github**, **heroku**, **git** deployer.

Swig is availble in commit message. You can use `now(format)` to display deployment time. For example, the default message is `Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}`:

``` js
Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}
// Site updated: 2014-05-12 00:02:25
```

Commit message can be set either in shell

``` bash
$ hexo deploy -m "Commit message"
```

or in `_config.yml`.

``` yaml
deploy:
  type: github
  repo: ...
  message: "Commit message"
```

## GitCafe Pages

Edit `_config.yml`.

``` yaml
deploy:
  type: gitcafe
  repo: <repository url>
  branch: [branch]
  message: [message]
```

Option | Description
--- | ---
`repo`, `repository` | GitCafe repository URL (Better to use HTTPS)
`branch` | The deployer will detect the branch to use automatically. You can also customize it on your own.
`message` | Customize commit message (Default is `Site updated: {% raw %}{{ now('YYYY-MM-DD HH:mm:ss') }}{% endraw %}`)

### Remove

Remove `.deploy-gitcafe` folder.

``` bash
$ rm -rf .deploy-gitcafe
```
### Custom Domain

Add your custom domain on https://gitcafe.com/<username>/<project>/custom_domains

Check [GitCafe Pages](https://gitcafe.com/GitCafe/Help/wiki/Pages-%E7%9B%B8%E5%85%B3%E5%B8%AE%E5%8A%A9) for more info.

## Other Methods

All generated files are saved in `public` folder. You can copy it to wherever you like.
