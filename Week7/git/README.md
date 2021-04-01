# Final step! How to connect R studio with Github?
## Prerequisites
* Skim through all the previous tutorial and have a basic concept of how Git works
* Download and install [Git](https://docs.github.com/en/github/getting-started-with-github/set-up-git)
* Download and install [RStudio](https://www.rstudio.com/products/rstudio/download/)

## Create the remote repository on GitHub
Now that you have what you need. Let's create the repository that will hold your new project.

1. Create a new repository on GitHub.
2. Name your repository with your __project name__.
3. Enter a description for your repository.
4. Choose Public visibility (or Private if you want).
5. Select Initialize this repository with a README.
6. Click Add __.gitignore__ and select __R__.
7. Click Create repository.

## Clone the repository with Rstudio
After you've created a repository on GitHub (the remote repository), the next step is to clone it to your local environment.

1. On GitHub, navigate to the Code tab of the repository.
2. On the right side of the website, click __Clone__ or __download__.
3. Click the __Copy to clipboard__ icon to the right of the repository URL.
4. Open Rstudio on your local environment.
5. Click __File__, __New Project__, __Version Control__, __Git__.
6. Paste the repository URL and enter TAB to move to the __Project directory name__ field.
7. Click __Create Project__.

## Create an R Markdown codument in RStudio
We assume that you are very familiar with this part. If not, please visit [here](https://rmarkdown.rstudio.com/) to learn more about __R Markdown__.

## Commit and puch the changes to GitHub
After you have created the R Markdown document and finished making your changes, it is time to commit them.

1. In RStudio click the __Git__ tab in the upper right pane.
2. Click __Commit__.
3. In the __Review changes__ view, check the staged box for all files.
4. Add a commit message, for example __Add initial speed and distance report__.
5. Click __Commit__.
6. Click the __Pull__ button to fetch any remoe changes.
7. Click the __Push__ button to push your changes to the remote repository.
8. On GitHub, navigate to the Code Tab of the repository to see the changes.

## Create local branches with Git
1. In Rstudio, clock the __Terminal__ tab in the lower left pane. The Terminal tab is next to the Console tab.
2. Create a new branch, git a name to your branch.
<pre>
<code>
git branch branchname
</code>
</pre>
3. Check your repository's status
<pre>
<code>
git status
</code>
</pre>
4. Check out ro your new branch
<pre>
<code>
git checkout branchname
</code>
</pre>
5. Verify that you are now checked out to your new branch
<pre>
<code>
git status
</code>
</pre>

## Commit local changes with Git
After you change some changes to your project. It's time to commit those changes.
1. __git status__ allows us to see the satus of the files on our branch. Your files are listed under the heading __Untracked files__.
<pre>
<code>
git status
</code>
</pre>

2. Add your file to the staging area so it's prepared to become part of the next commit.
<pre>
<code>
git add .
</code>
</pre>

3. See your files' current status. Your file is now listed under the heading __Changes to be committed__.
<pre>
<code>
git add .
</code>
</pre>

4. Commit your files, write down message to describe your commit information.
<pre>
<code>
git commit -m "commit message"
</code>
</pre>

5. See the history of commits
<pre>
<code>
git log --oneline
</code>
</pre>

6. See the changes between the master branch and the current branch (HEAD)
<pre>
<code>
git diff --stat --summary master..branchname
</code>
</pre>

## Open a pull request on GitHub
Now you have make some local commits, it is time to send your changes to the remote copy of your repository on GitHub and create a Pull Request.
1. Push the changes to the remote repository
<pre>
<code>
git push -u origin branchname
</code>
</pre>

2. create a Pull Request on GitHub.

3. Fill out the body of the Pull Request with information about the changes you’re introducing.

## Merge your pull request on GitHub
Since this is your repository, you probably don’t have anyone to collaborate with (yet). Go ahead and merge your Pull Request now.
1. On GitHub, navigate to the Pull Request that you just opened.
2. Scroll down and click the big green __Merge Pull Request__ button.
3. Click Confirm Merge.

