# README

# Project Template: React/Rails API

# Description

This project is built with React on the frontend and Ruby on Rails for the backend. Together we can easily deploy them to Render.

Note: if you are not planning to deploy your app to Render and prefer to use SQLite, you will need to make the following changes in the project files:

In the `Gemfile`, replace `gem 'pg', '~> 1.1'` with `gem 'sqlite3', '~> 1.4'`.
In the `database.yml` file, change the line `adapter: postgresql` to `adapter: sqlite3`.

# Requirements

Ruby 3.2.2
Rails 7+ or higher
NodeJS (v16 or higher), and npm
Yarn
Render account
Postgresql@15

See Environment Setup below for instructions on installing these tools if you don't already have them.

# Setup

Start by cloning (not forking) the project template repository and removing the remote:

```
$ git clone git@github.com:loso-nd/gi-effort-forecaster.git your-project-name
$ cd your-project-name
$ git remote rm origin
```

Then, [create a new remote repository](https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-locally-hosted-code-to-github#adding-a-project-to-github-without-github-cli) on GitHub. Head to [github.com](https://github.com/) and click the + icon in the top-right corner and follow the steps to create a new repository. Important: don't check any of the options such as 'Add a README file', 'Add a .gitignore file', etc. — since you're importing an existing repository, creating any of those files on GitHub will cause issues.

If you're working with a partner, [add them as a collaborator](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository) on GitHub. From your repo on GitHub, go to Settings > Manage Access > Invite a collaborator and enter your partner's username. Once your partner has access, they should git clone (not fork) the repository.

Finally, connect the GitHub remote repository to your local repository and push up your code:

```
$ git remote add origin git@github.com:your-username/your-project-name.git
$ git push -u origin main
```

When you're ready to start building your project, run:

```
bundle install
rails db:create
npm install --prefix client
```

You can use the following commands to run the application:

- `rails s` : run the backend on http://localhost:3000
- `npm start --prefix client` : run the frontend on http://localhost:4000

# Environment Setup

## Step 1 - Installing rbenv

In this step, you will install rbenv and make sure that it starts automatically at boot.

To do this on [macOS](https://www.digitalocean.com/community/tutorials/how-to-install-ruby-on-rails-with-rbenv-on-macos), this tutorial will use the package manager [Homebrew](https://brew.sh/).

To do this on

### Homebrew

On macOS or Linux, we recommend installing rbenv with Homebrew.
To download the [rbenv package](https://github.com/rbenv/rbenv#rbenv-shell) with Homebrew, run the following command:

```
$ brew install rbenv ruby-build
```

This will install rbenv and the [ruby-build] (https://github.com/rbenv/ruby-build) plugin. This plugin adds
the `rbenv install` command, which streamlines the installation process for new versions of Ruby. This may install several other dependencies and
take some time.

### Debian, Ubuntu, and their derivatives

Note that the version of rbenv that is packaged and maintained in the Debian and Ubuntu repositories is out of date. To install the latest version,
it is recommended to install rbenv using git.

```
$ sudo apt install rbenv
```

### RHEL 8|CentOS 8|Rocky Linux 8

- Option 1: [Install Ruby 3 on RHEL 8|CentOS 8|Rocky Linux 8 from Repo](https://computingforgeeks.com/install-ruby-on-rhel-centos-rocky-linux/)

- Option 2: [Install Ruby 3 using rbenv on RHEL 8|CentOS 8|Rocky Linux 8](https://computingforgeeks.com/install-ruby-on-rhel-centos-rocky-linux/)

Below are the steps for Option 2:

- Install common tools required

```
$ sudo dnf -y install git make gcc curl openssl-devel zlib-devel libffi-devel readline-devel sqlite-devel
```

- Install required rbenv tool by running the following commands

```
$ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash
```

- If you prefer to Using YUM package manager, you run the command below and not the commands listed under option 2 above.

```
$ sudo yum -y install git make gcc curl openssl-devel zlib-devel libffi-devel readline-devel sqlite-devel
```

Next you need to configure your shell environment to load rbenv:

- For bash:

  Ubuntu Desktop users should configure `~/.bashrc`:

  ```
  $ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
  $ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
  $ source ~/.bashrc
  ```

  On other platforms, bash is usually configured via ~/.bash_profile:

  ```
  $ echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bash_profile
  $ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
  $ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
  ```

- For Zsh:

  ```
  $ echo 'eval "$(~/.rbenv/bin/rbenv init - zsh)"' >> ~/.zshrc
  $ echo 'eval "$(rbenv init -)"' >> ~/.zshrc
  ```

Important: Restart your shell so that these changes take effect. (Opening a new terminal tab will usually do it.)

Confirm rbenv version

```
$ rbenv -v
```

### Alternative [package managers](https://mac.install.guide/ruby/index.html) to install ruby

## Step 2 - Installing Ruby

We recommend version 3.1.3. This is the latest released version of ruby. First, use the `-l` flag to list the available versions of Ruby. If you need to upgrade you can install it using rbenv:

```
$ rbenv install -l
$ rbenv install 3.1.3
```

Once it’s done installing, set it as your default version of Ruby with the global sub-command:

```
$ rbenv global 3.1.3
```

Verify which version of Ruby you're running by entering this in the terminal:

```
$ ruby -v
```

If you are the YUM package manger, run the following commands:

```
$ rbenv install -l
$ sudo yum install @ruby:3.1
$ ruby -v
```

### If you used an alternative [ruby package manager](https://mac.install.guide/ruby/index.html) to install ruby be sure for follow the necessary steps to install the desired version of ruby necessary to for this project.

## Step 3 - Working with Gems

When you install a gem, the installation process generates local documentation. This can add a significant amount of time to each gem’s installation process, so you can turn off local documentation generation by creating a file called ~/.gemrc which contains a configuration setting to turn off this feature:

``
$ echo "gem: --no-document" > ~/.gemrc

```

Gems are packages of Ruby libraries and programs that can be distributed throughout the Ruby ecosystem. You should also install the latest versions of [Bundler](https://bundler.io/), a tool that manages gem dependencies for projects. This is needed for Rails to work correctly:

```

$ gem install bundler

```

If you are the YUM package manger, run the following commands:

```

$ sudo gem install bundler

```

## Step 4 - Installing Rails

To install Rails, use the gem install command:

```

$ gem install rails

```
Rails is a complex web development framework and has many dependencies, so the process will take some time to complete. Eventually you’ll see a message stating that Rails is installed, along with its dependencies.


If you are the YUM package manger, run the following commands:

```

$ sudo gem install rails

```


rbenv works by creating a directory of shims, or libraries that intercept calls and change or redirect them.
In this case, shims point Ruby commands to the files used by the Ruby version that’s currently enabled.
To rehash the directory of shims, run the following command:

```

$ rbenv rehash

```

Verify your installation of Rails by printing its version with this command:

```

$ rails -v

```


## Step 5 - Install NodeJS

Verify you are running a recent version of Node with:

```

node -v

```

If you are the YUM package manger, run the following commands to install node and nginx web sever:

```

$ sudo yum install @nodejs:18
$ sudo yum install @nginx:1.20

```

You can also update your npm version with the following if need be:

```

$ npm i -g npm

```


# Step 6 - Install Postgresql
Render requires that you use PostgreSQL for your database instead of SQLite. PostgreSQL (or just Postgres for short) is an advanced database management
system with more features than SQLite. If you don't already have it installed, you'll need to set it up.

## PostgreSQL Installation for WSL
To install Postgres for WSL, run the following commands from your Ubuntu terminal:

```

sudo apt update
sudo apt install postgresql postgresql-contrib libpq-dev

```

Then confirm that Postgres was installed successfully:

```

psql --version

```

Run this command to start the Postgres service:

```

sudo service postgresql start

```

Finally, you'll also need to create a database user so that you are able to connect to the database from Rails. First, check what your operating system
username is:

```

whoami

```

If your username is "ian", for example, you'd need to create a Postgres user with that same name. To do so, run this command to open the Postgres CLI:

```

sudo -u postgres -i

```

From the Postgres CLI, run this command (replacing "ian" with your username):

```

createuser -sr ian

```

Then enter control + d or type logout to exit.

This [guide](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-database#install-postgresql) has more info on setting up Postgres on WSL if
you get stuck.


## Postgresql Installation for RHEL 8|CentOS 8|Rocky Linux 8
If you are using the YUM package manager, install postgres by running the following command:

```

$ sudo yum install @postgresql:14

```

## Postgresql Installation for OSX
To install Postgres for OSX, you can use Homebrew:

```

brew install postgresql@15

```

```

brew install libpq

```

Follow the prompt listed directly after each installation by exporting the configurations in your PATH.
Once Postgres has been installed, run this command to start the Postgres service:

```

brew services start postgresql

````

# Set Up a Render Account
You can sign up for a free account at https://dashboard.render.com/register. We recommend that you sign up using GitHub as that will make it a little
easier for you to connect Render to your GitHub account. The instructions below assume you've done that.

Once you've completed the signup process, you will be taken to the Render dashboard. In order to connect Render to your GitHub account, you'll need to
click the "New Web Service" button in the "Web Services" box. On the next page, you will see a GitHub heading on the right side and below that a link
labeled "Connect account". (If you didn't sign up using GitHub, it will say "Connect account" instead.) Click that link, then in the modal that appears
click "Install." You should then be taken back to the "Create a New Web Service" page, which should now show a list of your GitHub repos. We won't
actually create a web service just yet so you are free to navigate away from the page at this point.

Next, we'll set up a PostgreSQL instance. Click the "New +" button at the top of the page and select "PostgreSQL". Enter a name for your PostgreSQL
instance. The remaining fields can be left as is. Click "Create Database" at the bottom of the page. You should now be all set to follow the steps in
the "Deploying" section.


## Deploying

This application has all the starter code needed to help you deploy your
application to Render. It's recommended to deploy your project early and push up
changes often to ensure that your code works equally well in production and
development environments.

The instructions in this section assume that you've already set up a Render
account, created a PostgreSQL instance in your account, and set up your
environment to deploy to Render. If you have not yet completed these steps, see
the Environment Setup section below.

### Create a Master Key File

In the project files, delete the `config/credentials.yml.enc` file. Then, in the
terminal, run the following:

```sh
$ EDITOR="code --wait" bin/rails credentials:edit
````

**Note**: if you use a different text editor than VS Code, you will need to replace
`code` with the appropriate command.

The command above will open a file in VS Code and wait for you to close it
before completing the process of creating the credential files. Once you've done
that, you should see both the `credentials.yml.enc` and `master.key` files in
the `config` folder. You will need the value in the `master.key` file to set up
the web service in Render.

Commit your changes and push them to GitHub.

### Create the App Database

Render allows users to create [multiple databases within a single PostgreSQL
instance][multiple dbs] using the PostgreSQL interactive terminal,
[`psql`][psql].

Navigate to your PostgreSQL instance from the Render dashboard, click the
"Connect" dropdown, then the External Connection tab, and copy the PSQL command.
Paste it into your terminal and press enter. This command connects you to the
remote PostgreSQL instance.

To create the database, run this SQL command:

```sql
CREATE DATABASE new_db_name;
```

Now if you run `\l` from the PSQL prompt, you should see a table that includes
your main PostgreSQL instance as well as the database you just created.

Run the `\q` command to exit PSQL.

[multiple dbs]: https://render.com/docs/databases#multiple-databases-in-a-single-postgresql-instance
[psql]: https://www.postgresql.org/docs/current/app-psql.html

### Create the Render Web Service

To deploy, click the "New +" button in Render and select "Web Service". You'll
see a list of all the repositories in your GitHub account. Find the repo you
want to deploy and click the "Select" button.

In the page that opens, enter a name for your app and make sure the Environment
is set to Ruby.

Scroll down and set the Build Command to `./bin/render-build.sh` and the Start
Command to `bundle exec puma -C config/puma.rb`.

Open a separate tab in your browser, navigate to the Render dashboard, and click
on your PostgreSQL instance. Scroll down to the "Connection" section, find the
"Internal Database URL", and copy it.

Return to the other tab. Scroll down and click the "Advanced" button, then click
"Add Environment Variable." Enter `DATABASE_URL` as the key, then paste in the
URL you just copied. Note that the URL will end with the name you gave your
PostgreSQL instance when you initially created it; be sure to remove that name
and replace it with the name of the database you created in the last section.

Click "Add Environment Variable" again. Add `RAILS_MASTER_KEY` as the key, and
paste the value in the `config/master.key` file you created earlier.

The completed page should look like this:

![Web service settings](https://curriculum-content.s3.amazonaws.com/phase-4/project-template/web-service-settings.png)

Scroll down to the bottom of the page and click "Create Web Service". The deploy process will begin automatically.
