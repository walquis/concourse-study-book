# Task Inputs
Concourse task inputs are directories.

NOTE: If on the command line, you give a yml-defined input a value, **the contents of that directory will be recursively copied into the container**. Newbies to Concourse (like me) may find this somewhat non-intuitive.

```
$ cat inputs_required.yml
...
inputs:
  - name: some-important-input
...

$ alias ft="fly -t tutorial"
$ tutorials/basic/task-inputs $ ft execute -c inputs_required.yml -i some-important-input=.
```
The `-i` is not necessary if current dir has same name as dir specified by the required input...
```
$ pwd
/Users/cwalquist/src/concourse-tutorial/tutorials/basic/task-inputs
$ cat input_parent_dir.yml
...
inputs:
  - name: task-inputs
...
$ ft execute -c input_parent_dir.yml
# (Same results as previous)
```

