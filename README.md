# INFO6150
Class Syllabus: https://docs.google.com/document/d/16Hy7E2KatczXEOLyoD9mkvXPskL3-3vD1f4jLBxXppo/edit?usp=sharing

Repository of notes and in-class practice files.

# Forking class repo and setting upstream remote
1. Install git: https://git-scm.com/downloads
2. Go to the git repo for this class: https://github.com/aprilbingham-neu/seainfo6150
3. Click “Fork” to create your copy of the repo
4. Click “Clone or download” to get a link to copy your fork on your computer
5. Click “Use HTTPS”
6. Copy link
7. Open command line and use these commands
```
git clone [copied link]
cd seainfo6150
git remote add upstream https://github.com/aprilbingham-neu/seainfo6150
```

# Pushing your changes to your fork
1. Make changes in your fork
2. Open command line and use these commands
```
cd seainfo6150
git add .
git commit -m “[commit name]”
git push origin master
```

# Pulling updates from main repo
```
cd seainfo6150
git pull upstream master
```
