- **Branch** : [[Branch & Commit Convention#Branch Convention]]
- Commit : [[Branch & Commit Convention#Commit Convention]]
- References: [[Branch & Commit Convention#References]]

## Branch Convention
### Long living branches

#### master/main
this is where stable production ready code lands. No direct commits are allowed.

#### Develop/staging
this is a construction area. All new features are merged to it. This branch should be buildable all the time

### Special braches

####  **Feature branch**
- branches off from **develop**  
- merges to **develop **[[Branch & Commit Convention#Develope/staging]]
- A git branch should start with a category. Pick one of these `feature`, `bugfix`, `hotfix`, or `test` :
	- `feature` is for adding, refactoring or removing a feature
	- `bugfix` is for fixing a bug
	- `hotfix` is for changing code with a temporary solution and/or without following the usual process (usually because of an emergency)
	- `test` is for experimenting outside of an issue/ticket
	![[Pasted image 20230909163954.png]]

Exemple
````
git branch <category/reference/description-in-kebab-case>
````

`git branch feature/issue-42/create-new-button-component`
`git branch test/no-ref/refactor-components-with-atomic-design`
#### **Release branch**
- branches off from **develop  
- merges to **master** and **develop**  
- naming: **release**, **rc**

#### **Hotfix branch**
 branches off from **master**  
- merges to **master** and **develop** or **release** (if exists)  
- naming: **hotfix**

![[Pasted image 20230909163933.png]]


## Commit Convention

### Category
A commit message should start with a category of change. You can pretty much use the following 4 categories for everything: `feat`, `fix`, `refactor`, and `chore`. 

- `feat` is for adding a new feature
- `fix` is for fixing a bug
- `refactor` is for changing code for peformance or convenience purpose (e.g. readibility)
- `chore` is for everything else (writing documentation, formatting, adding tests, cleaning useless code etc.)

### **Statement(s)**
After the colon, the commit description should consist in short statements describing the changes.  
  
Each statement should start with a verb conjugated in an imperative way. Statements should be seperated from themselves with a "`;`".

```
git commit -m "<category: do something; do some other things>"
```

### **Examples**
- `git commit -m 'feat: add new button component; add new button components to templates'`
- `git commit -m 'fix: add the stop directive to button component to prevent propagation'`
- `git commit -m 'refactor: rewrite button component in TypeScript'`
- `git commit -m 'chore: write button documentation'`


## References
- https://dev.to/varbsan/a-simplified-convention-for-naming-branches-and-commits-in-git-il4
- https://medium.com/android-news/gitflow-with-github-c675aa4f606a