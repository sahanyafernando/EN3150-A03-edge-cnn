# GitHub Step-by-Step Guide

## A. Colne repository and setup

1. Go to GitHub → EN3150-A03-edge-cnn
2. Copy the https link through the green colour code box.
3. open a terminal in your laptop.
4. follow the commands.

In VS Code terminal:

```powershell
git clone https://github.com/sahanyafernando/EN3150-A03-edge-cnn.git
git switch [your branch name]
```

## B. Daily/stage workflow

Before changing files:

```powershell
git switch main
git pull
git status 
```
If the work tree is clean,

```powershell
git switch [your branch name]
git add .
git commit -m "[Meaningfull message about what you have done]"
git push origin HEAD
```

Repeat with a new commit after each genuine stage. 
# Very Important: Work only in your branch and do not commit to main.

## C. Recommended commit sequence







