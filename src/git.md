## Git cheat sheet
The organization and content of this cheat sheet is strongly based on the book [Pocket Guide: A Working Introduction. Silverman, Richard E. Git . " O'Reilly Media, Inc.", 2013.](https://books.google.it/books?hl=it&lr=&id=hqGPn2T47s4C&oi=fnd&pg=PP1&dq=git+pocket+&ots=xPJPpS5tkA&sig=GluS128Vwksyef4_mJYYAx-3AuU&redir_esc=y#v=onepage&q=git%20pocket&f=false)

---

### 1. Getting Started
**Basic configuration**

Every configuration command has the following format
```bash
git config --{local,global,system} <parameter> <value>
# order of importance (less important to most important): system,global,local
```
Most common parameters are:
``` bash
git config --global user.name "Mirco Mannino"       # Name
git config --global user.email mannino@domain.com   # E-mail
git config --global core.editor vim                 # Editor
git config --global alias.cp cherry-pick            # Alias
```

**Repository initialization**

```bash
# Create a new empy repository
git init <directory>

# Importing an exisiting project
git init 
git add . 
git commit -m "Begin project XXX"
```

**Ignoring files**

Add a ```.gitignore``` file into your repository and use the following *ignore patterns*:
```bash
# Ignore a specific file in a subdirectory
conf/config.h

# Ignore a specific file in the current directory
/config.h

# Pattern without slashes ("/") apply everywhere in this directory and below

# Ignore individual objects and object archives (*.o and *.a)
*.[oa]

# Exclude something from an existent gitignore rule
*.so            # Ignore all *.so files
!special.so     # Do NOT ignore special.so

# Ignore a folder
temp/
```
``` bash
git update-index --assume-unchanged     # Apply .gitignore rules also to tracked files
```

---

### 2. Making Commits

--- 

### MISC
# Add more files to the last commit
'''bash
git add <new files>
git commit --amend --no-edit
'''

# Merge 2+ commits
'''bash
git reset --soft HEAD~$NUM_COMMITS
git commit
''' 