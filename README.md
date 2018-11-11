# hapi

The Human API. A toolkit of bash shortcuts for developers.

## prj

`prj` is how you start working on a *project*.

A project correlate with a git repo.  A presumption is presently being made that you are working out of the `~/projects` folder. *TODO*

The purpose of the `prj` command is to:

- get you into the correct directory to work on the project 
- install the project from git, if it isn't downloaded yet
- if installed, find new updates to the project
- start up any virtual environment needed to develop the project
- potentially run health/testing on the project to get status (future feature)

```
  prj project_name
```

This will 

* attempt to `cd` into ~/projects/project_name
* if the folder doesn't exist, it will try to go to your `HAPI_REPO` and download a project of `project_name`.
* if it found the folder, it will attempt to `git fetch` to notify you of other developer's updates to the codebase.
* if it finds a folder named `~/.venv/project_name`, it will attempt to start a python `virtualenv` with it.


## tkts

The intent of this is to give one set of commands that connect to any ticketing system.  
Presently JIRA is the only implementation.

### Commands

```
  # list tkts assigned to you
  tkts 

  # detail view
  tkts ID-<tab-complete><enter>

  # comment
  tkts ID-123 "I am the very comment of a modern major general."

  # create tkts
  tkts c[reate]

# comment
```

### `tkts` Installation

`tkts` has a few requirements.

The `bin` folder in this project needs to be in your `$PATH`.

```
	echo "export PATH=$PWD/bin/:$PATH" ~/.bash_profile
```

An environment environment variable pointing to your jira server.  Consider adding this to your `~/.bash_profile`.

```
    export HAPI_TKTS="jira.your-company.com:443"
    export HAPI_REPO="git@github.com:YourName"
```

While you're in your `~/.bash_profile` you can add tab completion with the following:

```
  echo "source $PWD/bash/bash_profile" >> ~/.bash_profile
```

Finally, add a password file.

```
  echo "$user-name:$password" > ~/.jira_pass
  chmod 0600 ~/.jira_pass
```


- ticketing: jira, trello, bugzilla, flat file
  - state changing -> code review
  - project tkts
- software lifecycle
- version control
  - RSS: peer submissions
  - review
- news
- project contexts
  - hi
- project planning
  - graphs
  - wiki pages
- chat?
- build status
