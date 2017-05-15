Notes:
* Yaml Ain't Markup Language (Yaml) like many other data serialization languages (such as Json) has very few, basic concepts: declarations, Lists, Associative Arrays (objects).

Variable example:
name: 'test varibale'

List example:
  - 'value1'
  - 'value2'
  - 'value3'

Associative array:
  item:
    name: The Name
    location: The Location

# Sample playbook command
```
C02Q11MMG8WM:ansible kbohra$ ansible-playbook -i kbohra1-dev.local, playbooks/setup_apache.yaml
PLAY [all] *********************************************************************

TASK [setup] *******************************************************************
ok: [kbohra1-dev.local]

TASK [Ensure the HTTpd package is present] *************************************
changed: [kbohra1-dev.local]

TASK [Ensure the httpd service is started] *************************************
changed: [kbohra1-dev.local]

PLAY RECAP *********************************************************************
kbohra1-dev.local           : ok=3    changed=2    unreachable=0    failed=0
```

# Variables example
C02Q11MMG8WM:ansible kbohra$ ansible-playbook -i kbohra1-dev.local, playbooks/variables_demo.yaml
```
PLAY [all] *********************************************************************

TASK [setup] *******************************************************************
ok: [kbohra1-dev.local]

TASK [Set variable name] *******************************************************
ok: [kbohra1-dev.local]

TASK [Print variable value] ****************************************************
ok: [kbohra1-dev.local] => {
    "msg": "test machine"
}

PLAY RECAP *********************************************************************
kbohra1-dev.local           : ok=3    changed=0    unreachable=0    failed=0
```

# System info
```
C02Q11MMG8WM:ansible kbohra$ ansible all -i kbohra1-dev.local, -m setup
kbohra1-dev.local | SUCCESS => {
    "ansible_facts": {
        "ansible_all_ipv4_addresses": [
            "xx.XX.XX.XX"
        ],
        "ansible_all_ipv6_addresses": [
            "fe80::5054:2eff:fe5b:37cc"
        ],
        "ansible_architecture": "x86_64",
        "ansible_bios_date": "01/01/2007",
        "ansible_bios_version": "Bochs",
        "ansible_cmdline": {
            "KEYBOARDTYPE": "pc",
            "KEYTABLE": "us",
            "LANG": "en_US.UTF-8",
            "SYSFONT": "latarcyrheb-sun16",
            "crashkernel": "129M@0M",
            "noapic": true,
            "quiet": true,
            "rd_NO_DM": true,
            "rd_NO_LUKS": true,
            "rd_NO_LVM": true,
            "rd_NO_MD": true,
            "rhgb": true,
            "ro": true,
            "root": "UUID=481ca459-331f-4f79-89cd-a0ef6ef3b161"
        },
        "ansible_date_time": {
            "date": "2017-05-15",
            "day": "15",
            "epoch": "1494831844",
            "hour": "07",
            "iso8601": "2017-05-15T07:04:04Z",
            "iso8601_basic": "20170515T070404843947",
            "iso8601_basic_short": "20170515T070404",
            "iso8601_micro": "2017-05-15T07:04:04.844041Z",
            XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

# Setup Variables example
```
C02Q11MMG8WM:ansible kbohra$ ansible-playbook -i kbohra1-dev.local, playbooks/setup_variables.yaml

PLAY [all] *********************************************************************

TASK [setup] *******************************************************************
ok: [kbohra1-dev.local]

TASK [Print OS and version] ****************************************************
ok: [kbohra1-dev.local] => {
    "msg": "CentOS 6.5"
}

PLAY RECAP *********************************************************************
kbohra1-dev.local           : ok=2    changed=0    unreachable=0    failed=0
```

# Extra variables (command line args)
```
C02Q11MMG8WM:ansible kbohra$ ansible-playbook -i kbohra1-dev.local, playbooks/cli_variables.yaml -e 'name=test_variable'

PLAY [all] *********************************************************************

TASK [setup] *******************************************************************
ok: [kbohra1-dev.local]

TASK [Print extra variables command arguments] *********************************
ok: [kbohra1-dev.local] => {
    "msg": "test_variable"
}

PLAY RECAP *********************************************************************
kbohra1-dev.local           : ok=2    changed=0    unreachable=0    failed=0
```


