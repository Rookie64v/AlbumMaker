# AlbumMaker
ffmpeg-based mp3 converter and track splitter

Compatible Operating Systems:
Linux (anything with bash or a bash-like shell)

Dependencies:
ffmpeg

Usage:
make_album -i "audio_file" [--artist "artist_name"] [--album "album_name"] [--year "release_year"]\
[-t "track1_title" "track2_title" ... "last_track_title"] [-s "track2_timestamp" "track3_timestamp" ... "last_track_timestamp"]

make_album converts any "audio_file" recognized by ffmpeg to mp3, then splits it in N+1 tracks (N being the number of provided timestamps, each timestamp marking separation between tracks; timestamps need to be in ascending order as of current release). Each track is assigned a title (specified by -t option in order of track number): if any is missing a name with format "track_i" is used. All tracks are assigned id3 tags, version 2.3, for easier recognition by "dumb" players like car media systems and old mp3 players.

Got the recording of a conference and want to split it in different interventions, or maybe a do-it-yourself concert recording with your band? Let the tool do the job and avoid tedious tag manipulation!

Examples:
make_album -i IEEE_conference_dummy_names --album IEEE_conf_2017 --year 2017\
-t "Inspiration and idiocy - Fundamentals of variable naming" "SuperFoo" "Bar Evolution" -i 10:35 15:43

make_album -i "kid concert" --year 2017 --artist "Little Billy" -t "That was bad" "It cannot get worse" "I was wrong"\
please_get_ear_protection -s 3:40 8:27 10:53
