---
layout: post
title: Git - Push Date
---

On a current project, my team is using a Git repository on top of the client's CVS repository. This allows the team to create feature branches and share code between each other without having to relie on limited functionality of CVS.  Near the end of each sprint, I commit all changes into the client's CVS repository which is auto deployed to the QA environment. By using Git, we can ensure that we still have regular checkins by developers and still control our releases to QA without the code getting auto deployed and possibly breaking that environment. However, I did notice what maybe considered a short coming of Git, depending on your point of view! 

On a Friday evening, I asked each developer to ensure that all code was checked in and pushed to our central Git repository before I pulled and committed all changes into the CVS repository. Each developer followed my instructions and, as planned, I committed all changes into the CVS repository! Great, our sprint was released on time and everyone got to go home for the weekend.

Come Monday morning and I was left a little confused as I noticed not all files made it into the CVS repository! From reviewing the Git log, I could see that all files were committed before my deadline, but not all files were checked into the CVS repository! I must have made a mistake, surely this couldn't be the case!

Only after giving myself a stern talking down to, did I realize what happened. While all developers did commit their code to Git before my deadline, not all developers pushed their commits to the central Git repository on time!

When reviewing the Git log, you see the date/time that each commit took place, not when those commits were pushed to the central repository. What would really help here would be if Git kept track of a 'push date', but this is not the case for a good reason. You see, Git is a distributed version control system, what does a 'push date' really mean? What if developer A pushed commits to developer B's repository, who later pushed those same commits to the central repository. Which 'push date' would you be interested in, developer A's or developer B's? In addition, a 'push date' can't be added as part of the commit, as that would change the commit ID due to a different SHA1 hash each time!

From digging around, there appears to be two possible solutions:

1. Attach a note to each Git commit

Git allows notes to be attached to objects, without changing the objects themselves. Notes can be then displayed when using the Git log command. This feature allows for the creation of a Git hook that would add a note to each commit to identify when the push took place. Since hooks are specific to each repository, you could make it so that the note clearly identify which repository the push date is referring to. Not every Git repository would require this hook, maybe just your central one.

Creating the hook

- Modify the post-receive hook on your central repository


	#!/bin/sh
	#
	# This hook adds a note, using a custom ref, to each new commit contained the date that the push to this repository took place.
	#
	# (TODO Create the hook and put it here)
	#
	# To enable this hook, make this file executable by "chmod +x post-update".
	NOTE_REF=GitPushDate
	REPO=[repository_url]
	DATE=`date`

	while read oldrev newrev ref
	do
		echo "$ref"
		git notes --ref=$NOTE_REF add $ref -m "Commit $ref pushed on $date"
	done

	# Used a custom note ref so that it's less likely to be overwritten buy other notes.
	
	git log --show-notes=*
	git notes --ref=GitPushDate remove 4da66f248de917e6d4bd4bd14c63e1e6d041c104 


- Git allows notes to be changed, allowing a user to modify / delete previously created notes containing push dates, be it by accident or otherwise. Your central repository should be setup to refuse any commit that tries to alter a previously saved note with the custom ref of 'GitPushDate'. To do this, you will need to modify the pre-receive hook.


NOTE: (pardon the pun) Git ignores upstream notes by default, so developers need to explicitly fetch notes or configure Git to do so by default. However, this information may not be needed by all developers.

	# Push all notes to the origin repository
	git push origin refs/notes/*

	# Fetch all notes from the origin repository
	git config --add remote.origin.fetch "+refs/notes/*:refs/notes/*"

	# Output all note types from the origin repository in the log output
	git config --add notes.displayRef "refs/notes/origin/*"

	# git config --add remote.origin.fetch "+refs/notes/*:refs/remote-notes/origin/*"
	# git config --add notes.displayRef "refs/remote-notes/origin/*"


2. The Git reflog command

It appears to be possible to track a push date on the centeral repository using [reflog](http://stackoverflow.com/a/12704702/318302), I didn't get to try this out, but its soemthing that I would like to follow up on.

Resources

- http://git-scm.com/2010/08/25/notes.html
- https://www.kernel.org/pub/software/scm/git/docs/git-notes.html
- http://stackoverflow.com/a/6799031/318302
