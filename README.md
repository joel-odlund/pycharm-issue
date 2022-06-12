This is a code examples for a Jetbrains isseue:
https://intellij-support.jetbrains.com/hc/en-us/community/posts/6032658098834--Always-select-opened-file-appears-broken-with-dependencies-between-subprojects

Steps to reproduce the issue:

- create a virual environment and activate it
- install `package-a` as an editable package
```
cd package_a 
pip install -e .
```
- open the package_a as a project directory i PyCharm
- open package_b as a sub-project ("Attach")
- In PyCharm, configure both subprojects to use the python interpreter in the previously created virtual environment
- in PyCharm, enable the 'Always Select Opened File' option. 
- Edit `package_a/src/package_a/code.py`.  (Notice two instances of the file is selected)
- Navigate to SomeClass using 'Go to Definition' (Notice that both instances of the file is selected)

in this example,  the project window will select multiple files, but scroll to `package_a/src/package_a/code.py` 
in a real setting with multiple dependencies,  it can also scroll to one of the dependency folders

it appears that there is some order between the instances of an open file,  and that the window scrolls to the first one, not necessarily the expected one. 
