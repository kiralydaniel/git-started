Setup your GitHub
This a step by step guide on how to setup your Git and GitHub account to work properly using SSH.

On August 12th, 2021 there has been a significant change on how GitHub allows to authenticate their users: https://github.blog/changelog/2021-08-12-git-password-authentication-is-shutting-down/.

What can be really frustrating when encountering such problem is that there are lots and lots of solutions to the problem you have, but they are already outdated and no longer valid.

Lets go step-by-step through the new process!

## #1 Create a GitHub account
Go to https://github.com/ and create your personal account if you haven't done it yet.

## #2 Try to clone a repository
We use git to copy some repositories, work on them and commit changes. So the first step is usually cloning such repository. Lets take some example public repository and see what our options are.

Please go to: https://github.com/public-apis/public-apis which is the most popular public repository on GitHub.

When trying to clone such repository via SSH, a following pop-up should appear: no_public_ssh_keys.png

We apparently have to fix this issue.

## #3 Add a new public key
One common way to authenticate users is by providing username and password. Because such data can be stolen, phished or simply guessed, it isn't the safest option. Another option is to use a pair of keys, one public (may be known to others) and one private (only owner can know it). Those keys are usually a very long string that would be impossible to guess, thus providing extra security.

In our case we are pointed to: https://github.com/settings/ssh/new , where a simple form with Title and Key is presented to us.

We can give it any Title we want, let's go with CodeKey. To generate the Key you need to open your Git bash and execute following command:

$ ssh-keygen -t ed25519 -C "your_email@example.com"

You should get something similar to, where highlited is location of the file with your key: pub_location.png

You need to oopen the file with .pub extension in a simple notepad and copy its content. It will be something alike: ssh-ed25519 AAABC3NzaC1lZDI1NTE5AAAAIF3TtA4r3SqqJS6JFMKByz3sv+y9cl1R+x4z5jgotalE your_email@example.com

You need to fill in this value in the form recommended by git: add_new_key_form.png.png

After it has been successful you should have they key ready: key_created.png

Now you should be able to copy the repository using SSH

The last thing is to clone it, so please open git bash in your desired directory and try to run the command:

git clone git@github.com:public-apis/public-apis.git

You should be last time prompted if you want to give permission to cloning operation as such: clone_successful.png

Eventually you should find the folder with solution in the directory where you executed the commands.
