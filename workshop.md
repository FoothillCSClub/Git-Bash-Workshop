
Git / Bash Workshop
===================

# What is the command line?

The command line is a non-graphical way to interact with your computer.
In other words all interactions with the computer through the command
line are in the form of text.

Almost all modern operating systems ship with some sort of command line.
Windows has both CMD and Powershell. Linux and Macs have several forms
of command line, which are variously referred to as "the "terminal",
"bash", and "the console".

In this workshop, we're going to focus on bash, so if you're on Windows,
you're going to need to install a (relatively small) piece of software
called "git bash" in order to follow along; Go to
[gitforwindows.org](https://gitforwindows.org/), and click "Download".
That should take you to a page with some release notes on it. Scroll
down the section marked "Downloads" and find the appropriate .EXE file
file for your machine.  This will probably be the file marked
"Git-2.17.0-64-bit.exe".  If you're lost, here are some direct
[64-bit](https://github.com/git-for-windows/git/releases/download/v2.17.0.windows.1/Git-2.17.0-32-bit.exe)
and
[32-bit](https://github.com/git-for-windows/git/releases/download/v2.17.0.windows.1/Git-2.17.0-64-bit.exe)
download links.  Once you've downloaded the installer, follow the
on-screen instructions to finish the installation. If you're not sure
what to do, accepting the defaults should yield reasonable results. Note
that this will install both bash *and* git, which we will need later.

Opening up bash on your machine is a little bit different depending on
what operating system you're using.

 1. Macs: Open up the Finder, go to Applications > Utilities, and open the one
    named "Terminal". A small window with a white backround and black text
    should pop up.
 2. Windows: Search for "Git Bash" in the start menu, and execute it.
    You should be presented with window having a black background and
    some multi-colored text.
 3. Linux: Look for something like "Terminal" or "Console" in your
    applications menu (maybe under "System"?) and click on it.

If you have trouble with these steps, flag down someone from the workshop crew
for help.

Have a look at the text inside your new terminal window there's probably
a short snippet of text with some symbols in it followed by a `$` sign
and cursor. The `$` sign is the terminal's way of saying "What should I
do now?". It's waiting for you give it commands, so let's give it some;
type `ls -l` and press `ENTER`.

The `ls` command displays a list files and folders in the current folder.
In general, the command line requires you to type in some command, and press
`ENTER` to execute it. The terminal then tries to fulfill your request as best
it can, and at the end gives you another prompt (`$`) to tell you that it's
done.

Why would you use this? It sounds terribly primitive!
It is. But it has it's compensations. For one thing, interactions with a
computer performed via a command line are much easier to automate. For most
graphical applications automation is a secondary concern in comparison to
looking good and having a smooth and responsive user interface. Command line
programs, by contrast tend to be much easier to plug into one another, and
assemble into *scripts*, which can very useful for many software
engineering-related tasks.

# How do I use the command line?

Generally speaking, type in some command and press `ENTER`. But what
command should you type? That of course depends on what you're trying to
accomplish; If you're trying to figure out what's in the current
directory, the `ls` command is a good place to start, as we've already
seen. But what about copying, deleting, and renaming files? Each of
these has its own command:

 * `$ cp <source filename> <destination filename>`
   Copies `<source filename` and saves the copy in `<destination filename>`
 * `$ rm <filename>`
   Deletes `<filename>`
 * `$ mv <old filename> <new filename>`
   Renames (or moves) `<old filename>` into `<new filename>`
 * `$ cd <directory name>`
   Moves to a new current directory
 * `$ mkdir <new directory>`
   Creates a new directory

A note about the notation used here; when specifying a command to be
executed in the terminal, it is conventional to write it like this: `$
<command>`. The `$` sign represents the prompt given you by the terminal
(there's no need to type it) and `<command>` is what you should type.

Since all of the commands given here are file manipulation commands, it
might be helpful to know how to type out file names. First off, in a
modern terminal, most filenames can be autocompleted if you press
`<TAB>` midway through typing the filename. So if I have a file with a
long name that I want to rename to something more manageable, I normally
would have to do something like: `$ mv
this_is_an_obnoxiously_long_file_name_so_sue_me.txt shortname.txt`. What
a mouthful! But TAB completion will let me do something like:

`$ mv this_is_an<TAB>`

After which, the prompt should look something like:

`$ mv this_is_an_obnoxiously_long_file_name_so_sue_my.txt `

And then I can easily complete the command to:

`$ mv this_is_an_obnoxiously_long_file_name_so_sue_my.txt shortname.txt`

And press `<ENTER>`.

# So what's git?

We're going to switch gears a bit and start covering a much more
specific set of command line tools, specifically the git version control
system, which brings us back to the original question; what's git?

Git is a set of tools (programs) that attempt to solve the collaboration and
file versioning problems that arise when trying to work on a software project
with other people.

More informally, git tries to eliminate the problems associated with emailing
copies of your code to the people on your team and hoping that they'll be able
to make it work with whatever code that they just wrote while you were working
on yours. If you've ever doing tried this, you're no doubt aware that this
scenario quickly becomes an organizational nightmare. (If you've never done
this, count your blessings.)

So how does git make this any better? Git provides a system that can
track what changes you make to which files, when you make them, and also
provides facilities to easily share those changes with your team
members.

So how does that work? When working with git, the changes you make to
your code are committed to a data store know as a repository (or *repo*
for short). Once the changes are committed, they can be easily shared
with other internet-connected repositories, and your team members can
easily download and use your changes.

# How do I make use of git?

_A note for mac users_: While Macs do have bash by default they don't
ship ship with git, so you may need to install it. If you already have
XCode installed you needn't do anything more here.  XCode includes git
by default.  If you don't have XCode and would like to have git, download
git-osx-installer from
[SourceForge](https://sourceforge.net/projects/git-osx-installer/files/).
If you follow the SourceForge link, you should be presented with a list
of various versions of git-osx-installer. Most likely you'll want the
latest one ("git-2.16.3-intel-universal-mavericks.dmg"), but this may
depend on your operating system version.

The most common git operation that every self-respecting software developer
should know how to do is a clone. This downloads a copy of someone else's repo
to your computer. The repo includes not only all of their code the entire
change history of the code. For example,

`$ git clone git://cs.foothillstemclubs.org/git-bash-workshop.git`

will download a copy of the Markdown code I used to write this workshop.
By default, the repo will be placed in a directory called `git-bash-workshop`,
so let's move into it:

`$ cd git-bash-workshop`

Once in there, let's have a look at what we've downloaded:

`$ ls -l`

Notice that file called `workshop.md`? Open it, and you'll get a sense of deja
vu...

`$ cat workshop.md`

Now suppose you wanted to make improvements to my workshop repository;
how would you do that? First, open a new file in your favorite text
editor, and write a simple program in your favorite programming
language. For example you could make a program that outputs your name to
the console, like so:

	#include <stdio.h>
	
	int main(void) {
		printf("Hello, my name is Grond\n");
		
		return 0;
	}

Next, save the file inside the repo you just cloned. Name it something
like `<yourname>-hello.<file extension>`. So for example, the program I
just wrote would be saved as `grond-hello.c`.

After saving your file, run this command:

`$ git status`

Which should give you output something like this:

	On branch master
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		<yourname>-hello.<file extension>

	nothing added to commit but untracked files present (use "git add" to track)

In plain language, this means that you've made changes to the repository
that are not recorded as part of the repo's history (and are not visible
to other people working on the repo).

The next step is to *commit* your new program to the repository so that
it becomes part of the shared history of the repo, so that the rest of
us can see what you've done. To commit your new code, you first need to
*add* the code to the git repository's *index*, which is the list of
changes that are staged to be committed.

`$ git add <yourname>-hello.<extension>`

Now let's run `git status` again to see what's changed:

	On branch master
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		new file:   <yourname>-hello.<extension>

This means that your changes are now ready to be committed. Committing
will make your changes part of the history of the repo, and also allows
you to record a description of what your changes are and *why* you made
them. This is called a commit message, and it's very useful for people
going back to try and find bugs later on, so it's good to make commit
messages descriptive. So for example;

`$ git commit -m "Introduce myself (<yourname>) with code"`

briefly describes what you've done, and is probably sufficiently
detailed for a simple change like this. For more complex changes,
however, it's usually better to be a little bit more descriptive.

Are we done yet? Not quite. Running `git status` again gives us:

	On branch master
	Your branch is ahead of 'remotes/origin/master' by 1 commit.
	  (use "git push" to publish your local commits)
	  nothing to commit, working tree clean

Once we've committed, we can share our changes with other people by
pushing them back to the repository that we originally cloned so that
other people can see and use them.

`$ git push`

Now very likely, when you do this, you'll be presented with an error
message that looks something like this:

	To git://cs.foothillstemclubs.org/git-bash-workshop.git
	 ! [rejected]        master -> master (fetch first)
	error: failed to push some refs to 'git://cs.foothillstemclubs.org/git-bash-workshop.git'
	hint: Updates were rejected because the remote contains work that you do
	hint: not have locally. This is usually caused by another repository pushing
	hint: to the same ref. You may want to first integrate the remote changes
	hint: (e.g., 'git pull ...') before pushing again.
	hint: See the 'Note about fast-forwards' in 'git push --help' for details.

What this means is that someone else in the workshop has pushed to the
server before you, and that you have to download their changes and
reconcile them with your own before you can push. To do this, you need
to pull down their changes and merge them into yours, like this:

`$ git pull`

After you execute this, git will open up a text editor with a message in
it: `Merge branch 'master' of
git://cs.foothillstemclubs.org/git-bash-workshop` This is git's way of
annotating a *merge commit*, which is a special kind of commit message
that is generated when git merges two diverging revision histories.
Merges can get quite complicated, but for now it is sufficient to save
the commit message, and exit the text editor.

After the you're done pulling, try to push again with `git push`. If you
get lucky (and you're the first person to pull and push), you'll see
something like:

	Counting objects: 5, done.
	Delta compression using up to 4 threads.
	Compressing objects: 100% (5/5), done.
	Writing objects: 100% (5/5), 1.22 KiB | 0 bytes/s, done.
	Total 5 (delta 3), reused 0 (delta 0)
	To git://cs.foothillstemclubs.org/git-bash-workshop.git
	   9996818..07383ac  master -> master

And you're done! You've successfully contributed to the workshop's repo!
If your push gets rejected again, try pulling (and then pushing) until
you're successful. You will get there! Don't give up.
