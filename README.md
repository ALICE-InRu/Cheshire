# Cheshire
Contains other repos as submodules.

To initialize all submodels, use the following shell script
```
#!/bin/bash
git submodule init
for i in $(git submodule | sed -e 's/.* //'); do
    spath=$(git config -f .gitmodules --get submodule.$i.path)
    surl=$(git config -f .gitmodules --get submodule.$i.url)
    git clone --depth 1 $surl $spath
done
git submodule update
```

To update all submodules at once, try using
```
git submodule foreach git pull origin master
# git submodule foreach /path/to/some/cool/script.sh 
```

