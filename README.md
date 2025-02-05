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
snap install gimp --channel preview/stable
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

## OpenVINO™ AI Plugins

> [!IMPORTANT]
> These plugins are only supported on Intel hardware. The stable diffusion plugin requires an Intel GPU (integrated or discrete) and/or Intel NPU. The super resolution and semantic segmentation plugins will run on an Intel CPU, GPU, or NPU.

This snap contains support for AI plugins using Intel's OpenVINO AI inference library. In order to use these plugins, please follow these steps:


1. **Install the plugins and their dependencies**:

    ```shell
    sudo snap install intel-npu-driver --beta # for NPU support
    sudo snap install openvino-toolkit-2404 --beta
    sudo snap install openvino-ai-plugins-gimp --beta
    ```

2. **(Optional) Enable Intel NPU and GPU acceleration**:

    If you are running on a machine (e.g. a laptop or desktop containing an Intel Core Ultra processor) equipped with an Intel neural processing unit (NPU) or graphics processing unit (GPU), ensure you have permissions to use these devices by adding yourself to the `render` Unix group:

    ```shell
    sudo usermod -a -G render $USER
    ```

    You need to log out and log back for this change to take effect.

    Next, ensure that the devices have read and write permissions set on the group level:

    ```shell
    sudo chown root:render /dev/accel/accel*
    sudo chmod g+rw /dev/accel/accel*
    sudo chown root:render /dev/dri/render*
    sudo chmod g+rw /dev/dri/render*
    ```

3. **(Optional) Install stable diffusion models**:

    Models for the super resolution and semantic segmentation plugins are relatively small and therefore built into the snap, while the stable diffusion models are each on the order of GBs and therefore downloaded to a user's home directory at `~/.local/share/openvino-ai-plugins-gimp` via one of two methods: a `model-setup` command-line tool or from within the GIMP application. To run the interactive command-line tool:

    ```shell
    openvino-ai-plugins-gimp.model-setup
    ```

    Alternatively, users may download models from within GIMP by clicking "Model" in the top-left of the stable diffusion dialog window (Layer -> OpenVINO-AI-Plugins -> Stable Diffusion).

4. **Run `gimp` like normal**:

    Instructions for using the OpenVINO AI plugins within GIMP can be found in the [upstream GitHub repo](https://github.com/intel/openvino-ai-plugins-gimp).

## Maintainers

-   [@lucyllewy](https://github.com/lucyllewy/)

## License

-   The license of both the build files in this repository is [MIT](https://github.com/snapcrafters/gimp/blob/main/LICENSE)
