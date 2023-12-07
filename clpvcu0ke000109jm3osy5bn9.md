---
title: "Main vs. Master branch in GitHub"
datePublished: Thu Dec 07 2023 15:30:11 GMT+0000 (Coordinated Universal Time)
cuid: clpvcu0ke000109jm3osy5bn9
slug: main-vs-master-branch-in-github
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/UT8LMo-wlyk/upload/03790063d40e63a228b2ad9364cd7f76.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1701962678023/58d2c197-f97c-46bf-b569-5af7191e2794.jpeg
tags: github, git, github-actions-1, gitcommands, kunalkushwaha, wemakedevs

---

When I started learning GitHub commands for the first time from [the tutorial by WeMakeDevs](https://www.youtube.com/watch?v=apGV9Kg7ics), I was experimenting with it by creating, modifying, and deleting files using Git Bash. I then created my repository in GitHub, committed, and pushed those changes into the repository. I was so excited to see those green dots in my contribution graph. When I looked at my profile, there was no record of contributions on the graph.

As I was learning, I was writing all the commands in Git Bash in the master branch. I realized that there were two branches in my repository and the default was set to the main branch. But all my work was stored in the master branch.

### Main vs. Master branch

As I browsed the situation on Google, I realized many people had had the same problem before me. I learned that the main and the master branches are the same and are interchangeable. They both work the same.

When we create a repository on GitHub, it creates a repository with a single branch. This branch is the first one that is created and is the default branch. It is displayed when anyone visits the repository. This is the branch that Git checks out locally when someone clones the repository.

Developers used to fork the 'master' branch (the default version) to create secondary versions, add their code, and then merge it back again to the master branch. Things have changed now.

As of October 1, 2020, all new Git repositories on GitHub were named 'main' instead of 'master'.

### How did I fix it?

Locally, I only had the master branch. But in my repository, the main was the default branch. When I committed and pushed all the changes to my repository, it created a master branch with all the work I had done. I then had this situation where the master branch was several commits ahead of the main yet one commit behind the main.

I found the blog post by [Jonelle Noelani Yacapin](https://jonelle-noelani.medium.com/) where she faced the same situation as mine and also guided my way out of this mess.

### Step 1: Move the 'master' branch to 'main'

```bash
git branch -m master main
```

Now I don't have the master branch. Instead, I only have the main branch with the commit history of the master branch.

### Step 2: Integrate the remote changes

```bash
git pull origin main --allow-unrelated-histories
```

The remote contains work that we do not have locally. This happens when another repository pushes to the same ref. We must integrate the changes before pushing again. As the local main and remote main have completely unrelated histories, we must allow unrelated histories.

### Step 3: Push 'main' to the remote repository

```bash
git push -u origin main
```

This will push the main branch to the GitHub repository.

### Step 4: Point HEAD to the 'main' branch

```bash
git remote set-head origin main
```

We point the HEAD to the 'main' branch in GitHub so that all the commits/pushes are lined up correctly.

### Step 5: Change the default branch to 'main' on the GitHub site

This happens automatically for most of the time. If not, do it manually.

### Step 6: Delete 'master' branch on the remote repository

```bash
git push origin --delete master
```

That's it !!

### Conclusion

Sorting out the main and master branches may look confusing at first, but understanding them and executing the given steps will provide you with a favorable solution and, hence better workflow.

Feel free to connect with me on these platforms.

[**Twitter**](https://twitter.com/DeerendraS0904) | [**LinkedIn**](https://www.linkedin.com/in/deerendra-saravanan-246201267/)