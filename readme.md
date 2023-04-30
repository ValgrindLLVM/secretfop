<div align="center">
  <h1>secretfop 🦊✨</h1>
  <p>Bot that fetches and shares social media images on Telegram from Twitter or VKontakte</p>
  <b>work in progress</b>
  <!-- fun fact: this readme fully generated by ChatGPT -->
</div>

## Project Status

This project is currently in development and is not yet fully functional. The bot can
fetch and post images from VKontakte, but support for Twitter is still in progress. I
am working on implementing this feature and hope to have it ready soon. If you encounter
any issues or have suggestions for improving the bot, please feel free to open an issue or
submit a pull request. Thank you for your interest in our project!

## Building

This bot is written in Rust, so you will need `rustc` and `cargo` version 1.65 or greater
to build it. Here's how to build the bot in release mode:

```console
$ cargo build --release
```

This will create an executable file in `target/release/secretfop`. You can then run the bot with:

```console
$ ./target/release/secretfop
```

If you prefer, you can also download pre-built binaries from the
[Releases page](https://github.com/ValgrindLLVM/secretfop/releases) on GitHub.
Simply download the appropriate binary for your operating system and architecture, and then
run it with:

```console
$ ./secretfop
```

Note that pre-built binaries may not always be available for the latest version of the bot.
If you want to ensure that you have the most up-to-date version, you should build the bot
from source.

## Usage

This bot is designed to fetch images from social media accounts and post them to a Telegram
channel. Here are the available options for running the bot:

- `--populate`: This flag populates the cache of image IDs and exits without posting any
images to Telegram. This can be useful for the first run, when the cache is empty and
there are many images to fetch.
- `--cache <filename>`: This option specifies the name of the cache file to use. By default,
the cache file is named `.cache.secretfop.json`.
- `--config <filename>`: This option specifies the name of the configuration file to use.
By default, the configuration file is named `secretfop.yml`.

You can also use `crontab` to schedule the bot to run at specific times. For example,
to run the bot every hour, you could add the following line to your crontab file:

```crontab
*/3 * * * * /path/to/secretfop
```

This will run the bot every 3 minutes, fetching and posting any new images to the Telegram
channel.

Note that the bot will exit after posting any new images to Telegram. To keep the bot
running continuously, you will need to use a job scheduler like `systemd-timer` or `crontab`.

## Configuration

This bot uses a configuration file named `.secretfop.yml` to store its API tokens and
channel IDs. Here is the structure of the configuration file:

```yaml
vk_token: [vk user token]
twitter_token: [twitter app-only token]
telegram_token: [telegram bot token]
telegram_channel: [telegram channel id or @username]
twitter:
    - id: [id, required]
      name: [account name, optional, not used]
      url: [account url. optional, not used]
vk: [same as twitter]
```

You should replace the placeholders in square brackets with your own tokens and IDs.
Here is a brief explanation of each field:

- `vk_token`: Your VKontakte user token, which you can obtain from the VKontakte
Developers website.
- `twitter_token`: Your Twitter app-only token, which you can obtain from the Twitter
Developers website.
- `telegram_token`: Your Telegram bot token, which you can obtain by creating a new bot
with the BotFather.
- `telegram_channel`: The ID or @username of the Telegram channel where you want the
bot to post the images.
- `twitter`: A list of Twitter accounts that the bot should fetch images from. Each
account should have an `id` field, which is the Twitter user ID of the account.
- `vk`: A list of VKontakte accounts that the bot should fetch images from. Each account
should have an `id` field, which is the VKontakte user ID of the account.

You can add more Twitter and VKontakte accounts to the `twitter` and `vk` lists,
respectively, by copying the `- id` block and filling in the appropriate information.

## Limitations

This bot has some limitations that you should be aware of:

- **No video support for VKontakte**: Currently, the bot can only fetch and post images
from VKontakte. Videos are not supported.
- **No Twitter support**: At the moment, the bot does not support fetching or posting
images from Twitter. This feature may be added in a future update.
- **Not designed to run continuously**: This bot is designed to be run periodically using
a tool like `crontab`. It is not intended to be run continuously or as a daemon.

We are working to address these limitations in future releases of the bot. If you encounter
any issues or have any feature requests, please feel free to open an issue on the GitHub
repository.

