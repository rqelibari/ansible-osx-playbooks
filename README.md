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