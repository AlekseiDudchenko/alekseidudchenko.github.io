# nerd notes

alekseidudchenko.github.io


## moving a git repository to a new remote 


I encountered the following interesting task at my job.

We move all our git-repositories from our remote server to our brand-new instance of GitLab.  

Obviously, simple `git clone` and `git push` to a new remote is not exactly what we want. We have way more remote branches on remote and for the branches a have locally they are not all on the current stage. 
The solution would be to check put every branch and pull it. The same with tags, we have a lot. The same for push. Simple `git push` pushes only one specific branch at a time. 

It comes to a big pile of boring operations giving that I have about 20 repos. 


What I've found is `git clone --bare` command and `git push --mirror` 

Let's take a look at the example


	git clone --bare https://github.com/exampleuser/old-repository
	cd old-repository
	git push --mirror https://github.com/exampleuser/new-repository



[See official docs from GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/duplicating-a-repository)





