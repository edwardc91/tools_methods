# Tools, methods and utilities to use
## Using git-filter-repo to replace commits information

Use tool **git-filter-repo** to replace commits authors names and emails using
a *.mailmap* file on root of the repository. 
* Download **git-filter-repo** from [here](https://pypi.org/project/git-filter-repo/).
* Configure a *.mailmap* file on root of the repository with the information to filter and replace. More info about *.mailmap* file [here]()
* Run on the root of the repository `git-filter-repo --use-mailmap --replace-refs delete-no-add` to replace to authors information on the way defined on .mailmap.

**Important!!!** Do not use on a remote repository with several contribuitors, most likely will cause conflicts cause basically this command delete the old commits and create new ones with new sha kyes.
