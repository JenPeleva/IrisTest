# IrisTest

This repository showcases the scenario of having a project repository (IrisTest) which uses an external framework,
located in a separate repository (StylesTest). The idea is to allow IrisTest contributors to use and
contribute to the StylesTest repository without leaving the IrisTest repository. For this purpose we make the StylesTest
repository a subtree of the IrisTest repo.

## How do we create the subtree?

The subtree is created with the following command, executed in the IrisTest directory:
"git subtree add --prefix StylesTest https://github.com/JenPeleva/StylesTest master --squash", where:
+ ```--prefix StylesTest``` - StylesTest is the path/folder, relative to IrisTest's root, in which our subtree will
 reside (this should be the path to a new folder in IrisTest).
+ ```--squash``` - The common practice is to not store the entire history of the subproject in your main repository,
 this is why we squash the commits, but If you want to preserve the subtree history just omit the –squash
+ ```master``` - we specify the branch in StylesTest we want to pull from

## How do we work with IrisTest and StylesTest?

 We practically treat the StylesTest folder as a folder from the IrisTest project. We can make changes to it and push
those changes to master. If a change to the StylesTest repo is made through its parent's repo (through the subtree), this change will be pushed
 to the parent's repo the same way as other files, but won't be pushed to the StylesTest repository automatically. In order to
 push these changes to the StylesTest branch, as well as to pull the latest files from it, we use the following "push"
 and "pull" the following way:

+ ```git subtree pull --prefix=StylesTest https://github.com/JenPeleva/StylesTest master --squash```
+ ```git subtree push --prefix=StylesTest https://github.com/JenPeleva/StylesTest master --squash```

If the subtree repo is ahead of our subtree, git won't allow us to push any changes to StylesTest before pulling first. If
merge conflicts occur after pulling the latest version from StylesTest, conflicts are managed the same way as standard
merge conflicts.