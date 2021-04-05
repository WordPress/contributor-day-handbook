# How to Set Up VVV for Contributing to WordPress

[VVV (Varying Vagrant Vagrants)](https://github.com/Varying-Vagrant-Vagrants/VVV) is a virtual machine that runs on Virtualbox. In other words, it is a self-contained local development environment aimed at WordPress developers. It can be used to build sites and contribute to the development of WordPress Core.


# For Contributor Day Organizers

If you’re running a WordCamp Contributor Day, you should use the contributor day set up script to bundle a pre-configured VVV instance (including instructions) that can be copied onto USB sticks and given to attendees. Setting up a local environment over conference Wi-Fi can cause problems for all. The setup script generates a pre-built version of VVV that greatly reduces the amount of data that attendees need to download.

[Click for information about the VVV contributor day USB drive generator](https://github.com/Varying-Vagrant-Vagrants/CD-USB-Generator)


# For Contributor Day Attendees


## Installing VVV with a Contributor Day USB stick

During Contributor Days there might be USB sticks available containing the latest version of VVV which is already configured for use. This means that you won’t need to download the packages over Wi-Fi. However, you will still need to download some items and should follow the instructions provided in the files on the USB stick to get set up. 


## Installing VVV without a Contributor Day USB stick

If you don’t have a Contributor Day USB stick available, follow the instructions below:

1. Install[ VirtualBox 6.x](https://www.virtualbox.org/wiki/Downloads)
2. Install[ Vagrant 2.2.15+](https://www.vagrantup.com/downloads.html)
3. Restart your computer
4. Follow the VVV [installation instructions](https://varyingvagrantvagrants.org/docs/en-US/installation/).

## Start up VVV

1. In the command line/terminal, navigate to the directory where you installed VVV. You can sometimes drag and drop the folder on to the terminal as a fast way to type the path of the directory. **If you are on Windows this must be run with elevated administrator privileges**.
2. Install local vagrant plugins if you have not already by running this command: `vagrant plugin install --local`
3. Start VVV by running command `vagrant up`, the first time you do this will take a while
4. When complete, you should see a VVV logo with a happy teddy bear.
5. Visit `http://vvv.test` in your browser. You should see a listing of all the sites VVV created, as well as links to other administration-related tools.

## Enabling trunk and the meta environment

VVV also includes the following two environments:

*   [http://trunk.wordpress.test/](http://trunk.wordpress.test/) An SVN-based WordPress core trunk setup, useful for Contributor Days, Trac tickets, patches, general core contributing, etc.
*   [http://wp-meta.test](http://wpmeta.test) A collection of sites for contributing to WordPress.org

These two sites are disabled by default if you are installing VVV without the script on Contributor Day USB sticks. 

To enable these environments, check if you have a `config/config.yml` file in your VVV folder. If you don't have a `config.yml` file, then run `vagrant status` and it will be created for you. In `config.yml`, look for the `wordpress-trunk` and `wordpress-meta-environment` and change `skip_provisioning: true` to `skip_provisioning: false` and save. Finally, run `vagrant up --provision` to apply the change. This will take some time to run, especially if you have enabled the Meta environment.

For example to enable the trunk site, here is before:

```yaml
  wordpress-trunk:
    skip_provisioning: true # provisioning this one takes longer, so it's disabled by default
```

and here is after:

```yaml
  wordpress-trunk:
    skip_provisioning: false # provisioning this one takes longer, so it's disabled by default
```

For more detailed guide on enabling these environments, refer to [this guide](https://github.com/WordPress/meta-environment/blob/master/docs/install.md).


## Tips and tricks

*   VVV is a virtual machine (VM) that runs on Virtualbox, which means when you start it up it will keep running on your machine until you shut it down. To save your battery life you should get into the habit of shutting down the environment when you don’t need it. To do this, navigate to the directory where you installed VVV and run command `vagrant halt`. You can start the VM up again by running command `vagrant up` from the same directory.
*   WordPress Core uses SVN, so you may need to familiarise yourself with its commands if you plan on testing or writing patches. [You can find out how to work with patches here in the Core handbook](https://make.wordpress.org/core/handbook/tutorials/working-with-patches/).
*   You can run `vagrant ssh` to get inside VVV where you will find an Ubuntu Linux install with common tools such as `svn`, `git`, etc

## Create a GitHub repo (optional)

If you want to create patches for WordPress, you don’t want to use SVN. If you want to use a version control system though, Git is a good alternative. Pull requests on GitHub can provide a convenient way to receive feedback on your work and to share the patch for your contributions.

**Tip:** You can add ‘.diff’ to the end of any pull request URL and GitHub will return a diff file that you can then attach to a [Trac](https://docs.google.com/document/d/1Q4u_dOuCNGoKpD2lD4mJujredAatevlIkuAzwFhakbM/edit#heading=h.v7ymrqrnqqm8) ticket. Alternatively, you can add a link to the pull request in a Trac ticket comment.

To create a GitHub repo:

1. Make sure VVV is set up (see instructions above).
2. Swap out your SVN repo with a Git one in VVV by running the following command: `vagrant ssh -c /srv/www/wordpress-trunk/bin/develop_git`
3. Fork the [https://github.com/wordpress/wordpress-develop](https://github.com/wordpress/wordpress-develop) repo on GitHub.
4. Run the following commands to set this new repo as your origin remote: `cd ...vvv/www/wordpress-trunk/public_html && git remote set-url origin https://github.com/YOURNAME/wordpress-develop.git`
5. Check out the master branch: `git checkout master`
6. Create a feature branch based on the Trac ticket you want to work on (e.g. 12345): `git checkout -b trac-12345`
7. Add commits for your fixes and run command `git push`.
8. Go to GitHub and open a pull request to your `master` branch.
9. Copy the URL to your newly-created pull request, and paste it into a new comment on WordPress Trac and ask for feedback.

## Other resources

[Learn how to set up more sites on VVV](https://varyingvagrantvagrants.org/docs/en-US/adding-a-new-site/).

[Core Handbook - tutorial on installing a local server](https://make.wordpress.org/core/handbook/tutorials/installing-a-local-server/).

[Core Handbook - how to submit Github Pull Request to WordPress Core](https://make.wordpress.org/core/handbook/contribute/git/github-pull-requests-for-code-review/)
