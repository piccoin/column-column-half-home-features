# column-column-half-home-features
  piccoin column column-half home-features
Contributing to Git Large File Storage

Hi there! We're thrilled that you'd like to contribute to this project. Your help is essential for keeping it great.

This project adheres to the Open Code of Conduct. By participating, you are expected to uphold this code.

Feature Requests

Feature requests are welcome, but will have a much better chance of being accepted if they meet the first principles for the project. Git LFS is intended for end users, not Git experts. It should fit into the standard workflow as much as possible, and require little client configuration.

Large objects are pushed to Git LFS servers during git push.
Large objects are downloaded during git checkout.
Git LFS servers are linked to Git remotes by default. Git hosts can support users without requiring them to set up anything extra. Users can access different Git LFS servers like they can with different Git remotes.
Upload and download requests should use the same form of authentication built into Git: SSH through public keys, and HTTPS through Git credential helpers.
Git LFS servers use a JSON API designed around progressive enhancement. Servers can simply host off cloud storage, or implement more efficient methods of transferring data.
You can see what the Git LFS team is prioritizing work on in the roadmap.

Project Management

The Git LFS project is managed completely through this open source project and its chat room. The roadmap shows the high level items that are prioritized for future work. Suggestions for major features should be submitted as a pull request that adds a markdown file to docs/proposals discussing the feature. This gives the community time to discuss it before a lot of code has been written. Roadmap items are linked to one or more Issue task lists (example), with the roadmap label, that go into more detail.

The Git LFS teams mark issues and pull requests with the following labels:

bug - An issue describing a bug.
core-team - An issue relating to the governance of the project.
enhancement - An issue for a possible new feature.
review - A pull request ready to be reviewed.
release - A checklist issue showing items marked for an upcoming release.
roadmap - A checklist issue with tasks to fulfill something from the roadmap
Submitting a pull request

Fork and clone the repository
Configure and install the dependencies: script/bootstrap
Make sure the tests pass on your machine: script/test
Create a new branch: git checkout -b my-branch-name
Make your change, add tests, and make sure the tests still pass
Push to your fork and submit a pull request
Accept the GitHub CLA
Pat yourself on the back and wait for your pull request to be reviewed.
Here are a few things you can do that will increase the likelihood of your pull request being accepted:

Follow the style guide where possible.
Write tests.
Update documentation as necessary. Commands have man pages.
Keep your change as focused as possible. If there are multiple changes you would like to make that are not dependent upon each other, consider submitting them as separate pull requests.
Write a good commit message.
Building

Git LFS depends on having a working Go 1.5+ environment, with your standard $GOROOT and $GOPATH environment variables set. The easiest way to download Git LFS for making changes is go get:

$ go get github.com/github/git-lfs
This clones the Git LFS repository to your $GOPATH. If you typically keep your projects in a specific directory, you can symlink it from $GOPATH:

$ cd ~/path/to/your/projects
$ ln -s $GOPATH/src/github.com/github/git-lfs
From here, run script/bootstrap to build Git LFS in the ./bin directory. Before submitting changes, be sure to run the Go tests and the shell integration tests:

$ script/test        # runs just the Go tests
$ script/integration # runs the shell tests in ./test
$ script/cibuild     # runs everything, with verbose debug output
Updating 3rd party packages

Update Nut.toml.
Run script/vendor to update the code in the .vendor/src directory.
Commit the change. Git LFS vendors the full source code in the repository.
Submit a pull request.
Releasing

If you are the current maintainer:

Create a new draft Release. List any changes with links to related PRs.
Make sure your local dependencies are up to date: script/bootstrap
Ensure that tests are green: script/cibuild
Bump the version in lfs/lfs.go, like this.
Add the new version to the top of CHANGELOG.md
Build for all platforms with script/bootstrap -all (you need Go setup for cross compiling with Mac, Linux, FreeBSD, and Windows support).
Test the command locally. The compiled version will be in bin/releases/{os}-{arch}/git-lfs-{version}/git-lfs
Get the draft Release ID from the GitHub API: curl -in https://api.github.com/repos/github/git-lfs/releases
Run script/release -id {id} to upload all of the compiled binaries to the release.
Publish the Release on GitHub.
Update Git LFS website (release engineer access rights required).
Ping external teams on GitHub:
@github/desktop
Build packages:
rpm
apt
Bump homebrew version and generate the homebrew hash with curl --location https://github.com/github/git-lfs/archive/vx.y.z.tar.gz | shasum -a 256 (example)
Resources

Contributing to Open Source on GitHub
Using Pull Requests
GitHub Help
