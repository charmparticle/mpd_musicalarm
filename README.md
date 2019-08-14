# mpd_musicalarm
A simple shellscript which serves as a music alarm. It uses mpd and mpc. Invoke it with cron or anacron or whatever it is the kids are using these days, testing first, of course.

modify $MAXVOL, $MUSICDIR, $WAKEUPSONGS and $WAKEUPRADIO to your needs, by creating a config file in `~/.config/mpd_musicalarm/config` with values set up separated by an equals sign only. Consult the example file to make your own.

It's pretty easy to create a playlist using ncmpcpp by hitting the 'a' key and choosing a new playlist, or using mpc save, after adding songs or albums. Once the playlist is created, it should reside in `~/.config/mpd/playlists` if you've configured it to run under your user, otherwise, it is probably in `/var/lib/mpd/playlists`. 

An interesting thing I learned while making this script: mpd will *not* set any volume level until music has been added to the main playlist, and played. I picture this like mpd is some surly guy. You tell him to add some music to the cd player, and say, "hey, man - could you make sure the volume isn't too high", and he replies "what are you even talking about? There isn't any music playing!". So, yeah; this is a problem if you want mpd to be a music alarm, with the music fading in, since it will initally play at the last volume you used. My workaround for this was to create a silent mp3 file, add that, play it, change the volume to 0, and add the $WAKEUPSONGS or $WAKEUPRADIO playlist.

One other problem that bugged me for awhile was how to figure out if an internet radio stream is valid. I found a solution, which involves the use of ffprobe, so you'll need to install that if you want to be able to set your internet radio stream of choice in the config file.

*DEPENDENCIES*

mpd, mpc, ffmpeg
