---
layout: post
title: How to play Wuthering Waves on Mac using PlayCover?
comments: true
---

[Wuthering waves](https://wutheringwaves.kurogames.com/en/main) is a new action based mobile game launched in May 2024. The mobile version was poorly optimized so that it feels like a different game compared to the PC version. Kuro Games announced there will be
Mac version, but did not provide a release date. However, this isn't the end of day since you can use PlayCover to run iOS apps
on Apple Silicon laptops.

<!--more-->

[Official YouTube channel](https://www.youtube.com/@WutheringWaves)

## Disclamer

Use at your own risk. Do NOT use automation tools or modify game data for cheating.

## 1. Installing PlayCover

You can download the latest version at [Download - PlayCover](https://playcover.io/download/). At the time of writing, I was using 3.0.0 Beta2. You can find the source code of PlayCover [here](https://github.com/PlayCover/PlayCover).

## 2. Download IPA

You'll need a decrypted IPA for the game which you can find at [Wuthering Waves - Decrypt IPA Store](https://decrypt.day/app/id6475033368).

Drag the downloaded IPA file into PlayCover app to install the game.

## 3. Change game setting

Open settings for the game and change Application Type to `public.app-category.games`.

![](https://d28as0x2ccoex4.cloudfront.net/2024/06/1da2a28123674d4f18abe4953e0d8630.png)

## 4. Remove folders and create symlinks

Run the game, when it says "Downloading launcher data", quit the game.

![](https://d28as0x2ccoex4.cloudfront.net/2024/06/518d9f357be43ce902a69de21edb9d7f.png)

After quiting, run the following command in terminal and restart the game.

```shell
rm -r /Users/$USER/Library/Containers/com.kurogame.wutheringwaves.global/Data/Library/Users/$USER/Library/Containers/com.kurogame.wutheringwaves.global/Data && ln -sf /Users/$USER/Library/Containers/com.kurogame.wutheringwaves.global/Data /Users/$USER/Library/Containers/com.kurogame.wutheringwaves.global/Data/Library/Users/$USER/Library/Containers/com.kurogame.wutheringwaves.global/Data
```

Here's [an explaination of the command](https://github.com/PlayCover/PlayCover/issues/1478#issuecomment-2122978287).

> Unreal Engine use file path from ConvertToIOSPath in their source code. They separated read path and write path.  
In iOS, these functions work well, but in MacOS they go like this.  
original path => '../../Content/Some_Content'  
read path '../../Content/Some_Content' => '/Users/<User>/Library/Containers/<App>/<Documents or Library>//Users/<User>/Library/Containers/<App>/<Documents or Library>/<Some Path>/Content/Some_Content'  
write path '../../Content/Some_Content' => '/Users/<User>/Library/Containers/<App>/<Documents or Library ( not same to read path )>//Users/<User>/Library/Containers/<App>/<Documents or Library (same to read path )>/<Some Path>/Content/Some_Content'

## 5. Import keymaps

You'll need to create a keymap in order to play the game smoothly. You can find some keymaps from [this GitHub issue](https://github.com/PlayCover/PlayCover/issues/1479). Here's what my keymap with XBox wireless controller looks like:

![](https://d28as0x2ccoex4.cloudfront.net/2024/06/8851fa3913fdc9656d14e78bf0eec846.png)

## 6. Enjoy

The game had a rough opening and did not live up to community's high expectation as a Genshin Impact competitor. Nevertheless,
I liked it's combat system.
