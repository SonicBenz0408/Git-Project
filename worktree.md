# <center>Git Project--------**worktree**</center>

## 1.Linked working tree
## 2.Create a new working tree
## 3.Remove a linked working tree
`git worktree remove <worktree>`

* **How it work**

After the commit done, we can use this command to remove linked working tree, and delete the folder at the same time.

* **Warning**

This command only can remove linked working tree which is **clean**.

If you want to remove an **unclean** linked working tree, you can use **--force** as follow:

`git worktree remove -f <worktree>`   

## 4.Another method to remove
* **Delete the folder**

Instead of using the command of remove, you can directly delete the folder of linked working tree.

* **Prune**

Though the folder has been deleted, the linked working tree still exists, just loses its path.

You have to use the following command to remove the linked working tree without path:

`git worktree prune`

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

