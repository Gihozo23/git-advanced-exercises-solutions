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
