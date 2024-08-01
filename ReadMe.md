## Version Control
- system that records changes to a file (any file)
- **Recovery** retrieve entire project back to previous state
- **Who modified** 
- **Compare changes** over time using Version Control

### Local Version Control Systems

version-control method of choice is to copy files into another directory with timestamps.
- Error prone
It is easy to forget which directory you’re in and accidentally write to the wrong file or copy over files you don’t mean to

![Paste image 20]

- local VCSs has a simple database that kept all the changes to files under revision control.
- GNU **Revision Control System** automates the storing, retrieval, logging, identification, and merging of revisions.
- works by keeping patch sets (differences between files) in a special format on disk; it can then re-create what any file looked like at any point in time by adding up all the patches.

### Centralized Version Control Systems
**CVS | Subversion | Perforce**

To collaborate with developers on other systems
![[Pasted image 20240731145401.png]]
- single server that contains all the versioned files, and a number of clients that check out files from that central place. For many years, this has been the standard for version control.
- Administrators have fine-grained control over who can do what.
- **Downsides**
single point of failure that the centralized server represents.
If that server goes down for an hour, then during that hour, nobody can **collaborate** at all or **save versioned changes** to anything they’re working on.

### Distributed Version Control Systems
**Git | Mercurial | Darcs**

![[Pasted image 20240731150218.png]]


- fully mirror the repository, including its full history
- clients don’t just check out the latest snapshot of the files
- They fully mirror the repository, including its full history.
- any of the client repositories can be copied back up to the server to restore it.
- Every clone is really a full backup of all the data

### History of Git

Linux Kernel ( open source software )

Software Changes using patches & archived files 
Using BitKeeper Tool (Commercial Company) revoked free of charge
Linux Developer Community & Linus Torvalds Developed their own Tool based on BitKeeper with their own Goals 
- Speed
- Simple Design
- Non linear Development (with Parallel Branches system)
- Fully Distributed
- Efficient with large projects

#### Git Snapshots
- Git don’t use **delta-based version control** (“store as a set of files and the changes made to each file over time)
- Every time you commit, Git take a picture of all the files, stores a reference to that snapshot

![[Pasted image 20240731153138.png]]
- To be efficient, if files have not changed, Git doesn’t store the file again.
![[Pasted image 20240731153023.png]]


* Nearly Every Operation Is Local, like Browsing the History. no problem with network latency. Read simply from local database.

#### Git Has Integrity
- **checksummed** before it is stored, can’t lose information in transit or get file corruption without Git being able to detect it. Using **SHA-1 hash**
- Git stores everything in its database not by file name but by the hash value of its contents.
#### Git only add data
- Any action, git only add data to its Database. 
- It hard to erase a data.

#### Git States

**Modified   Staged  Committed** 

Modified - File changed , not committed to Database.

Staged - Marked the modified file in current version to go to next Commit Snapshort

Committed - Data is safely stored in Local Database.

Three sections 
**Working Directory    Staging Area      Git Directory**

![[Pasted image 20240731160710.png]]

**Working Directory**
Single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.

**Staging Area**
is a file, generally contained in your Git directory, that stores information about what will go into your next commit.

**Git Repository**
stores the metadata and object database for your project

**Basic Git workflow**

![[Pasted image 20240731172831.png]]

![[Pasted image 20240731172854.png]]

- modify file In Working Directory. If it was changed since it was checked out but has not been staged, it is modified.
- selectively stage just those changes you want to be part of your next commit, which adds only those changes to the staging area. modified and was added to the staging area. it is staged.
- Commit it, takes files in staging area & Snapshot permanently to git directory.


#### Command line
Run all git commands
GUI only run partial commands for simplicity.


#### Your Identity
Set User name & Email address 
`$ git config --global user.name "John Doe"`
`$ git config --global user.email johndoe@example.com”`

**Option EMacs Editor**
`“$ git config --global core.editor emacs”`

#### Checking Your Settings
`“$ git config --list`
`user.name=John Doe`
`user.email=johndoe@example.com`
`color.status=auto`
`color.branch=auto`
`color.interactive=auto`
`color.diff=auto`
`...”`

`$ git config user.name`
`John Doe`

#### Local Git Repository

Add directory & use `git init`
`Git add` - track the specific file
`Git commit -m ‘message’` 

#### Clone Git Repository
`git clone <URL>`

**Clone to newfolder**
`git clone <URL> Folder`

Transfer Protocol
- HTTP Protocol
- SSH Protocol

#### Recording Changes to the Repository
Remember that each file in your working directory can be in one of two states: tracked or untracked.
- Tracked files are files that were in the last snapshot, as well as any newly staged files; they can be unmodified, modified, or staged.
- In short, tracked files are files that Git knows about.
![[Pasted image 20240731170131.png]]

#### Check Status
`git status`

 
