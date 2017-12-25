# ansible-changed-example

To make sure whether changed or not if check mode

```console
$ s2i build https://github.com/sclorg/s2i-python-container.git --context-dir=3.5/test/setup-test-app/ centos/python-35-centos7 python-sample-app
$ docker-compose up -d
$ ansible-playbook -i hosts.ini changed_or_not.yml -C --diff
```

An example of result

```
...
TASK [debug] ****************************************************************************************************
ok: [ansiblechangedexample_centos7_1] => {
    "results": [
        {
            "_name": "shell",
            "changed": true
        },
        {
            "_name": "shell",
            "changed": true
        },
        {
            "_name": "file_touch",
            "changed": true
        },
        {
            "_name": "file_link_same",
            "changed": false
        },
        {
            "_name": "file_link_new",
            "changed": true
        },
        {
            "_name": "copy_same",
            "changed": false
        },
        {
            "_name": "copy_different",
            "changed": true
        },
        {
            "_name": "lineinfile_no",
            "changed": false
        },
        {
            "_name": "lineinfile_replace",
            "changed": true
        },
        {
            "_name": "find",
            "changed": false
        },
        {
            "_name": "yum_already",
            "changed": false
        },
        {
            "_name": "yum_update",
            "changed": true
        },
        {
            "_name": "pip_already",
            "changed": false
        },
        {
            "_name": "pip_update",
            "changed": true
        },
        {
            "_name": "set_fact",
            "changed": false
        },
        {
            "_name": "uri",
            "changed": false
        },
        {
            "_name": "get_url_already",
            "changed": false
        },
        {
            "_name": "get_url_new",
            "changed": true
        },
        {
            "_name": "git",
            "changed": true
        }
    ]
}

PLAY RECAP ******************************************************************************************************
ansiblechangedexample_centos7_1 : ok=77   changed=10   unreachable=0    failed=0
```
