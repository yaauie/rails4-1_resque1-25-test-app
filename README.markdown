Quick walkthrough of adding resque web as a route in a bare rails 4 install.

~~~
╭─{ yaauie @ beorn in ~/src/resque }
╰─● rails --version
Rails 4.1.4
[success.]
~~~
~~~
╭─{ yaauie @ beorn in ~/src/resque }
╰─○ rails new rails4-test-app && cd rails4-test-app
      create
      create  README.rdoc
      create  Rakefile
      create  config.ru
      create  .gitignore
      create  Gemfile
      create  app
      create  app/assets/javascripts/application.js
      create  app/assets/stylesheets/application.css
      create  app/controllers/application_controller.rb
      create  app/helpers/application_helper.rb
      create  app/views/layouts/application.html.erb
      create  app/assets/images/.keep
      create  app/mailers/.keep
      create  app/models/.keep
      create  app/controllers/concerns/.keep
      create  app/models/concerns/.keep
      create  bin
      create  bin/bundle
      create  bin/rails
      create  bin/rake
      create  config
      create  config/routes.rb
      create  config/application.rb
      create  config/environment.rb
      create  config/secrets.yml
      create  config/environments
      create  config/environments/development.rb
      create  config/environments/production.rb
      create  config/environments/test.rb
      create  config/initializers
      create  config/initializers/assets.rb
      create  config/initializers/backtrace_silencers.rb
      create  config/initializers/cookies_serializer.rb
      create  config/initializers/filter_parameter_logging.rb
      create  config/initializers/inflections.rb
      create  config/initializers/mime_types.rb
      create  config/initializers/session_store.rb
      create  config/initializers/wrap_parameters.rb
      create  config/locales
      create  config/locales/en.yml
      create  config/boot.rb
      create  config/database.yml
      create  db
      create  db/seeds.rb
      create  lib
      create  lib/tasks
      create  lib/tasks/.keep
      create  lib/assets
      create  lib/assets/.keep
      create  log
      create  log/.keep
      create  public
      create  public/404.html
      create  public/422.html
      create  public/500.html
      create  public/favicon.ico
      create  public/robots.txt
      create  test/fixtures
      create  test/fixtures/.keep
      create  test/controllers
      create  test/controllers/.keep
      create  test/mailers
      create  test/mailers/.keep
      create  test/models
      create  test/models/.keep
      create  test/helpers
      create  test/helpers/.keep
      create  test/integration
      create  test/integration/.keep
      create  test/test_helper.rb
      create  tmp/cache
      create  tmp/cache/assets
      create  vendor/assets/javascripts
      create  vendor/assets/javascripts/.keep
      create  vendor/assets/stylesheets
      create  vendor/assets/stylesheets/.keep
         run  bundle install
Fetching gem metadata from https://rubygems.org/..........
Fetching additional metadata from https://rubygems.org/..
Resolving dependencies...
Using rake (10.3.2)
Using i18n (0.6.11)
Using json (1.8.1)
Using minitest (5.4.0)
Using thread_safe (0.3.4)
Using tzinfo (1.2.1)
Using activesupport (4.1.4)
Using builder (3.2.2)
Using erubis (2.7.0)
Using actionview (4.1.4)
Using rack (1.5.2)
Using rack-test (0.6.2)
Using actionpack (4.1.4)
Using mime-types (1.25.1)
Using polyglot (0.3.5)
Using treetop (1.4.15)
Using mail (2.5.4)
Using actionmailer (4.1.4)
Using activemodel (4.1.4)
Using arel (5.0.1.20140414130214)
Using activerecord (4.1.4)
Using bundler (1.5.3)
Using coffee-script-source (1.7.1)
Using execjs (2.2.1)
Using coffee-script (2.3.0)
Using thor (0.19.1)
Using railties (4.1.4)
Using coffee-rails (4.0.1)
Using hike (1.2.3)
Using multi_json (1.10.1)
Using jbuilder (2.1.3)
Using jquery-rails (3.1.1)
Using tilt (1.4.1)
Using sprockets (2.11.0)
Using sprockets-rails (2.1.3)
Using rails (4.1.4)
Using rdoc (4.1.1)
Using sass (3.2.19)
Using sass-rails (4.0.3)
Using sdoc (0.4.0)
Using spring (1.1.3)
Using sqlite3 (1.3.9)
Using turbolinks (2.2.2)
Using uglifier (2.5.3)
Your bundle is complete!
Use `bundle show [gemname]` to see where a bundled gem is installed.
         run  bundle exec spring binstub --all
* bin/rake: spring inserted
* bin/rails: spring inserted
[success.]
~~~
~~~
╭─{ yaauie @ beorn in ~/src/resque/rails4-test-app }
╰─○ git init . && git add . && git commit -am "bare rails4"
Initialized empty Git repository in /Users/yaauie/src/resque/rails4-test-app/.git/
[master (root-commit) a8c129a] bare rails4
 56 files changed, 905 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Gemfile
 create mode 100644 Gemfile.lock
 create mode 100644 README.rdoc
 create mode 100644 Rakefile
 create mode 100644 app/assets/images/.keep
 create mode 100644 app/assets/javascripts/application.js
 create mode 100644 app/assets/stylesheets/application.css
 create mode 100644 app/controllers/application_controller.rb
 create mode 100644 app/controllers/concerns/.keep
 create mode 100644 app/helpers/application_helper.rb
 create mode 100644 app/mailers/.keep
 create mode 100644 app/models/.keep
 create mode 100644 app/models/concerns/.keep
 create mode 100644 app/views/layouts/application.html.erb
 create mode 100755 bin/bundle
 create mode 100755 bin/rails
 create mode 100755 bin/rake
 create mode 100755 bin/spring
 create mode 100644 config.ru
 create mode 100644 config/application.rb
 create mode 100644 config/boot.rb
 create mode 100644 config/database.yml
 create mode 100644 config/environment.rb
 create mode 100644 config/environments/development.rb
 create mode 100644 config/environments/production.rb
 create mode 100644 config/environments/test.rb
 create mode 100644 config/initializers/assets.rb
 create mode 100644 config/initializers/backtrace_silencers.rb
 create mode 100644 config/initializers/cookies_serializer.rb
 create mode 100644 config/initializers/filter_parameter_logging.rb
 create mode 100644 config/initializers/inflections.rb
 create mode 100644 config/initializers/mime_types.rb
 create mode 100644 config/initializers/session_store.rb
 create mode 100644 config/initializers/wrap_parameters.rb
 create mode 100644 config/locales/en.yml
 create mode 100644 config/routes.rb
 create mode 100644 config/secrets.yml
 create mode 100644 db/seeds.rb
 create mode 100644 lib/assets/.keep
 create mode 100644 lib/tasks/.keep
 create mode 100644 log/.keep
 create mode 100644 public/404.html
 create mode 100644 public/422.html
 create mode 100644 public/500.html
 create mode 100644 public/favicon.ico
 create mode 100644 public/robots.txt
 create mode 100644 test/controllers/.keep
 create mode 100644 test/fixtures/.keep
 create mode 100644 test/helpers/.keep
 create mode 100644 test/integration/.keep
 create mode 100644 test/mailers/.keep
 create mode 100644 test/models/.keep
 create mode 100644 test/test_helper.rb
 create mode 100644 vendor/assets/javascripts/.keep
 create mode 100644 vendor/assets/stylesheets/.keep
[success.]
~~~

Now, add resque to Gemfile and edit routes file per instructions,
then run `bundle` to ensure everything is installed...

~~~
╭─{ yaauie @ beorn in ~/src/resque/rails4-test-app (✘ master) }
╰─● bundle
Resolving dependencies...
Using rake (10.3.2)
Using i18n (0.6.11)
Using json (1.8.1)
Using minitest (5.4.0)
Using thread_safe (0.3.4)
Using tzinfo (1.2.1)
Using activesupport (4.1.4)
Using builder (3.2.2)
Using erubis (2.7.0)
Using actionview (4.1.4)
Using rack (1.5.2)
Using rack-test (0.6.2)
Using actionpack (4.1.4)
Using mime-types (1.25.1)
Using polyglot (0.3.5)
Using treetop (1.4.15)
Using mail (2.5.4)
Using actionmailer (4.1.4)
Using activemodel (4.1.4)
Using arel (5.0.1.20140414130214)
Using activerecord (4.1.4)
Using bundler (1.5.3)
Using coffee-script-source (1.7.1)
Using execjs (2.2.1)
Using coffee-script (2.3.0)
Using thor (0.19.1)
Using railties (4.1.4)
Using coffee-rails (4.0.1)
Using hike (1.2.3)
Using multi_json (1.10.1)
Using jbuilder (2.1.3)
Using jquery-rails (3.1.1)
Using mono_logger (1.1.0)
Using rack-protection (1.5.3)
Using tilt (1.4.1)
Using sprockets (2.11.0)
Using sprockets-rails (2.1.3)
Using rails (4.1.4)
Using rdoc (4.1.1)
Using redis (3.1.0)
Using redis-namespace (1.5.0)
Using sinatra (1.4.5)
Using vegas (0.1.11)
Using resque (1.25.2)
Using sass (3.2.19)
Using sass-rails (4.0.3)
Using sdoc (0.4.0)
Using spring (1.1.3)
Using sqlite3 (1.3.9)
Using turbolinks (2.2.2)
Using uglifier (2.5.3)
Your bundle is complete!
Use `bundle show [gemname]` to see where a bundled gem is installed.
[success.]
~~~

Committing changes. See them [here](https://github.com/yaauie/rails4-1_resque1-25-test-app/commit/25b10e5b414b950987a92085cfcaf8171aae4d53)

~~~
╭─{ yaauie @ beorn in ~/src/resque/rails4-test-app (✘ master) }
╰─● git commit -am "add resque to Gemfile and edit routes.rb file per instructions"
[master 25b10e5] add resque to Gemfile and edit routes.rb file per instructions
 3 files changed, 23 insertions(+)
[success.]
~~~

Starting a rails server, and requesting `GET http://0.0.0.0:3000/resque`...

~~~
╭─{ yaauie @ beorn in ~/src/resque/rails4-test-app (✔ master) }
╰─● rails server
Warning: Running `gem pristine --all` to regenerate your installed gemspecs (and deleting then reinstalling your bundle if you use bundle --path) will improve the startup performance of Spring.
=> Booting WEBrick
=> Rails 4.1.4 application starting in development on http://0.0.0.0:3000
=> Run `rails server -h` for more startup options
=> Notice: server is listening on all interfaces (0.0.0.0). Consider using 127.0.0.1 (--binding option)
=> Ctrl-C to shutdown server
[2014-07-22 05:56:41] INFO  WEBrick 1.3.1
[2014-07-22 05:56:41] INFO  ruby 1.9.3 (2012-04-20) [x86_64-darwin12.2.1]
[2014-07-22 05:56:41] INFO  WEBrick::HTTPServer#start: pid=57411 port=3000


Started GET "/resque" for 127.0.0.1 at 2014-07-22 05:57:21 +0000


Started GET "/resque/overview" for 127.0.0.1 at 2014-07-22 05:57:21 +0000
[2014-07-22 05:57:21] WARN  Could not determine content-length of response body. Set content-length of the response or set Response#chunked = true


Started GET "/resque/jquery-1.3.2.min.js" for 127.0.0.1 at 2014-07-22 05:57:21 +0000
[2014-07-22 05:57:21] WARN  Could not determine content-length of response body. Set content-length of the response or set Response#chunked = true


Started GET "/resque/style.css" for 127.0.0.1 at 2014-07-22 05:57:21 +0000
[2014-07-22 05:57:21] WARN  Could not determine content-length of response body. Set content-length of the response or set Response#chunked = true


Started GET "/resque/ranger.js" for 127.0.0.1 at 2014-07-22 05:57:21 +0000
[2014-07-22 05:57:21] WARN  Could not determine content-length of response body. Set content-length of the response or set Response#chunked = true


Started GET "/resque/jquery.relatize_date.js" for 127.0.0.1 at 2014-07-22 05:57:21 +0000
[2014-07-22 05:57:21] WARN  Could not determine content-length of response body. Set content-length of the response or set Response#chunked = true


Started GET "/resque/reset.css" for 127.0.0.1 at 2014-07-22 05:57:21 +0000
[2014-07-22 05:57:21] WARN  Could not determine content-length of response body. Set content-length of the response or set Response#chunked = true


Started GET "/resque/poll.png" for 127.0.0.1 at 2014-07-22 05:57:21 +0000
[2014-07-22 05:57:21] WARN  Could not determine content-length of response body. Set content-length of the response or set Response#chunked = true
^C[2014-07-22 05:57:33] INFO  going to shutdown ...
[2014-07-22 05:57:33] INFO  WEBrick::HTTPServer#start done.
Exiting
[success.]
~~~
