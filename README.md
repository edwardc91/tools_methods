# Tools, methods and utilities to use
## Using git-filter-repo to replace commit's information

Use tool **git-filter-repo** to replace commits authors names and emails using
a *.mailmap* file on root of the repository. 
* Download **git-filter-repo** from [here](https://pypi.org/project/git-filter-repo/).
* Configure a *.mailmap* file on root of the repository with the information to filter and replace. More info about *.mailmap* file [here](https://lukasmestan.com/using-mailmap-in-git-repository/)
* Run on the root of the repository `git-filter-repo --use-mailmap --replace-refs delete-no-add` to replace to authors information on the way defined on .mailmap.
* Run `git show -s <commit_SHA_key>` to check the information before/after the transformation. 

**Important!!!** Do not use on a remote repository with several contribuitors, most likely will cause conflicts cause basically this command delete the old commits and create new ones with new SHA kyes.

## Using BFG Repo-Cleaner to clean repositories of big files

* Download tool BFG Repo-Cleaner from [here](https://repo1.maven.org/maven2/com/madgag/bfg/1.14.0/bfg-1.14.0.jar). **Important**, need a java virtual machine to run the executable. Extra information of tool available [here](https://rtyley.github.io/bfg-repo-cleaner/)
* Always create before a clone of the repo that you wanna clean like this `git clone --mirror git://example.com/some-big-repo.git`. **Note** the flag mirror  is used to update the references on the remote repo with the final push.
* Run `java -jar bfg.jar --strip-blobs-bigger-than 100M some-big-repo.git`. 
* Then run to command to strip out the unwanted dirty data, which Git will now recognise as surplus to requirements: 
```
$ cd some-big-repo.git
$ git reflog expire --expire=now --all && git gc --prune=now --aggressive
```

* Use 