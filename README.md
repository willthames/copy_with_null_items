# Showcase for bug at [ansible/ansible#9689](https://github.com/ansible/ansible/pull/9689)

`ansible-playbook -vv -i localhost, first_found.yml localhost`

demonstrates the behaviour (it tries to copy
`files/hello/world/this/is/odd/afile` to `dest`).

```
[will@will first_found (master)]$ ansible-playbook -vv
first_found.yml -i localhost,

PLAY [localhost]
**************************************************************

GATHERING FACTS
***************************************************************
<localhost> REMOTE_MODULE setup
ok: [localhost]

TASK: [showcase | with_first_found is odd when no files exist]
****************
changed: [localhost] => {"changed": true, "checksum":
"da39a3ee5e6b4b0d3255bfef95601890afd80709", "dest":
"/tmp/whatever/files/hello/world/this/is/odd/afile", "gid": 1000,
"group": "will", "item": null, "md5sum":
"d41d8cd98f00b204e9800998ecf8427e", "mode": "0664", "owner": "will",
"secontext": "unconfined_u:object_r:user_tmp_t:s0", "size": 0, "src":
"/home/will/.ansible/tmp/ansible-tmp-1417501831.78-240666070710062/source",
"state": "file", "uid": 1000}

PLAY RECAP
********************************************************************
localhost                  : ok=2    changed=1    unreachable=0
failed=0
```
