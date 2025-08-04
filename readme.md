# IPhone Mirroring Loop
1. **Save the Script**
    - Place the Python script where you want (e.g. `/usr/local/bin/update_plist.py`).

2. **Find Python Path**
    - Use `which python3` to get the absolute path to your Python 3 interpreter.

3. **Create LaunchDaemon**
    - Save the LaunchDaemon plist (e.g. `/Library/LaunchDaemons/plistchecker.plist`).
    - In ProgramArguments, put the full path to `python3` and your script.

4. **Load at Boot**
    - Run `sudo launchctl load /Library/LaunchDaemons/plistchecker.plist` to enable autostart as root.

**Done!**  
Your script now checks/updates the plist automatically in the background with the required permissions.
