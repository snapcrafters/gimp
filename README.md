<h1 align="center">
  <img src="gimp.png" alt="GIMP">
  <br />
  GIMP - The GNU Image Manipulation Program
</h1>

<p align="center"><b>This is the snap for GIMP</b>, <i>"The Free &amp; Open Source Image Editor"</i>. It works on Ubuntu, Fedora, Debian, and other major Linux
distributions.</p>

<p align="center">
<a href="https://snapcraft.io/gimp"><img src="https://snapcraft.io/gimp/badge.svg" alt="Snap Status"></a>
<a href="https://github.com/snapcrafters/gimp/actions/workflows/sync-version-with-upstream.yml"><img src="https://github.com/snapcrafters/gimp/actions/workflows/sync-version-with-upstream.yml/badge.svg"></a>
<a href="https://github.com/snapcrafters/gimp/actions/workflows/release-to-candidate.yaml"><img src="https://github.com/snapcrafters/gimp/actions/workflows/release-to-candidate.yaml/badge.svg"></a>
<a href="https://github.com/snapcrafters/gimp/actions/workflows/promote-to-stable.yml"><img src="https://github.com/snapcrafters/gimp/actions/workflows/promote-to-stable.yml/badge.svg"></a>
</p>

## Install

```shell
snap install gimp
```

([Don't have snapd installed?](https://snapcraft.io/docs/core/install))

<p align="center">Published for <img src="https://raw.githubusercontent.com/anythingcodes/slack-emoji-for-techies/gh-pages/emoji/tux.png" align="top" width="24" /> with :gift_heart: by Snapcrafters</p>

## How to contribute to this snap

Thanks for your interest! Below you find instructions to help you contribute to this snap.

The general workflow is to submit pull requests that merges your changes into the `candidate` branch here on GitHub. Once the pull request has been merged, a GitHub action will automatically build the snap and publish it to the `candidate` channel in the Snap Store. Once the snap has been tested thoroughly, we promote it to the `stable` channel so all our users get it!

### Initial setup

If this is your first time contributing to this snap, you first need to set up your own fork of this repository.

1. [Fork the repository](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo) into your own GitHub namespace.
2. [Clone your fork](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository), so that you have it on your local computer.
3. Configure your local repo. To make things a bit more intuitive, we will rename your fork's remote to `myfork`, and add the snapcrafters repo as `snapcrafters`.

    ```shell
    git remote rename origin myfork
    git remote add snapcrafters https://github.com/snapcrafters/gimp.git
    git fetch --all
    ```

### Submitting changes in a pull request

Once you're all setup for contributing, keep in mind that you want the git information to be all up-to-date. So if you haven't "fetched" all changes in a while, start with that:

```shell
git fetch --all -p
```

Now that your git metadata has been updated you are ready to create a bugfix branch, make your changes, and open a pull request.

1. All pull requests should go to the stable branch so create your branch as a copy of the stable branch:

    ```shell
    git checkout -b my-bugfix-branch snapcrafters/candidate
    ```

2. Make your desired changes and build a snap locally for testing:

    ```shell
    snapcraft --use-lxd
    ```

3. After you are happy with your changes, commit them and push them to your fork so they are available on GitHub:

    ```shell
    git commit -a
    git push -u myfork my-bugfix-branch
    ```

4. Then, [open up a pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) from your `my-bugfix-branch` to the `snapcrafters/candidate` branch.
5. Once you've opened the pull request, it will automatically trigger the build-test action that will launch a build of the snap. You can watch the progress of the snap build from your pull request (Show all checks -> Details). Once the snap build has completed, you can find the built snap (to test with) under "Artifacts".
6. Someone from the team will review the open pull request and either merge it or start a discussion with you with additional changes or clarification needed.
7. Once the pull request has been merged into the stable branch, a GitHub action will rebuild the snap using your changes and publish it to the [Snap Store](https://snapcraft.io/gimp) into the `candidate` channel. After sufficient testing of the snap from the candidate channel, one of the maintainers or administrators will promote the snap to the stable branch in the Snap Store.

## Maintainers

-   [@lucyllewy](https://github.com/lucyllewy/)

## License

-   The license of both the build files in this repository is [MIT](https://github.com/snapcrafters/gimp/blob/main/LICENSE)
