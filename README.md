ansible_unregistervm_windows_newvmmounted
======================

This is an ansible role to perform unregister Hyper-V Windows VM before unmounting with Actifio.

This role covers removing Windows license key and unjoining computer from AD domain. 

Requirements
--------------

Ansible >= 2.5 and PyWinrm module are required.

Required Windows 2016 or later for Hyper-V host and VM because of using Powershell direct feature. ( Issuing commands to Hyper-V host through WinRM then passing them to taget VM using Powershell direct. )


Role Variables
--------------

Following variables are accepted/required for this role. 

| Variable Name    | Description | Required (Y/N) |
|------------------|---|---|
| tgt_vm_name      | Target VM name which will be customized with this role. | Y
| vmwin_adminuser      | Administrator user name of the target Windows VM. Default is 'Administrator' | Y
| vmwin_adminpassword  | Administrator user password of the target Windows VM. | Y

Example Playbook
----------------

### Customize Windows VM after mounting image as New VM by Actifio

```
- name: customize windows vm after mounting image as new vm by actifio
  hosts: "{{ host_group }}"
  roles:
    - ansible_customizevm_windows_newvmmounted_hyperv
  vars:
    tgt_vm_name: DemoWin2016
    vmwin_adminpassword: password

```


License
-------

Copyright 2018 <Hiroshi Takeuchi hiroshi.takeuchi@actifio.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
