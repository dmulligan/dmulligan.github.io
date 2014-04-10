---
layout: post
title: CVS - Notes to self
---

For a current project, I am forced, by the client, to use CVS as the source code control system. I am, however, using my own Git repository on top of CVS for development work. Using CVS has forced me to refamiliarise myself with some basic commands which I am leaving here as a reminder to myself.


Checkout a project:

    cvs co <project>


Checkout a branch:

	cvs co -r <branch_name> <project>


Switch branch:

	cvs up -r <branch_name>


Review the branch of the working directory (inc. any sticky tag):

	cvs stat busy.html


List all branches in the repository:

	cvs log -h | awk -F"[.:]" '/^\t/&&$(NF-1)==0{print $1}' | sort -u

Thanks to [StackOverflow](http://stackoverflow.com/a/2765076/318302)


Create a tag:

	cvs tag -cR T_START_branch_name


Review locally changed files:

	cvs -qn update
- -q quite
- -n don't modify any local files


Add a new file:

	cvs add <filename>
	cvs commit <filename>


Check in a modified file:

	cvs ci <filename>


Remove a file:

	cvs remove <filename>
	cvs commit <filename>


Resurrect a removed file from the CVS Attic:

	cvs add <filename>
	cvs commit <filename>

Commit all additions, removals and modifications:

	cvs commit


Compare two CVS directories:

	diff --exclude="CVS" -rq <dir_1> <dir_2>


Compare two CVS branches:

	cvs co -r <branch_name_1> <project>;mv <project> <branch_name_1>
	cvs co -r <branch_name_2> <project>;mv <project> <branch_name_2>
	diff --exclude="CVS" -rq <branch_name_1> <branch_name_2>

I'm sure there is a better way to checkout a project using a given directory name!
