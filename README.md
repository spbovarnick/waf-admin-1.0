# WORLD ARTS FOUNDATION INC

This site is built with Ruby on Rails using the latest `importmaps` to handle js files.

### Database

This app is using a postgres database locally and in production.
To create a local database you can run `rails db:create`, and then seed it with data using `rails db:seed`.

Make sure to check `storage.yml` `local` settings to use the the Pathname appropriate to your use case--setting this up from scratch or migrating from the original monorepo.

If you are transitiong from the original version of this project, you can create a copy of your original local db with the following psql command:
```
CREATE DATABASE waf_admin_rails_development
WITH TEMPLATE waf_rails_development
OWNER [Your username];
```

Because ActiveRecord attachments from the original db are stored within the other repo, you'll need to move them to this repo to access them. You can do so from your terminal with the command `cp -r absolute/path/to/original/repo/storage/* absolute/path/to/new/repo/storage`. You can get the absolute path to each repo's storage directory by opening each respective project's console and entering `Rails.root.join("storage")`.

### Local Development

- Make sure you have yarn installed globaly: `npm install --global yarn`
- Make sure you have [redis](https://redis.io/docs/install/install-redis/install-redis-on-mac-os/) installed globally (`brew install redis`) and running while working in development
- Install node modules: `yarn install`
- Precompile assets: `bundle exec rake assets:precompile`
- The master key stored in the ignored `master.key` file is required to access mailer address and app-specific password, which is stored in `config/credentials.yml.enc`
- Rather than `rails s`, boot the development server with the `bin/dev` command, which points to `Procfile.dev` to start the server and watch for `Sass` changes

If you encounter the error `[__NSCFConstantString initialize] may have been in progress in another thread when fork() was called. We cannot safely call it or ignore it in the fork() child process. Crashing instead. Set a breakpoint on objc_initializeAfterForkError to debug.` add `export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES` to your `~/.zshrc` or `~/.bashrc`. You can check that the `OBJC_DISABLE_INITIALIZE_FORK_SAFETY` variable is set correctly by opening a fresh terminal from within your IDE and running `echo $OBJC_DISABLE_INITIALIZE_FORK_SAFETY`. If `YES` is returned, go ahead and start the server.

### Third Party Tools

**_rails_live_reload_** <br/>
Using this gem for live reload during development. <br/>
[https://github.com/railsjazz/rails_live_reload](https://github.com/railsjazz/rails_live_reload)

**_Devise_** <br/>
Used for account management and authentication for the CMS. <br/>
[https://github.com/heartcombo/devise](https://github.com/heartcombo/devise)

**_Ransack_** <br/>
Used for search. <br/>
[https://github.com/activerecord-hackery/ransack](https://github.com/activerecord-hackery/ransack)

**_Acts as taggable on_** <br/>
Using this gem for tagging functionality on the `ArchiveItem` model. <br/>
[https://github.com/mbleigh/acts-as-taggable-on](https://github.com/mbleigh/acts-as-taggable-on)

**_pg-search_** <br/>
Used for faster, indexed, full-text search. <br/>
[https://github.com/Casecommons/pg_search](https://github.com/Casecommons/pg_search)

**_dartsass-rails_**
Use to compile Sass and output CSS.
[https://github.com/rails/dartsass-rails](https://github.com/rails/dartsass-rails)