This folder contains examples for defining vars.yml and vault.yml for different use cases.

Global variables

If you define vars.yml and vault.yml in the root directory, those variables apply to all groups defined in your inventory.

Group-specific variables

If you want different variables per group, create a group_vars/ folder in the root directory. Inside it, create one subfolder per group — the subfolder name must exactly match the group name defined in inventory.ini. Each subfolder can then contain its own vars.yml and vault.yml.

Example

Given this inventory.ini:

ini
[test_group]
192.168.1.10
192.168.1.11

[second_test_group]
192.168.1.20

To define variables individually for each group, structure your files like this:

group_vars/
├── test_group/
│   ├── vars.yml
│   └── vault.yml
└── second_test_group/
    ├── vars.yml
    └── vault.yml

Ansible automatically loads group_vars/<group_name>/vars.yml and vault.yml for any host belonging to that group no extra configuration needed.