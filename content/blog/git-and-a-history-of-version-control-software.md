---
title: 'Git, and a History of Version Control Software'
date: 2022-09-03T12:19:55+02:00
Tags: [technology, history]
math: false
draft: false
---

Git is a version control system (VCS). That is to say, it tracks the history of
your code project as you make changes to it. In 2022, programmers from all
around the world live and breathe Git. It is very difficult to overstate just
how much Git is used in today's software world. As an extreme example, all of
the Windows source code is stored in a single Git repository: 350 million
files, which make the repository 300 gigabytes in size.[^1] To give a more
trivial example, the source code of Git itself is in a git repository.[^2] For
all of Git's ubiquity, however, it was not always the standard VCS that
developers automatically opted for.

Back when the computer was a niche object and a mastery of its usage and
programming won you the title of a "nerd", developers did not have the
privilege to a use such a powerful and dynamic VCS as Git. Actually, at one
point in the past there was no VCS at all. As Juan Buis writes[^3], for any
software project that you worked on back then, there would be a designated
person who owned the master version and you would be given access to only the
part of the codebase that needed work.  When you were finished, your changes
would be verified for errors and these changes would be made directly to the
central master version.

This meant, in particular, that it was very hard to track the codebase. The
only way was to constantly store copies of the master version. But for large
projects this would require an increasingly large amount of disc space, at a
time when 8-inch floppy discs had barely come into the market. To add to that,
if the master version got corrupted or deleted, all of your hard work would
flow right down the drain.

Finally, in 1972, the first VCS in software history was developed. It was
called Source Code Control System (SCCS) and was written by developer Marc
Rochkind for the IBM 360 running OS and the PDP-11 running UNIX.[^4] According
to Rochkind, its key features can be summarised into four categories.

1. _Storage_: Every version of a module is stored in the same file and any
   source code that appears in several versions of the module is stored only
   once, thus saving disc space. All prior versions can be accessed using SCCS.

2. _Protection_: Contributors can be given restricted access to the codebase,
   so that a person is allowed to edit only the modules assigned to them.

3. _Identification_: SCCS stamps load modules[^5] with the version number,
   date, time, and other such information; the source code that made the load
   module can be inferred just from this information.

4. _Documentation_: The authors of each change are recorded along with other
   such information.

These can perhaps be called the basic principles of revision control since all
VCSs that came after SCCS, although being much more powerful and flexible, based
themselves on these capabilities.

The second generation of VCSs subsequently brought improvements.
One of these, Concurrent Versioning System (CVS) was created by Dick Grune in
July 1986 in order to be able to work together with his students on the
development of the [ACK C
compiler](https://en.wikipedia.org/wiki/Amsterdam_Compiler_Kit). The problem
was that they all had really different schedules: one worked nine-to-five, the
other worked irregularly, and Grune could only work on it in the evenings; CVS
allowed them to commit changes in their own time.[^6] It started out as a
collection of shell scripts written by Grune, called _cmt_, and became CVS when
Brian Berliner translated to C a cleaned-up version of cmt.  CVS went on to
become the standard VCS for a long time after Jim Kingdon adapted CVS to work
remotely over TCP/IP, which allowed use of CVS by the open-source community.
CVS won the STUG Award in 2003.[^7]

The next major open-source VCS that came along was Subversion. It was created
by CollabNet, Inc. in 2000 to be an improvement of CVS which removed some bugs
and added more features, which, by 2001, was sufficiently advanced to host its
own source code.[^8] Version 1.0 was released in 2004, and it was accepted as
a top-level Apache project in 2010. Subversion was very much preferred to CVS
because of the improvements it brought: moving and renaming files was cleaner,
commits were with respect to the whole tree and not just individual files, and
so on. Around the time Subversion was first released were born its primary
contemporary rivals: Mercurial and Git.

Both Mercurial and Git arose out of the Linux kernel project that was started
by Linus Torvalds. The project initially used BitKeeper to track source-code
history, a proprietary VCS created by the company BitMover. The reason Linus
opted for BitKeeper was that it was free under a community licence. That was
until Andrew Tridgell decided to reverse-engineer BitKeeper to create his own
tool that would allow non-contributors to access the Linux kernel source; the
content of a BitKeeper repository could only be checked out by using the
proprietary client. He was later accused by BitMover as violating the community
licence, which was consequently removed: the only way to use BitKeeper was to
pay.[^9]

Since there was no other free VCS in 2005 that had could match the distributive
functionality and the speed of BitKeeper that was essential in developing the
Linux kernel, Linus decided to write his own; this became Git. Almost at the
same time as the Git project was announced, another kernel developer, Olivia
Mackall, started working on another VCS called Mercurial in response to
BitMover discontinuing the free usage of BitKeeper in the kernel project.
These otherwise conspicuous names can be understood from the following quotes:

> Shortly before the first release, I read an article about the ongoing
> Bitkeeper debacle that described Larry McVoy as mercurial (in the sense
> of 'fickle'). Given the multiple meanings, the convenient abbreviation,
> and the good fit with my pre-existing naming scheme (see my email
> address), it clicked instantly. Mercurial is thus named in Larry's
> honor. I do not know if the same is true of Git.[^10]
>
> (Olivia Mackall)

> I'm an egotistical bastard, so I name all my projects after myself. First
> Linux, now Git.[^11]
>
> (Linus Torvalds)

According to Linus, Git is better than Mercurial.[^12] But according to most
normal people, although there are some differences, they are performance-wise
very close and both very fast. That said, performance does not always translate
to ease of utility. I have never used Mercurial and thus cannot comment on
whether an everyday Mercurial user will find it hard to revert changes and
perform other version control actions. Actually, I would not be surprised if
the average Mercurial user knew more about how Mercurial works than the average
Git user who does not know how Git works, simply because many, many more people
use Git and Mercurial[^13] and this includes people who are not professional
programmers.  But Git, from my experience, is not easy to use; this is
summarised best by the following XKCD comic:[^14]

{{< image src="https://imgs.xkcd.com/comics/git_2x.png" width="50%" >}}

Version control has therefore had a long and rich history spanning over fifty
years. Perhaps all of this culminates in Git and Mercurial, and no better
systems for revision control will ever be created. This would not be surprising
since their sheer versatility far surpasses any other imaginable system.  Or
perhaps this versatility is merely an illusion, as with all the other big VCSs
that came along and lost their popularity in the matter of a few decades. Only
time will tell.

[^1]: Harry, Brian. "The Largest Git Repo on the Planet" Brian Harry’s Blog, 28 Feb. 2019, [https://devblogs.microsoft.com/bharry/the-largest-git-repo-on-the-planet](https://devblogs.microsoft.com/bharry/the-largest-git-repo-on-the-planet).

[^2]: It can be found at [https://git.kernel.org/pub/scm/git/git.git/](https://git.kernel.org/pub/scm/git/git.git/).

[^3]: Juan Luis. "How Git Changed the History of Software Version Control." HackerNoon, 11 June 2018, [https://hackernoon.com/how-git-changed-the-history-of-software-version-control-5f2c0a0850df](https://hackernoon.com/how-git-changed-the-history-of-software-version-control-5f2c0a0850df).

[^4]: Rochkind, Marc J. "The Source Code Control System." IEEE Transactions on Software Engineering, vol. SE-1, no. 4, 1975, pp. 364–70. Crossref, https://doi.org/10.1109/tse.1975.6312866. A scanned PDF can be found [here](https://basepath.com/aup/talks/SCCS-Slideshow.pdf).

[^5]: Load modules are something specific to programming on the IBM OS/360 or the PDP-11 that I do not know anything about. Perhaps good places to begin looking would be the (extensively researched) Wikipedia pages for the [IBM System/360](https://en.wikipedia.org/wiki/IBM_System/360) series and the [PDP-11](https://en.wikipedia.org/wiki/PDP-11).

[^6]: Grune, Dick. "Concurrent Versions System CVS." Dick Grune’s Website, [https://dickgrune.com/Programs/CVS.orig](https://dickgrune.com/Programs/CVS.orig). Accessed 3 Sept. 2022.

[^7]: "STUG Award." USENIX, 7 May 2020, [https://www.usenix.org/about/stug/](https://www.usenix.org/about/stug/).

[^8]: "What Is Subversion?" Red Bean, [https://svnbook.red-bean.com/en/1.7/svn.intro.whatis.html](https://svnbook.red-bean.com/en/1.7/svn.intro.whatis.html). Accessed 3 Sept. 2022.

[^9]: McAllister, Neil. "Linus Torvalds’ BitKeeper Blunder." InfoWorld, 2 May 2005, [https://www.infoworld.com/article/2670360/linus-torvalds--bitkeeper-blunder.html](https://www.infoworld.com/article/2670360/linus-torvalds--bitkeeper-blunder.html).

[^10]: Mackall, Olivia. "Why Did Matt Choose the Name Mercurial?" Mercurial, 2012, [https://lists.mercurial-scm.org/pipermail/mercurial/2012-February/041807.html](https://lists.mercurial-scm.org/pipermail/mercurial/2012-February/041807.html). Accessed 3 Sept. 2022. Note that Olivia Mackall was formerly Matt Mackall; I do not know the reason behind her using another name.

[^11]: McMillan, Robert. "After Controversy, Torvalds Begins Work on 'Git.'" PC World, 20 Apr. 2005, [https://www.pcworld.idg.com.au/article/129776/after_controversy_torvalds_begins_work_git_/](https://www.pcworld.idg.com.au/article/129776/after_controversy_torvalds_begins_work_git_/). Accessed 3 Sept. 2022.

[^12]: He says this in "Tech Talk: Linus Torvalds on Git." YouTube, uploaded by Google, 14 May 2007, [www.youtube.com/watch?v=4XpnKHJAok8](https://www.youtube.com/watch?v=4XpnKHJAok8).

[^13]: "Version Control Systems Popularity in 2016." RhodeCode, 2016, [https://rhodecode.com/insights/version-control-systems-2016](https://rhodecode.com/insights/version-control-systems-2016).

[^14]: Comic taken from [https://xkcd.com/1597/](https://xkcd.com/1597/). During my research for this blogpost, I found [Oh Shit, Git!?!](https://ohshitgit.com/); try this website out if you make a mistake in handling your Git repository. I also found [this](https://hackaday.com/wp-content/uploads/2017/04/flowgit.png) image that really helps in understanding basic Git actions.
