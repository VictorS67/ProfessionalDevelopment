# What is Remote? How to change remote git repository?
## Managing remote repositories
### Adding a remote repository
To add a new remote, use the __git remote add__ command on the terminal, in the directory your repository is stored at.

The __git remote add__ command takes two arguments:
* A remote name, for example, __origin__
* A remote URL, for example, *https://github.com/user/repo.git*

For example:
<pre>
<code>
git remote add origin https://github.com/user/repo.git
# Set a new remote

git remote -v
# Verify new remote
> origin  https://github.com/user/repo.git (fetch)
> origin  https://github.com/user/repo.git (push)
</code>
</pre>

#### Troubleshooting: Remote orifin already exists
This error means you've tried to add a remote with a name that already exists in your local repository.
<pre>
<code>
git remote add origin https://github.com/user/repo.git
> fatal: remote origin already exists.
</code>
</pre>
To fix this, you can:
* Use a different name for the new remote
* Rename the existing remote repository
* Delete the existing remote repository

### Changing a remote repository's URL
The __git remote set-url__ command changes an existing remote repository URL.

The __git remote set-url__ command takes two arguments:
* An existing remote name. For example, __origin__ or __upstream__ are two common choices.
* A new URL for the remote. For example:
  *  If you're updating to use HTTPS, your URL might look like:
<pre>
<code>
https://github.com/USERNAME/REPOSITORY.git
</code>
</pre>
  * If you're updating to use SSH, your URL might look like:
<pre>
<code>
git@github.com:USERNAME/REPOSITORY.git
</code>
</pre>

#### Switching remote URLs from SSH to HTTPS
1. Open Git Bash.
2. Change the current working directory to your local project.
3. List your existing remotes in order to get the name of the remote you want to change.
<pre>
<code>
git remote -v
> origin  git@github.com:USERNAME/REPOSITORY.git (fetch)
> origin  git@github.com:USERNAME/REPOSITORY.git (push)
</code>
</pre>
4. Change your remote's URL from SSH to HTTPS with the __git remote set-url__ command.
<pre>
<code>
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
</code>
</pre>
5. Verify that the remote URL has changed.
<pre>
<code>
git remote -v
# Verify new remote URL
> origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
> origin  https://github.com/USERNAME/REPOSITORY.git (push)
</code>
</pre>
The next time you __git fetch__, __git pull__, or __git push__ to the remote repository, you'll be asked for your GitHub username and password. When Git prompts you for your password, enter your personal access token (PAT) instead. Password-based authentication for Git is deprecated, and using a PAT is more secure.

#### Switching remote URLs from HTTPS to SSH
1. Open Git Bash.
2. Change the current working directory to your local project.
3. List your existing remotes in order to get the name of the remote you want to change.
<pre>
<code>
git remote -v
> origin  https://github.com/USERNAME/REPOSITORY.git (fetch)
> origin  https://github.com/USERNAME/REPOSITORY.git (push)
</code>
</pre>
4. Change your remote's URL from HTTPS to SSH with the __git remote set-url__ command.
<pre>
<code>
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
</code>
</pre>
5. Verify that the remote URL has changed.
<pre>
<code>
git remote -v
# Verify new remote URL
> origin  git@github.com:USERNAME/REPOSITORY.git (fetch)
> origin  git@github.com:USERNAME/REPOSITORY.git (push)
</code>
</pre>

#### Troubleshooting: No such remote '[name]'
This error means that the remote you tried to change doesn't exist:
<pre>
<code>
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
> fatal: No such remote 'origin'
</code>
</pre>
Check that you've correctly typed the remote name.

### Renaming a remote repository
Use the __git remote rename__ command to rename an existing remote.
The __git remote rename__ command takes two arguments:
* An existing remote name, for example, __origin__
* A new name for the remote, for example, *destination*

#### Example
<pre>
<code>
git remote -v
# View existing remotes
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)

git remote rename origin destination
# Change remote name from 'origin' to 'destination'

git remote -v
# Verify remote's new name
> destination  https://github.com/OWNER/REPOSITORY.git (fetch)
> destination  https://github.com/OWNER/REPOSITORY.git (push)
</code>
</pre>

#### Troubleshooting: Could not rename config section 'remote.[old name]' to 'remote.[new name]'
This error means that the remote you tried the old remote name you typed doesn't exist.

You can check which remotes currently exist with the __git remote -v__ command:
<pre>
<code>
git remote -v
# View existing remotes
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
</code>
</pre>

#### Troubleshooting: Remote [new name] already exists
This error means that the remote name you want to use already exists. To solve this, either use a different remote name, or rename the original remote.

### Removing a remote repository
Use the __git remote rm__ command to remove a remote URL from your repository.
The __git remote rm__ command takes one argument:
* A remote name, for example, __destination__

#### Example
<pre>
<code>
git remote -v
# View current remotes
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
> destination  https://github.com/FORKER/REPOSITORY.git (fetch)
> destination  https://github.com/FORKER/REPOSITORY.git (push)

git remote rm destination
# Remove remote
git remote -v
# Verify it's gone
> origin  https://github.com/OWNER/REPOSITORY.git (fetch)
> origin  https://github.com/OWNER/REPOSITORY.git (push)
</code>
</pre>

#### Troubleshooting: Could not remove config section 'remote.[name]'
This error means that the remote you tried to delete doesn't exist:
<pre>
<code>
git remote rm name
> error: Could not remove config section 'remote.name')
</code>
</pre>

## References
- [Git 07: Updating Your Repo by Setting Up a Remote](https://www.neonscience.org/resources/learning-hub/tutorials/git-setup-remote)
- [Getting changes from a remote repository](https://docs.github.com/en/github/getting-started-with-github/getting-changes-from-a-remote-repository)
- [Managing remote repositories](https://docs.github.com/en/github/getting-started-with-github/managing-remote-repositories)