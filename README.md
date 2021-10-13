# nerd notes


## moving a git repository to a new remote 


I encountered the following interesting task at my job.

We move all our git-repositories from our remote server to our brand-new instance of GitLab.  

Obviously, simple `git clone` and `git push` to a new remote is not exactly what we want. We have way more remote branches on remote and for the branches a have locally they are not all on the current stage. 
The solution would be to check put every branch and pull it. The same with tags, we have a lot. The same for push. Simple `git push` pushes only one specific branch at a time. 

It comes to a big pile of boring operations giving that I have about 20 repos. 


What I've found is `git clone --bare` command and `git push --mirror` 

Let's take a look at the example


	git clone --bare https://github.com/exampleuser/old-repository.git
	cd old-repository.git
	git push --mirror https://github.com/exampleuser/new-repository.git



[See official docs from GitHub](https://docs.github.com/en/repositories/creating-and-managing-repositories/duplicating-a-repository)



Another possibility to consider is add new remote. But you will need to pull and push branches and tags.

Some helpful command:
	
	# to see all your current remotes 
	git remote -v 

	# to change the origin
	git remote set-url origin https://github.com/user/repo2.git

	# to just add a new remote keeping the existing 
	git remote add new_remote_name https://github.com/user/repo2.git

	# to remove specific remote
	git remote rm <remote-name>
	# to rename a remote
	git remote rename <old> <new>






