# Reverse's Raid Mode

Reverse's Raid Mode is a lightweight Windows app for WoW raiders. I built it to bench the apps that eat into the resources WoW could use or pull my attention off the fight. With my usual apps running, I saw up to 40% fewer running Windows processes on my PC. That's a process count, not a benchmark or a promise about FPS.

## What it does

- The App Roster groups foreground apps, background processes and related helpers. You can see the proposed close list before you start. WoW and Discord start **Rostered**. **Benched** apps can be closed if eligible, and **Flex** apps stay open unless you enable closing them.
- An active session checks running processes about every three seconds by default. It can close eligible Benched apps again if they relaunch. This is a check after launch, not a Windows application block.
- Core Windows components are protected. The app may report matching Windows services in the scan, but does not stop or disable them. If startup pausing is enabled, only reviewed, matching sources that pass the app's checks can be paused.
- **End session** stops the checks and restores the startup entries it paused, or reports any restoration conflict. You can choose to reopen eligible desktop apps that closed at the start of the raid. Supported apps may bring back their own saved sessions.
- Roster and return rules are saved locally at `%LOCALAPPDATA%\RaidModeRaiders\whitelist.json`. They aren't synchronized to a Microsoft account or bundled in the ZIP.

## Review the Raiders test build

The package is **Raiders 0.15.0**, Windows file version **0.15.0.1**, with the revised arrow R. It is an unsigned x64 Windows test build. The release ZIP contains only the EXE and the quick start guide. [Download the reviewed Raiders ZIP](https://github.com/SymbiSynth/reverse-raid-mode/releases/tag/v0.15.0-raiders). The WinForms header and Windows icon were checked on this exact executable. The 54-check Raiders regression run applies to the previous build.

1. Extract the ZIP and open the EXE as your normal Windows user.
2. Use **Scan & preview** to review the close list, including background apps. Set anything you need to keep to Rostered.
3. Save your work before approving a session. An eligible app that starts after activation can be force-closed. The app cannot restore unsaved work.
4. Use **End session** when you’re done. If Windows was interrupted while startup entries were paused, use **Recover session** before starting another raid.

See the [quick start guide](Raiders-quick-start.txt) for the app controls and [technical addendum](Reverse%20Raid%20Mode%20Technical%20Addendum.pdf) for the implementation, Windows operations, recovery rules and test limits. The application does not automate gameplay. No Blizzard or guild endorsement is implied.

## Source and build

The [source snapshot](Reverse-Raid-Mode-Source.zip) includes the C# WinForms project, tests, and build script. On Windows, `build.ps1 -Raiders` selects the Raiders edition; `-Tests` also compiles the fixture runner. The release download is the original verified ZIP. A build from source is a separate artifact.

## Feedback

Include the build, the app you tested, the rule you picked and what happened. If you tried an **After raid** option, say which one. For a performance report, compare before and after with the same apps running. Keep account names, local paths with personal details and raw startup commands out of feedback screenshots or logs.
