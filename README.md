Ansible variables
=================

Ansible playbook and roles which help to test the precedence of variables.


Usage
-----

1. Run the playbook and see what value is printed where
2. Go to the place where the variable is defined and comment it out
3. Then run the playbook again to see which other variable is printed out
4. Repeat the steps 1-3 until you comment out the last variable


Run the playbook
----------------

```
$ ansible-playbook -i hosts -l localhost -e '{ "xxx": "This is the value passed to the playbook from command line" }' ./site.yaml
```


Vars order
----------

1. Command line (`-e EXTRA_VARS`)
2. Role params in the play OR in the role `dependencies`
3. `vars_files` section in the role
4. `vars` section in the play
5. `defaults` file in the role


General override rules
----------------------

1. Defaults in child role can be overridden by vars in parent role
2. `vars` in child role can be overridden in parent role by passing params to
   the child role definition in the `dependencies` list of the parent role
