# <center>Git Project--------**worktree**</center>

## 1.Linked working tree
## 2.Create a new working tree
## 3.Remove a linked working tree
## 4.Another method to remove
## 5.Lock & Unlock
### (1)Lock 
`git worktree lock [--reason <string>] <worktree>`

If a linked working tree is stored on a portable device or network share which is not always mounted, you can prevent its administrative files from being pruned by issuing the git worktree lock command, optionally specifying `--reason` to explain why the working tree is locked.
### (2)Unlock
`git worktree unlock <worktree>`

Unlock a working tree, allowing it to be pruned, moved or deleted.
### (3)Example
An example case here is:
* insert thumb drive, mount file system
* add work-tree on thumb drive, use it for a while
* lock work-tree and remove (unmount and disconnect) thumb drive
* later, re-insert thumb drive, unlock work tree, continue working

