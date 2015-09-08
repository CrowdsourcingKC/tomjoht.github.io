---
title: "Collaborate and review content with Github"
permalink: /pubapis_github_pull_requests/
course: "Documenting REST APIs"
type: notes_docapis
---
{% include notes.html %}

## Managing reviews through Github

Chances are if you're working a documentation project that involves text files, you'll be committing them to a repository such as Github. How do you manage edits, reviews, and other collaborations with your projects? In this tutorial, you'll learn how to create branches and perform pull requests with Github.

## Create a new Github repository

1. Log in to your Github account, click the **Repositories** tab, and then click **New** to create a new repository.
	
	<img src="{{ "/images/restapicourse/github_new_repo.png" | prepend: site.baseurl }}" alt="Creating a new Github repository" />
	
2. Type a name and description, select the "Initialize this repository with a README" check box, and then click **Create repository**. 
	
	<img src="{{ "/images/restapicourse/github_repo_settings.png" | prepend: site.baseurl }}" alt="Initializing the repo" />

## Add collaborators to your project

You need to add collaborators to your Github project so they can commit edits to a branch. If people don't have write access, they can fork the project instead of making edits on a branch on the same project. If someone isn't a collaborator and they want to make edits, they will see this note:

To add collaborators to your Github project:

1. While viewing your Github repository, click the **Settings** button (gear icon) on the lower-right. 
2. Click the **Collaborators** tab on the left.
	
	<img src="{{ "/images/restapicourse/github_add_collaborators.png" | prepend: site.baseurl }}" alt="Adding collaborators" />
	
3. Type the Github usernames of those you want to have access in the Collaborator area.
4. Click **Add Collaborator**.

## Make edits in a separate branch

By default, your new repository has one branch called "Master." Usually when you're making changes or reviews/edits, you create a new branch and make all the changes in the branch. Then when finished, the repo owner merges edits from the branch into the master through something called a "pull request."

{{note}}Although you can perform these operations using git commands from terminal, it's easier to perform the actions through the browser interface.{{end}}

1. Pretend you're a SME reviewer. Go to the Github repo and create a new branch by selecting the branch drop-down menu and typing a new branch name, such as "sme review."
	
	<img src="{{ "/images/restapicourse/github_sme_review.png" | prepend: site.baseurl }}" alt="Creating a new branch" />
	
	When you create a new branch, the content from the master is copied over into the new branch. The branch is like doing a "Save as" with an existing document.
	
2. Click the **README.txt** file, and then click the pencil icon ("Edit this file") to edit the file.
	
	<img src="{{ "/images/restapicourse/github_making_branch_edits.png" | prepend: site.baseurl }}" alt="Making an edit" />
	
3. Make some changes to the content, and then scroll down and click **Commit Changes**. Explain the reason for the changes and commit the changes to your sme-review branch, and then click **Commit Changes**.
	
	Reviewers could continue making edits this way until they have finished reviewing all of the documentation. All of the changes are made on a branch, not the master.

## Create a pull request

Now that the review process is complete, it's time to merge the branch into the master. You merge the branch into the master through a pull request. Anyone on the team with write access can initiate and complete the pull request.

1. View the repository and click the **Pull requests** button on the right.
2. Click the **New pull request** button.
	
	<img src="{{ "/images/restapicourse/github_new_pull_request.png" | prepend: site.baseurl }}" alt="New Pull Request" />
	
3. Select the branch ("sme review") that you want to compare against the master.
	
	<img src="{{ "/images/restapicourse/github_compare_to.png" | prepend: site.baseurl }}" alt="Compare to" />
	
	When you compare the branch against the master, you can see a list of all the changes. You can view the changes through two options: Unified or Split. Unified shows the edits together in the same content area, whereas split shows the two files side by side.
	
4. Click **Create pull request**.
5. Describe the pull request, and then click **Create pull request**.

## Processing the pull request

Now pretend you are the repo owner, and you see that you received a new pull request. You want to process the pull request and merge the sme review branch into the master.

1. Click the **Pull requests** button to see the pending pull requests.
2. Click the pull request and view the changes by clicking the **Files changed** tab.
	
	<img src="{{ "/images/restapicourse/github_files_changed.png" | prepend: site.baseurl }}" alt="" />
	
	If you only want to implement some of the edits, go into the sme review branch and make the updates before processing the pull request. The pull request doesn't give you a line-by-line option about which changes you want to accept or reject (like in Microsoft Word's Track Changes). It's an all-or-nothing process.
	
	Note also that if the pull request is made against an older version of the master, the merges may be more difficult to make.
	
3. Click the **Conversation** tab, and then click the **Merge pull request** button.
4. Click **Confirm merge**. 
	
	The sme review branch gets merged into the master. Now the master and the sme review branch are the same. 
	
5. Click **Delete branch** button to delete the sme review branch.
	
	If you don't want to delete the branch here, you can always remove old branches by clicking the **branches** link while viewing your Github repository, and then click the Delete (trash can) button next to the branch. 
	
	<img src="{{ "/images/restapicourse/github_delete_this_branch.png" | prepend: site.baseurl }}" alt="Deleting old branches" />
	
	If you look at your list of branches, you'll see that the deleted branch no longer appears.



