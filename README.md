# IrisTest

===

This repository showcases the scenario of having a project repository (IrisTest) which uses an external scss framework,
located in a separate repository (StylesTest). The idea is to allow IrisTest contributors to use and
contribute to the StylesTest repository without leaving the IrisTest repository. For this purpose we make the StylesTest
repository a subtree of the IrisTest repo.

## How did we make the subtree?

The subtree is created with the following command: "git subtree add --prefix StylesTest https://github.com/JenPeleva/StylesTest master --squash",
where:
+ ```--prefix StylesTest``` - StylesTest is the relative path to the folder in which our subtree will resides within IrisTest.
+ ```--squash``` - The common practice is to not store the entire history of the subproject in your main repository,
but If you want to preserve it just omit the –squash
+ ```master``` - we specify the branch we want to pull from

## How do we work with IrisTest and StylesTest?

 We practically treat the StylesTest folder as a folder from the IrisTest project. We can make changes to it and push
those changes to master. If a change to the subtree files is made through its parent's repo, this change will be pushed
 to the parent's repo the same way as other files. However, to push the change to the subtree source branch
(in our case StylesTest), as well as to pull the latest files from the subtree, we use the following "push" and "pull" commands:

+ ```git subtree pull --prefix=StylesTest https://github.com/JenPeleva/StylesTest master --squash```
+ ```git subtree push --prefix=StylesTest https://github.com/JenPeleva/StylesTest master --squash```

If the subtree repo is ahead of our files, git won't allow us to push any changes to StylesTest before pulling first. If
merge conflicts occur after pulling the latest version from StylesTest, conflicts are managed the same way as standard
merge conflicts.