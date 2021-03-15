# common_github-create-repo
=========

This role will create a repo on github.
This will also need a set-vars-all of the project you will work on.

## Requirements
------------

All dependencies will appear on requirements.yml file

## Role Variables
--------------

### Input vars

    github_create_repo:
      1:
        repo_name: repo4
        workspace: arsolute
        project: MONO
        is_private: true
        scm: git

    Recomended to save this var encrypted
    github_password: some token

### Output Vars:
create_repository_response
From which you can use to verify if the repo was already created or not.
#### Example:
`when: create_repository_response.status == 400 and (create_repository_response.content|from_json)['error']['message']  == "Repository with this Slug and Owner already exists."`

## Dependencies
------------

All dependencies will appear on requirements.yml file
Needs to specify github_password in some encrypted role as dependency like encryptvar_project

## Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

      - hosts: localhost

        pre_tasks:
           - raw:  ansible-galaxy role install -r requirements.yml

        tasks:
          - name: Including role to test
            include_role:
              name: '../common_github-create-repo'

## License
-------

BSD

## Author Information
------------------
Made by @sergi-canas
