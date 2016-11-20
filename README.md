# What is this?
Those files are the [ansible][1] playbooks and roles I use to manage my local
macOS machine (currently a MBP).
When I found myself reconfiguring the same stuff over and over again, whenever
I created a new user on my system, I made my decision to invest time into
automating all those steps.

[1]: http://docs.ansible.com/ansible/index.html
[2]: http://docs.ansible.com/ansible/playbooks_tags.html

# Why not simple zsh/bash scripts?
In my opinion [ansible][1] offers mainly four advantages:

- **Oranization**: With [ansible][1] you are encouraged to organize your concerns. E.g. it takes
			       care of automatically including files at the right position
- **Orchestration**: [ansible][1] can run the same tasks on many hosts. It manages
				     all the trouble of connecting to those hosts and executing
				     the tasks.
- **Granulation**: With [ansible][1] one can adavance step by step or exclude tasks from beeing
			       run (e.g. using [tags][2])
- **Idempotency**: [ansible][1] encourages to write idempotent tasks.

# How is this organized?
The project is organized on three abstraction levels: [tasks][3], [roles][4] and [playbooks][5].
Tasks are like one command in a script. A role is a collection of tasks and a playbook is a
connection between tasks and roles on one side and hosts on the other side.

Currently there are the following roles:

|Role         |Description                                                                                                                                                                                                  |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|appmanager   |Makes sure a local app manager exists. A local app manager is a system user (uid <= 500), who has no administrator rights on the system, besides installing those apps, which do not need any special rights.|
|homebrew     |Ensure homebrew is installed on the local machine. Homebrew needs a folder, where it can be installed to and a link in /usr/local/bin.|

and the following playbooks:

|Playbook     |Roles used          |Description                                                                                 |
|-------------|--------------------|--------------------------------------------------------------------------------------------|
|appmanagement|appmanager          |Ensures an easy and more secure way of app installation on the system by a local app manager|

[3]: http://docs.ansible.com/ansible/playbooks_intro.html#tasks-list
[4]: http://docs.ansible.com/ansible/playbooks_roles.html
[5]: http://docs.ansible.com/ansible/playbooks_intro.html

# How to run?
Just get a copy of the repository or clone it:

    # In Terminal.app:
    # clone the repo
    git clone https://github.com/rqelibari/ansible-osx-playbooks.git ./ansible-osx-playbooks
    # switch to the new directory
    cd ./ansible-osx-playbooks

Then choose a playbook you want to run and execute the following from inside the repository directory:

    ./ansible-playbook.pex -i ./hosts {{playbook-to-run}}.yml --ask-vault-pass

Replace *{{playbook-to-run}}* with the name of the playbook, you want to run.

## Vault Password
**Important**: The [vault][6] pass for vaults in this repo is *vaultPassword*

[6]: http://docs.ansible.com/ansible/playbooks_vault.html