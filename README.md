

You can use the script to create a streaming site like what our team use few years back on [01nonton](https://satu.lol/01nonton)

Mount Gdrive to drive server
Install MongoDB.
```
apt-get install mongodb
```
find plexdrive latest version : https://github.com/dweidenfeld/plexdrive/releases (version amd64).
```
mkdir /disc2/plexdrive
cd /disc2/plexdrive
wget https://github.com/dweidenfeld/plexdrive/releases/download/4.0.0/plexdrive-linux-amd64
mv plexdrive-linux-amd64 plexdrive
chown root:root /disc2/plexdrive/plexdrive
chmod 755 /disc2/plexdrive/plexdrive
```
Now we are going to get our client id and client secret from the google API. To do this we do the following:
- Log in to the Google API Console. [Google API Console](https://console.developers.google.com/)
- create a new project.
- Go to Overview - Google APIs, Google Apps APIs, Drive API y Enable.
- Go to Credentials in the left panel and Create Credentials, OAuth client ID.
- In application type we select Other and Create.
- It will give us a client id and client secret. Copy it and save.


Install screen
```
apt-get install screen
screen -S plexdrive
mkdir /disc2/plexcloud
cd /disc2/plexdrive
./plexdrive -o allow_other -v 3 -m localhost /disc2/plexcloud
```



to exit screen : Control + A + D.
back to screen session : screen -r plexdrive



Usage of ./plexdrive mount:
  --cache-file string
    	Path of the cache file (default "~/.plexdrive/cache.bolt")
  --chunk-check-threads int
    	The number of threads to use for checking chunk existence (default 2)
  --chunk-load-ahead int
    	The number of chunks that should be read ahead (default 3)
  --chunk-load-threads int
    	The number of threads to use for downloading chunks (default 2)
  --chunk-size string
    	The size of each chunk that is downloaded (units: B, K, M, G) (default "10M")
  -c, --config string
    	The path to the configuration directory (default "~/.plexdrive")
  --drive-id string
    	The ID of the shared drive to mount (including team drives)
  -o, --fuse-options string
    	Fuse mount options (e.g. -fuse-options allow_other,...)
  --gid int
    	Set the mounts GID (-1 = default permissions) (default -1)
  --max-chunks int
    	The maximum number of chunks to be stored in memory (default 10)
  --refresh-interval duration
    	The time to wait till checking for changes (default 1m0s)
  --root-node-id string
    	The ID of the root node to mount (use this for only mount a sub directory) (default "root")
  --uid int
    	Set the mounts UID (-1 = default permissions) (default -1)
  --umask value
    	Override the default file permissions
  -v, --verbosity int
    	Set the log level (0 = error, 1 = warn, 2 = info, 3 = debug, 4 = trace)
  --version
    	Displays program's version information
      
      
      To Unmount fusermount -u ~/mountedfolder
