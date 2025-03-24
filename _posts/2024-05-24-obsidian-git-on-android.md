---
layout: post
title: Obsidian git on Android 14 (Samsung) 2024
comments: true
---

[Obsidian](https://obsidian.md) has paid official syncing system, but with it's open and vibrant community, there are various ways to sync your notes between multiple devices. This post demonstrates how I set up the [obsidian-git](https://github.com/denolehov/obsidian-git) plugin on my Samsung S23 and S25 Ultra phone with One UI 6 and 7 (Android 14).

<!--more-->

This guide:

- assumes you have basic familiarity with git
- does NOT require root access
- does NOT require Termux running in the background after the initial git clone.

## Install Termux to get shell and git on your Android phone

1. Download [F-Droid](https://f-droid.org/en/)
1. From F-Droid, download [Termux](https://f-droid.org/en/packages/com.termux/)
1. Open Termux, run `termux-change-repo`. Press the ↓ button and press spacebar to tick all repositories, then press enter to move to the next screen
1. Press ↓, then spacebar to tick the `Mirrors hosted by Albatross`, press enter
1. Run `pkg install git -y`
1. Run `termux-setup-storage`
   1. See [Termux-setup-storage - Termux Wiki](https://wiki.termux.com/wiki/Termux-setup-storage) for details

## Clone the Git repo from GitHub

1. Run `cd storage/shared` (If you get permissions issues, refer to [this page](https://wiki.termux.com/wiki/Termux-setup-storage))
1. Run `git clone <your repository>` and enter your login when prompted. You may need to create a [personal access token](https://github.com/settings/tokens) if you're using GitHub.
   1. You need to add the following permissions to the access token
        1. Repository: Your Notes/Obsidian repository
        1. Repository permission: **Metadata**: Read access
        1. Repository permission: **Code** and **commit** statuses: Read and write access

## Setup Obsidian and obsidian-git plugin

1. Install and open [Obsidian](https://play.google.com/store/apps/details?id=md.obsidian&hl=en_GB&gl=US)
1. Click "Open folder as vault", click on your phone name at the top to navigate to the top directory, and click on your git repository name. Then click "use this folder"
1. Install and enable the [obsidian-git](https://github.com/denolehov/obsidian-git) plugin
1. Enter your GitHub username and personal access token in the obsidian-git plugin settings

I purchased the [catalyst license](https://help.obsidian.md/Licenses+and+payment/Catalyst+license) to get the early access version and support Obsidian team's great work.

I followed these guides to get things setup originally:

- [Tutorial for automatically syncing an Obsidian vault with Git on an Android device · GitHub](https://gist.github.com/Makeshift/43c7ecb3f1c28a623ea4386552712114)
- [Obsidian + Android + Syncing via GitHub in 2023](https://www.reddit.com/r/ObsidianMD/comments/17odzjb/obsidian_android_syncing_via_github_in_2023/)

## Limitations

Due to the git implementation used by Obsidian-git plugin, you might encounter [Performance issues on mobile](https://github.com/denolehov/obsidian-git?tab=readme-ov-file#performance-on-mobile). I did not notice any issue yet with my S23 Ultra and small knowledge base.

## Additional syncing methods

- [Ofifcial Obsidian Sync](https://obsidian.md/sync)
- [GitHub - vrtmrz/obsidian-livesync](https://github.com/vrtmrz/obsidian-livesync?tab=readme-ov-file)
- [Obsync: A Two-Way Obsidian Sync · GitHub](https://gist.github.com/rahaaatul/267fb390d244deeccf776ed6c9414a4e)
- [Syncthing](https://syncthing.net)
