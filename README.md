Git Summary.
============

Starting.
---------

**git init** \-\> To initialize git in current directory.

**git config --global user.name "<your name - (!= username)>"** \-\> set your name.
**git config --global user.email "<your email>"** \-\> set your email.

**git config user.name** \-\> check your name.
**git config user.email** \-\> check your email.

Git lifecycle
-------------
You have just created your repository or just commited and no modified, then:

- Modified: The file has been changed since last commit.
- Staged: File modified and marked but not recorded. (mod + 'git add')
- Commited: File modified, staged and recorded in our '.git' file. (mod + 'git add' + 'git commit')

        Commited \-\> Modified \-\> Staged \-\> Commited

Keep tracking
-------------
**git status** \-\> Shows files and its status. (modified, staged, commited)

**git log** \-\> Shows the history of our commits.
**git show** \-\> Shows changes made with last commit. (!= Since the last)

**git diff** \-\> Shows changes since the last commit.
(SHA = Simple Hashing Algorithm. Kind of a commit id shown when git log.)
**git diff** <SHA-before> <SHA-after> \-\> Shows changes from one commit to another one.

Travel through commits and states.
-----------------------
Terminology:
- C: commited or commit.
- M: modified.
- S: staged.

Example:
- CS -> second commit + staged state.

Imagine this is what you've done in your directory:

History   :      C1 \-\> C1M \- C1S \- C1C=C2 \-\> C2M \- C2S \- C2C=C3
Commit SHA:    <SHA1>              <SHA2>                <SHA3>

### You are in state C3:
Reversible time travels:
**git checkout HEAD~1** \-\> Files are exactly as in C2.
**git checkout HEAD~2** \-\> Files are exactly as in C1.
**git checkout <SHA2>** \-\> Files are exactly as in C1.
**git checkout <SHA1>** \-\> Files are exactly as in C1.
**git checkout HEAD** \-\> After checkout to C1 or C2, it returns all to state C3.

Non reversible time travels:
**git reset --soft <SHA2>** \-\> Files are now exactly as in C2S.
**git reset --mixed <SHA2>** \-\> Files are now exactly as in C2M.
**git reset --hard <SHA2>** \-\> Files are now exacly as in C2.

### You are in state C2S
**git restore --staged <file>** \-\> File is now as in C2M.
**git reset --mixed <SHA2>** \-\> Non reversible. Files are now exactly as in C2M.
**git reset --hard <SHA2>** \-\> Non reversible. Files are now exacly as in C2.

### You are in state C2M
**git restore <file>** \-\> File is now as in C2.
**git reset --hard <SHA2>** \-\> Non reversible. Files are now exacly as in C2.
