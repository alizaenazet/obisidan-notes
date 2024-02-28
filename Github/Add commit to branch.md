## `git fetch`
sebelum memulai bekerja untuk mendapatkan perubahan terbaru dari repositori utama.
```
From https://github.com/alizaenazet/cashirin_app
 * [new branch]      dev        -> origin/dev
 * [new branch]      staging    -> origin/staging
 * [new tag]         v0.1.0     -> v0.1.0
```

## `git checkout dev`

```
M	pom.xml
M	src/main/java/module-info.java
D	src/main/java/org/openjfx/App.java
D	src/main/java/org/openjfx/SystemInfo.java
M	target/classes/module-info.class
D	target/classes/org/openjfx/App.class
D	target/classes/org/openjfx/SystemInfo.class
D	target/maven-status/maven-compiler-plugin/compile/null/createdFiles.lst
D	target/maven-status/maven-compiler-plugin/compile/null/inputFiles.lst
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
```

## `git checkout -b "branch-name"`

Membuat branch baru dan langsung beralih ke branch tersebut.
```
Switched to a new branch 'adding-layer-class'
```

## `git add *`

Menambahkan file ke staged area untuk commit. Jika ingin menambahkan semua file, gunakan `git add .`
```
```

## `git status`

```
On branch adding-layer-class
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   mainClass/App.java
	new file:   mainClass/SystemInfo.java
```

## `git commit -m "commit desc"`

Membuat commit dengan pesan commit.
```
[adding-layer-class c52641c] added class layer
 2 files changed, 42 insertions(+)
 create mode 100644 src/main/java/layers/mainClass/App.java
 create mode 100644 src/main/java/layers/mainClass/SystemInfo.java
```

## `git push -u origin branch-name`

Melakukan push perubahan ke branch di repositori GitHub.
```
Enumerating objects: 13, done.
Counting objects: 100% (13/13), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (9/9), 1.10 KiB | 1.10 MiB/s, done.
Total 9 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'adding-layer-class' on GitHub by visiting:
remote:      https://github.com/alizaenazet/cashirin_app/pull/new/adding-layer-class
remote:
To https://github.com/alizaenazet/cashirin_app.git
 * [new branch]      adding-layer-class -> adding-layer-class
branch 'adding-layer-class' set up to track 'origin/adding-layer-class'.
```


