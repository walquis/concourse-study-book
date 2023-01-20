# Task Scripts - the run feature

```
$ pwd
/Users/cwalquist/src/concourse-tutorial/tutorials/basic/task-scripts

$ ls
task_show_uname.sh	task_show_uname.yml	test.sh

$ cat task_show_uname.yml
...
inputs:
  # Note that the name matches the current directory name ...
  - name: task-scripts

run:
  path: /bin/sh
  args: ["./task-scripts/task_show_uname.sh"]
...

$ ft execute -c task_show_uname.yml
```
