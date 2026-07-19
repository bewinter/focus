<p align="center">
   <img src="https://ik.imagekit.io/turnupdev/focus-new-logo_Sy07sN3gG.png" width="300" height="300" alt="Focus logo">
</p>

<p align="center">
   <a href="http://makeapullrequest.com"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat" alt=""></a>
   <a href="https://github.com/ayoisaiah/focus/actions"><img src="https://github.com/ayoisaiah/focus/actions/workflows/test.yml/badge.svg" alt="Github Actions"></a>
   <a href="https://golang.org"><img src="https://img.shields.io/badge/Made%20with-Go-1f425f.svg" alt="made-with-Go"></a>
   <a href="https://goreportcard.com/report/github.com/ayoisaiah/focus"><img src="https://goreportcard.com/badge/github.com/ayoisaiah/focus" alt="GoReportCard"></a>
   <a href="https://github.com/ayoisaiah/focus"><img src="https://img.shields.io/github/go-mod/go-version/ayoisaiah/focus.svg" alt="Go.mod version"></a>
   <a href="https://github.com/ayoisaiah/focus/blob/master/LICENCE"><img src="https://img.shields.io/github/license/ayoisaiah/focus.svg" alt="LICENCE"></a>
   <a href="https://github.com/ayoisaiah/focus/releases/"><img src="https://img.shields.io/github/release/ayoisaiah/focus.svg" alt="Latest release"></a>
</p>

<h1 align="center">Focus on your task</h1>

Focus is a cross-platform productivity timer for the command line. It is based
on the [Pomodoro Technique](https://en.wikipedia.org/wiki/Pomodoro_Technique), a
time management method developed by Francesco Cirillo in the late 1980s.

## 🍅 How it works

1. Pick a task you need to accomplish.
2. Set a timer for 25 minutes and start working without interruptions.
3. When the timer rings, take a short break for 5 minutes.
4. Once you've completed four work sessions, you can take a longer 15 minute
   break.

## ✨ Main features

- Work and break session lengths are customisable.
- You can pause and resume work sessions.
- You can skip break sessions.
- You can customise the number of sessions before a long break.
- You can set a maximum number of sessions.
- Desktop notifications are supported on all platforms.
- You can customise the notification messages.
- Detailed statistics for your work history are provided including charts.
- Focus provides six built-in ambient sounds that you can play during a session,
  and you can add your own custom sounds.

## 💻 Screenshots

![Focus first run](https://ik.imagekit.io/turnupdev/focus-screenshot_6BU22Sj-J.png)

![Focus statistics](https://ik.imagekit.io/turnupdev/focus-stats-screenshot_0dLtjklu_0.png)

![Focus](https://ik.imagekit.io/turnupdev/focus-ops_bcJ7-Gnuag.png)

## ⚡ Installation

Focus is written in Go, so you can install it through `go install` (requires Go
1.16 or later):

```bash
go install github.com/ayoisaiah/focus/cmd/focus@latest
```

On Linux, the `libasound2-dev` package is required to compile Focus. Ubuntu or
Debian users can install it through the command below:

```bash
sudo apt install libasound2-dev
```

Other installation methods are
[available here](https://github.com/ayoisaiah/focus/wiki/Installation/).

## 🚀 Usage

Once Focus is installed, run it using the command below:

```
focus
```

**Note:** Only one instance of `focus` can be active at a time.

## ⚙ Configuration

When you run Focus for the first time, it will prompt you to set your preferred
timer lengths, and how many sessions before a long break. Afterwards, you may
change these values by using command-line options or editing the `config.yml`
file which will be located in `~/.config/focus/` on Linux,
`%LOCALAPPDATA%\focus` on Windows, and `~/Library/Application Support/focus` on
macOS.

Here's the default configuration settings:

```yml
work:
  duration: 25m # work session length
  message: Focus on your task # shown in the terminal and notification
  sound: loud_bell # notification sound

short_break:
  duration: 5m # short break length
  message: Take a breather # shown in the terminal and notification
  sound: bell # notification sound

long_break:
  duration: 15m # long break length
  message: Take a long break # shown in the terminal and notification
  sound: bell # notification sound

settings:
  ambient_sound: "" # name of ambient sound to play
  auto_start_break: true # automatically start the next break session
  auto_start_work: false # automatically start the next work session
  cmd: "" # execute an arbitrary command after each session
  long_break_interval: 4 # work sessions before a long break
  sound_on_break: false # play ambient sound during break sessions
  strict: false # prevent resuming a paused work session

display:
  dark_theme: true # use colours befitting a dark background

notifications:
  enabled: true # show desktop notifications
```

If you specify a command-line argument while running focus, it will override the
corresponding value in the config file.

## ⏳ Sessions

Focus has 3 types of sessions: work, short break, and long break.

### 💼 Work sessions

- Set to 25 minutes length by default. Use the `--work` or `-w` option to change
  the length, or change `work.duration` in the `config.yml` file.
- Message displayed in the terminal and desktop notification can be changed
  using `work.message`.
- You can pause a work session by pressing `Ctrl-C`. Use `focus resume` to
  continue from where you stopped.
- The `focus resume` command supports the `--sound`, `--sound-on-break`, and
  `--disable-notification` flags.
- If `settings.auto_start_work` is `false`, you will be prompted to start each
  work session manually. Otherwise if set to `true`, it will start without your
  intervention.
- The maximum number of work sessions can be set using the `--max-sessions` or
  `-max` option. After that number is reached, focus will exit.
- Use the `--long-break-interval` or `-int` option to set the number of work
  sessions before a long break, or change `settings.long_break_interval` in your
  `config.yml`.

### 😎 Break sessions

- Short break is 5 minutes by default. Use the `--short-break` or `-s` option to
  change the length, or set `short_break.duration` in the `config.yml` file.
- Long break is 15 minutes by default. Use the `--long-break` or `-l` option to
  change the length, or set `long_break.duration` in the `config.yml` file.
- Message displayed in the terminal and desktop notification can be changed
  using `short_break.message` and `long_break.message`.
- Pressing `Ctrl-C` during a break session will interrupt it. Run `focus resume`
  to skip to the next work session.
- If `settings.auto_start_break` is `false`, you will be prompted to start each
  break session manually. Otherwise if set to `true`, it will start without your
  intervention.

## Tagging sessions

You can use the `--tag` or `-t` flag to apply a tag to a new session:

```bash
focus --tag 'side-project'
```

Multiple tags are supported (use commas to separate each):

```bash
focus --tag 'side-project,focus'
```

## 🔔 Notifications

![Focus notification](https://ik.imagekit.io/turnupdev/focus-notify_igz_8z0Jnp.png)

Notifications are turned on by default. Set `notifications.enabled` to `false`
in your config file, or use the `--disable-notification` flag if you don't want
notifications once a session ends.

## 🔊 Ambient sounds

Focus provides six ambient sounds by default: `coffee_shop`, `playground`,
`wind`, `rain`, `summer_night`, and `fireplace`. You can play a sound using the
`--sound` option, or set a default sound in your config file through the
`settings.ambient_sound` key.

```bash
focus --sound 'coffee_shop'
```

If you want to play a custom sound instead, copy the file (supports MP3, FLAC,
OGG, and WAV) to the appropriate directory for your operating system:

- **Linux**: `~/.local/share/focus/static`
- **Windows**: `%LOCALAPPDATA\focus\static`
- **macOS**: `~/Library/Application Support/focus/static`

Afterwards, specify the name of the file in the `settings.ambient_sound` key or
`--sound` option. **Note that custom sounds must include the file extension**.

```bash
focus --sound 'university.mp3'
focus --sound 'subway.ogg'
focus --sound 'airplane.wav'
focus --sound 'stadium_noise.flac'
```

By default, ambient sounds are played only during work sessions. They are paused
during break sessions, and resumed again in the next work session. If you'd like
to retain the ambient sound during a break session, set
`settings.sound_on_break` to `true`, or use the `--sound-on-break` or `-sob`
flag.

You can also disable sounds when starting or resuming a session by setting
`--sound` to `off`:

```bash
focus --sound 'off'
focus resume --sound 'off'
```

## 📈 Statistics & History

```bash
focus stats
```

The above command will display your work history for the last 7 days by default.
You'll see how many work sessions you completed, how many you abandoned, and how
long you focused for overall. It also displays a break down by week, and hour to
let you know what times you tend to be productive.

You can change the reporting period through the `--period` or `-p` option. It
accepts the following values: _today_, _yesterday_, _7days_, _14days_, _30days_,
_90days_, _180days_, _365days_, _all-time_.

```bash
focus stats -p 'today'
focus stats -p 'all-time'
```

You can also set a specific time period using the `--start` and `--end` options.
The latter defaults to the current day if not specified. See the list of
acceptable formats in the
[project wiki](https://github.com/ayoisaiah/focus/wiki/Acceptable-datetime-formats-for-filtering).

```bash
focus stats --start '2021-08-06'
focus stats --start '2021-08-06' --end '2021-08-07'
focus stats --start '2021-07-23 12:00:05 PM' --end '2021-07-29 03:25:00 AM'
```

### 📃 Listing sessions

Use the `list` command to display a table of your work sessions instead of
aggregated statistics. Use the `--period` or `--start` and `--end` option to
change the reporting period (defaults to the last 7 days).

```bash
focus list
```

```text
┌──────────────────────────────────────────────────────────────────────────────┐
| # | START DATE            | END DATE              | TAGGED       | STATUS    |
| 1 | Feb 21, 2023 09:09 PM | Feb 21, 2023 09:09 PM |              | abandoned |
| 2 | Feb 21, 2023 09:11 PM | Feb 21, 2023 09:11 PM |              | abandoned |
| 3 | Feb 21, 2023 09:15 PM | Feb 21, 2023 09:15 PM | reading      | abandoned |
| 4 | Feb 21, 2023 09:15 PM | Feb 21, 2023 09:16 PM | side-project | completed |
| 5 | Feb 21, 2023 09:16 PM | Feb 21, 2023 09:17 PM | writing      | completed |
| 6 | Feb 21, 2023 09:21 PM | Feb 21, 2023 09:22 PM | writing      | completed |
| 7 | Feb 21, 2023 09:22 PM | Feb 21, 2023 09:23 PM | writing      | completed |
└──────────────────────────────────────────────────────────────────────────────┘
```

You can filter the list by tag:

```bash
focus list --tag 'client,piano'
```

```text
┌──────────────────────────────────────────────────────────────────────────────┐
| # | START DATE            | END DATE              | TAGGED       | STATUS    |
| 1 | Feb 21, 2023 09:15 PM | Feb 21, 2023 09:15 PM | reading      | abandoned |
| 2 | Feb 21, 2023 09:15 PM | Feb 21, 2023 09:16 PM | side-project | completed |
└──────────────────────────────────────────────────────────────────────────────┘
```

**Note:**

- Sessions that cross over to a new day will count towards that day's sessions.
- A session with an empty end date indicates that the process was ended such a
  way that a graceful shutdown was not possible.

### ✒ Editing sessions

You can edit the tags of one or more sessions through the `edit-tag` command. It
accepts the same options as the `list` command to select the sessions to be
edited. The tags are command-line arguments. You will be prompted before the
update is carried out.

The command below edits the tags of all sessions recorded `today` and tagged
with `writing`. It updates the tags for each session to writing, novel, and
`once-upon-a-time`.

```bash
focus edit-tag --tag 'writing' -p 'today' 'writing' 'novel' 'once-upon-a-time'
```

```text
┌────────────────────────────────────────────────────────────────────────────────────────────────────┐
| # | START DATE            | END DATE              | TAGGED                             | STATUS    |
| 1 | Feb 21, 2023 09:16 PM | Feb 21, 2023 09:17 PM | writing · novel · once-upon-a-time | completed |
| 2 | Feb 21, 2023 09:21 PM | Feb 21, 2023 09:22 PM | writing · novel · once-upon-a-time | completed |
| 3 | Feb 21, 2023 09:22 PM | Feb 21, 2023 09:23 PM | writing · novel · once-upon-a-time | completed |
└────────────────────────────────────────────────────────────────────────────────────────────────────┘
 WARNING  The sessions above will be updated. Press ENTER to proceed
```

### 🔥 Deleting sessions

Deleting sessions is done in the same way as `list` except that `delete` is used
instead. You will be prompted to confirm the deletion before it is carried out.

```bash
focus delete --start '2023-02-21 21:21:00'
```

```text
┌─────────────────────────────────────────────────────────────────────────┐
| # | START DATE            | END DATE              | TAGGED  | STATUS    |
| 1 | Feb 21, 2023 09:22 PM | Feb 21, 2023 09:23 PM | writing | completed |
| 2 | Feb 21, 2023 09:33 PM | Feb 21, 2023 09:33 PM |         | abandoned |
└─────────────────────────────────────────────────────────────────────────┘
 WARNING  The above sessions will be deleted permanently. Press ENTER to proceed
```

## 🤝 Contribute

Bug reports and feature requests are much welcome! Please open an issue before
creating a pull request.

## ⚖ Licence

Created by Ayooluwa Isaiah, and released under the terms of the
[MIT Licence](http://opensource.org/licenses/MIT).
