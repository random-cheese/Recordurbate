# Recordurbate

## Important
This is fork of `oliverjrose99/Recordurbate`  

## Differences(TODO)
1. Docker Suppoert (working on it)     
	and then put the docker image on Docker Hub or somethere else public.
2. Better file support       
	you won't get a bunch of `.mp4.part` file, and when you try to change the name from `.mp4.part` to `.mp4` to make it playable, sometime it work sometime it doesn't. we need to make it work 100% of time.      
3. Bug fixed (run `python3 ./Recordurbate.py stop` would just hang there sometimes)


## Requirements
* Linux
* Python 3+ (requests)
* Youtube-dl
* FFmpeg
## Installation
The default config files will work out of the box with youtube-dl and FFmpeg installed. Streams will be saved to the folder videos/\<name>/\<name> \<date> \<hour>_\<min>.mp4. This can be changed by editing the youtube-dl.config file, see the configuration section for more. 
## Usage

View the usage/help text
```
./Recordurbate help
```

Add or remove a streamer to record
```
./Recordurbate.py [add | del] username
```

Start, stop or restart the daemon
```
./Recordurbate.py [start | stop | restart]
```

List the streamers in the config
```
./Recordurbate list
```

Import streamers from a file
```
./Recordurbate import [file]
```

Export streamers to a file. The file parameter is optional and the default location will be used if not passed
```
./Recordurbate.py export [file]
```

## Config Files
There are two main config files that are used, `config.json` and `youtube-dl.config`, both being stored in the configs directory. In that directory is also the log file (rb.log) and the pid file (rb.pid).

### Config.json
This file is used directly by Recordurbate and contains all the configuration options as well as the array of streamers to record.

`youtube-dl_cmd` - Sets the command used to run Youtube-dl. 

`youtube-dl_config` - Sets where the config file for Youtube-dl is located and is passed with the `--config-location` parameter. Note that system and user wide configs still apply, see [this link](https://github.com/ytdl-org/youtube-dl#configuration) for more info.

`auto_reload_config` - Sets if the bot should reload the config after every loop to allow adding or removing streamers while running.

`rate_limit` - Sets whether or not the API calls should be rate limited.

`rate_limit_time` - The time in seconds to wait between API calls, only waits if `rate_limit` is true.

`default_export_location` - Sets the default location for the export command.

`streamers` - An array of strings, each of which is a streamer to record.

### Youtube-dl.config
This file is used to set all of the Youtube-dl config options and is passed using the `--config-location` parameter. As mentioned, the system and user wide configs still apply. Options such as quality, export options and more can be [found on the Youtube-dl Github.](https://github.com/ytdl-org/youtube-dl)

# Commit as difference user (random-cheese)
```
sudo chmod 600 $HOME/.ssh/random-cheese-github.pub

git add -A
git -c user.name='random-cheese' -c user.email=temp.throwaway365@gmail.com commit -m "commit message"
GIT_SSH_COMMAND='ssh -i $HOME/.ssh/random-cheese-github -o IdentitiesOnly=yes -F /dev/null' git push origin
```