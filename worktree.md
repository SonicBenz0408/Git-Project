# <center>Git Project--------**worktree**</center>

## 1.Linked working tree
* **Working tree, main and linked**

A working tree is a set of files in a branch linked to the repository. 
A repository consists of one main working tree and 0 or more linked working trees. 
The main working tree is where you'll work most of the time. You can create, edit, delete files here and `add` changes to the staging area. Just some usual stuff.
The linked working tree is a directory independent from the main working tree. You can do other stuff here while there are unstaged changes in the main working tree.

You can create a linked working tree in a new folder/directory from the branch you choose, so you can switch between different branches without stopping your work-in-progress.

After the changes in the new linked working tree are committed and your work is done in there, you can simply delete/remove it.


* **When & Why**

Let's say that you're working on a big feature in branch**feature**and it's nowhere near finished. If you now have to fix a sudden bug and implement a patch from the**master**branch or switch between branches to compare them to each other without using the `worktree` command, there are two ways to do it:
1. You will have to `add` your WIP to the staging area, `commit` them, go to branch**master**to do stuff, come back, and then use `git reset` to get back to where you were.
2. If you know this method, you can use `git stash` to teporarily saved your WIP, leave branch**feature**to do other stuff, and then use `git stash apply` to go back.

Both of the methods take lots of steps to complete and can be time-consuming when you have to repeat it frequently. But with the `worktree` command, you can save all those troubles and working on another branch without interrupting your current work. 


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

