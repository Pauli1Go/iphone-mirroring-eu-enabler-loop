# IPhone Mirroring Loop

1. **Save the Script**
   - Place the Python script where you want (e.g. `/usr/local/bin/check_and_update_plist.py`).

2. **Find Python Path**
   - Use `which python3` to get the absolute path to your Python 3 interpreter.

3. **Create LaunchAgent**
   - Save the LaunchAgent plist (e.g. `~/Library/LaunchAgents/plistchecker.plist`).
   - In ProgramArguments, put the full path to `python3` and your script.

4. **Load at Login**
   - Run `launchctl load ~/Library/LaunchAgents/plistchecker.plist` to enable autostart.

**Done!** Your script now checks/updates the plist automatically in the background. And you should be able to start the IPhone mirroring from your dock.
