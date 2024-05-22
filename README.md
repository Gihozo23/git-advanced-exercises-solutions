# git-advanced-exercises-solutions

## Part 1

### Challenge 1: Missing File Fix

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git status
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 4727dd79c258153c7e0c4ab48e5d31de17f55719 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:03:14 2024 +0200

    chore: Create third and fourth files

commit df30f9f72d091c3fc2292743869d52cb04c39cac

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git add test4.md


HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ GIT_EDITOR=vim git commit --amend
[main ac9a58d] chore: added the fourth file
 Date: Mon May 20 18:03:14 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit ac9a58d0b43e7a7d963ee84fac1547bc20a5f253 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:03:14 2024 +0200

    chore: added the fourth file

commit df30f9f72d091c3fc2292743869d52cb04c39cac
```

### challenge 2: Editing Commit History:

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit ac9a58d0b43e7a7d963ee84fac1547bc20a5f253 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:03:14 2024 +0200

chore: Create second file
    chore: added the fourth file

commit df30f9f72d091c3fc2292743869d52cb04c39cac
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:03:05 2024 +0200

    chore: Create another file

commit f304f1e957676e880885e76ed897159ad19afb69
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    chore: Create initial file

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git rebase -i HEAD~2
Stopped at df30f9f...  chore: Create another file
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main|REBASE 1/2)
$ GIT_EDITOR=vim git commit --amend
[detached HEAD ebccea4] chore: Create second file
 Date: Mon May 20 18:03:05 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md

```

### Challenge 3: Keeping History Tidy - Squashing Commits

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 60de0a4bd820c5c38a1eb2dbbd5ca8a735331f13 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:03:14 2024 +0200

    chore: added the fourth file

commit ebccea4f98bca7963d2a718b5881f05dc59b27bb
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:03:05 2024 +0200

    chore: Create second file

commit f304f1e957676e880885e76ed897159ad19afb69
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    chore: Create initial file
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git rebase -i --root
[detached HEAD 239f1a2] Creating the initial and second files
 Date: Mon May 20 18:02:54 2024 +0200
 3 files changed, 5 insertions(+)
 create mode 100644 readme.md
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit d6006b4377244dfd5cb3e0e5105804f823960dad (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:03:14 2024 +0200

    chore: added the fourth file

commit 239f1a2c674f006679ed3e29eaada3e20d4b37d9
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file


```

```bash
### Challenge 4: Splitting a Commit:

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git reset Head~

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test3.md
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git add test3.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git commit -m "create third file"
[main da4e445] create third file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git add test4.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git commit -m "create the fourth file"
[main 1f4a21e] create the fourth file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 1f4a21ee06dbc92c14debf686e7b1f37bcbe9965 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:40:27 2024 +0200

    create the fourth file

commit da4e44557b158b110b3cf4e7fb5c4a9230bf6f6b
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200

    create third file

commit 239f1a2c674f006679ed3e29eaada3e20d4b37d9
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file

```

### Challenge 5: Advanced Squashing

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git rebase -i HEAD~2
[detached HEAD 8cfbadf] Create third and fourth files
 Date: Tue May 21 11:39:52 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 8cfbadf2540c0961c42a1077a7a98df6f9f09294 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200

    Create third and fourth files

    Create third file

    Create fourth file

commit 239f1a2c674f006679ed3e29eaada3e20d4b37d9
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)

```

### Challenge 6: Advanced Squashing

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        unwanted.txt

nothing added to commit but untracked files present (use "git add" to track)

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git add unwanted.txt

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git commit -m "Unwanted commit"
[main 831bee9] Unwanted commit  
 1 file changed, 1 insertion(+) 
 create mode 100644 unwanted.txt
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git rebase -i head~2
Successfully rebased and updated refs/heads/main.

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git rebase --continue
fatal: No rebase in progress?

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git status
On branch main
nothing to commit, working tree clean

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 8cfbadf2540c0961c42a1077a7a98df6f9f09294 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200

    Create third and fourth files

    Create third file

    Create fourth file

commit 239f1a2c674f006679ed3e29eaada3e20d4b37d9
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file

commit 8cfbadf2540c0961c42a1077a7a98df6f9f09294 (HEAD -> main)n)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200

    Create third and fourth files

    Create third file

    Create fourth file

commit 239f1a2c674f006679ed3e29eaada3e20d4b37d9
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file
                                                            
```

### Challenge 6 : Reordering Commits

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 8cfbadf2540c0961c42a1077a7a98df6f9f09294 (HEAD -> maipick 8cfbadf Create third and fourth files
n)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200

    Create third and fourth files

    Create third file

    Create fourth file

pick 8cfbadf Create third and fourth files
commit 239f1a2c674f006679ed3e29eaada3e20d4b37d9
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files
pick 8cfbadf Create third and fourth files

    chore: Create initial file

    chore: Create second file

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git rebase -i --root
Successfully rebased and updated refs/heads/main.

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 88990d8ee9d2b18e01f7e0cd206c5187780e2f05 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file

commit ec3827025004328c0d7071bd312d45c65fdc907f
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200

    Create third and fourth files

    Create third file

    Create fourth file

```

### Challenge 8: Cherry-Picking Commits:

```bash
 HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git checkout -b ft/banch
Switched to a new branch 'ft/banch'

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/banch)
$ git add test5.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/banch)
$ git commit -m "Implemented test 5"
[ft/banch e344992] Implemented test 5
 1 file changed, 1 insertion(+)      
 create mode 100644 test5.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/banch)
$ git log
commit e344992cb0e276e922712c5ce8ab591a42321279 (HEAD -> ft/banch)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 12:56:44 2024 +0200

    Implemented test 5

commit 88990d8ee9d2b18e01f7e0cd206c5187780e2f05 (main)      
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file

commit ec3827025004328c0d7071bd312d45c65fdc907f
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200


HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/banch)
$ git checkout main
Switched to branch 'main'

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git cherry-pick --no-commit e344992cb0e276e922712c5ce8ab591a42321279

 ```

### challenge 9: Visualizing Commit History (Bonus)

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log --graph
* commit 88990d8ee9d2b18e01f7e0cd206c5187780e2f05 (HEAD -> main)
| Author: Gihozo23 <christellegihozo23@gmail.com>
| Date:   Mon May 20 18:02:54 2024 +0200
|
|     Creating the initial and second files
|
|     chore: Create initial file
|
|     chore: Create second file
|
* commit ec3827025004328c0d7071bd312d45c65fdc907f
  Author: Gihozo23 <christellegihozo23@gmail.com>
  Date:   Tue May 21 11:39:52 2024 +0200

      Create third and fourth files

      Create third file

      Create fourth file


```

### challenge 10: Understanding Reflogs (Bonus)

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git reflog
88990d8 (HEAD -> main) HEAD@{0}: checkout: moving from ft/banch to main
e344992 (ft/banch) HEAD@{1}: commit: Implemented test 5     
88990d8 (HEAD -> main) HEAD@{2}: checkout: moving from main 
to ft/banch
88990d8 (HEAD -> main) HEAD@{3}: rebase (finish): returning 
to refs/heads/main
88990d8 (HEAD -> main) HEAD@{4}: rebase (pick): Creating the initial and second files
ec38270 HEAD@{5}: rebase (pick): Create third and fourth files
c992bde HEAD@{6}: rebase (start): checkout c992bdea3f231e9e605c71962c74515366fc28e7
8cfbadf HEAD@{7}: rebase (finish): returning to refs/heads/main
8cfbadf HEAD@{8}: rebase (start): checkout HEAD~1
8cfbadf HEAD@{9}: rebase (finish): returning to refs/heads/main
8cfbadf HEAD@{10}: rebase (start): checkout HEAD~
8cfbadf HEAD@{11}: rebase (finish): returning to refs/heads/main
8cfbadf HEAD@{12}: rebase (start): checkout head~2
831bee9 HEAD@{13}: rebase (finish): returning to refs/heads/:

```

## Part 2
### Challenge 1: 

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

```

### challenge 2: 

```bash
HP@DESKTOP-VK7L602 MINGW64 ~re/Desktop/theGym/git advanced/git-advanced-exercises (ft//Desktop/theGym/git advanced/gnew-feature)                w-feature)
$ git add feature.txt

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/new-feature)
$ git commit -m "Implemented core functionality for new 
feature"
[ft/new-feature a89d1c8] Implemented core functionality 
for new feature
 2 files changed, 2 insertions(+)
 create mode 100644 feature.txt
 create mode 100644 test5.md
```

### Challenge 3:

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/new-feature)
$ git checkout main
Switched to branch 'main'

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        readme.txt

nothing added to commit but 
untracked files present (use "git add" to track)        

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git add readme.txt

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git commit -m "Updated project readme"
[main 07300fb] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

```

### Challenge 4: 

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log --oneline
07300fb (HEAD -> main) Updated project readme
88990d8 Creating the initial and second files
ec38270 Create third and fourth files

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ cat .git/refs/heads/main
07300fbfa63335a5867e1741ada7f0d5ea8c8752

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log
commit 07300fbfa63335a5867e1741ada7f0d5ea8c8752 (HEAD -> main)
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Wed May 22 10:44:05 2024 +0200

    Updated project readme

commit 88990d8ee9d2b18e01f7e0cd206c5187780e2f05
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

    Creating the initial and second files

    chore: Create initial file

    chore: Create second file

commit ec3827025004328c0d7071bd312d45c65fdc907f
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 11:39:52 2024 +0200

    Create third and fourth files


```

### Challenge 5: Branch deletion

```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git merge ft/new-feature
Merge made by the 'ort' strategy.
 feature.txt | 1 +
 test5.md    | 1 +
 2 files changed, 2 insertions(+)
 create mode 100644 feature.txt
 create mode 100644 test5.md

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git branch -d ft/new-feature
Deleted branch ft/new-feature (was a89d1c8).

```

### challenge 6: Creating a Branch from a Commit

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git log --oneline
7d7aa86 (HEAD -> main) Merge branch 'ft/new-feature'  
07300fb Updated project readme
a89d1c8 Implemented core functionality for new feature
88990d8 Creating the initial and second files
ec38270 Create third and fourth files
Switched to branch 'main'   
                            
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git merge ft/new-branch-fr/Desktop/theGym/git advanced/gom-commit
Already up to date.

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git checkout -b ft/new-branch-from-commit a89d1c8
Switched to branch 'ft/new-branch-from-commit'
                            
```
### challenge 7 :


``bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/new-branch-from-commit)
$ git checkout main
Switched to branch 'main'

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git merge ft/new-branch-from-commit
Already up to date.

```

### Challenge 8 : Rebasing branch

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/new-branch-from-commit)
$ git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.


```

### challenge 9: Renaming branch


```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/new-branch-from-commit)
$ git branch -m ft/new-branch-from-commit ft/improved-branch-nam

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)

```

### Challenge 10: Checking Out Detached HEAD
```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)
$ git log
commit 7d7aa861b297dd62eac081bc32ef89abd3a7eea7 (HEAD -> ft/improved-branch-nam, main)
Merge: 07300fb a89d1c8
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Wed May 22 10:56:37 2024 +0200

    Merge branch 'ft/new-feature'

commit 07300fbfa63335a5867e1741ada7f0d5ea8c8752
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Wed May 22 10:44:05 2024 +0200

    Updated project readme

commit a89d1c8d935fdf429576518d9ef2e2f4f6d6f609
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Tue May 21 22:53:27 2024 +0200

    Implemented core functionality for new feature        

commit 88990d8ee9d2b18e01f7e0cd206c5187780e2f05
Author: Gihozo23 <christellegihozo23@gmail.com>
Date:   Mon May 20 18:02:54 2024 +0200

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)
$ git checkout 07300fbfa63335a5867e1741ada7f0d5ea8c8752
Note: switching to '07300fbfa63335a5867e1741ada7f0d5ea8c8752'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to 
a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. 
Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 07300fb Updated project readme

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises ((07300fb...))
```
## Part 3  

### Challenge 1: Stashing Changes

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   feature.txt

no changes added to commit (use "git add" and/or "git commit -a")
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git stash
Saved working directory and 
index state WIP on main: 7d7aa86 Merge branch 'ft/new-feature'


```

### challenge 2: Retrieving Stashed Changes
```bash

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git stash pop
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   feature.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (63803a90ba71a73cb8199c2392eed1b4e5f24fd6)


```

### Challenge 3: Branch Merging Conflicts (Continued)

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git checkout ft/improved-branch-nam
Switched to branch 'ft/improved-branch-nam'

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)        
$ git add .

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)        
$ git checkout main
error: Your local changes to the following files would be overwritten by checkout:  
        feature.txt
Please commit your changes or stash them before you switch branches.
Aborting

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)        
$ git commit -m "feature.txt modified from the improved-branch"
[ft/improved-branch-nam dd1d1f5] feature.txt modified from the improved-branch      
 1 file changed, 2 insertions(+), 1 deletion(-)

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)        
$ git checkout main
Switched to branch 'main'

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git merge ft/improved-branch-nam
Auto-merging feature.txt
CONFLICT (content): Merge conflict in feature.txt       
Automatic merge failed; fix conflicts and then commit the 
conflicts and then commit the result.
                            
```

### Challenge 4: Resolving Merge Conflicts with a Merge Tool

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git merge ft/improved-branch-nam
Auto-merging feature.txt
CONFLICT (content): Merge conflict in feature.txt       
Automatic merge failed; fix conflicts and then commit the 
conflicts and then commit the result.
                            /Desktop/theGym/git advanced/g
HP@DESKTOP-VK7L602 MINGW64 ~MERGING)/Desktop/theGym/git advanced/git-advanced-exercises (main|MERGING)
$ git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
opendiff kdiff3 tkdiff xxdiff meld tortoisemerge gvimdiff diffuse diffmerge ecmerge 
p4merge araxis bc codecompare smerge emerge vimdiff nvimdiff
Merging:
  {local}: modified file    
  {remote}: modified file   
Hit return to start merge reeature.txt':solution tool (vimdiff):    
```

### Challenge 5: Understanding Detached HEAD State

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (ft/improved-branch-nam)
$ git checkout 07300fbfa63335a5867e1741ada7f0d5ea8c8752
Note: switching to '07300fbfa63335a5867e1741ada7f0d5ea8c8752'.

You are in 'detached HEAD' state. You can look around, make experimental
do so (now or later) by usin you can discard any commits yg -c with the switch command. Example:                  branches by switching back to 

  git switch -c <new-branch-name>                       branch to retain commits you c

Or undo this operation with:g -c with the switch command. 


  git switch -              name>

Turn off this advice by setting config variable advice.detachedHead to false        

HEAD is now at 07300fb Updating config variable advice.deted project readme

HP@DESKTOP-VK7L602 MINGW64 ~ed project readme/Desktop/theGym/git advanced/git-advanced-exercises ((07/Desktop/theGym/git advanced/g300fb...))                  0fb...))
$ git checkout main
Previous HEAD position was 07300fb Updated project readme
Switched to branch 'main'

```

### Challenge 6: Ignoring Files/Directories
```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main|MERGING)
$ touch .gitignore

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git add .

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git commit -m ".gitignore file created"
[main ec3d45a] .gitignore file created
 2 files changed, 1 insertion(+)   
 create mode 100644 .gitignore     
 create mode 100644 hey.tmp        
```

### challenge 7: Working with Tags

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git tag v1.0
```

### Challenge 8: Listing and deleting tags
```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git tag
v1.0

HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git tag -d v1.0
Deleted tag 'v1.0' (was ec3d45a)

```

### Challenge 9: Pushing Local Work to Remote Repositories
```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git push --set-upstream origin main
Enumerating objects: 27, done.
Counting objects: 100% (27/27), done.
Delta compression using up to 4 threads
Compressing objects: 100% (23/23), done.
Writing objects: 100% (27/27), 2.41 KiB | 411.00 KiB/s, done.
Total 27 (delta 11), reused 0 (delta 0), pack-reused 0    
remote: Resolving deltas: 100% (11/11), done.
To https://github.com/Gihozo23/git-advanced-exercises.git 
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

```

### Challenge 10: Pulling Changes from Remote Repositories

```bash
HP@DESKTOP-VK7L602 MINGW64 ~/Desktop/theGym/git advanced/git-advanced-exercises (main)
$ git pull origin
Updating ec3d45a..7f036b5
Fast-forward
 readme.md | 4 +---
 1 file changed, 1 insertion(+), 3 deletions(-)
```
