Extracting musical information from sound
=========================================

**Presenter:** Adrian Holovaty

**Track:** III

**Description:**

    Music Information Retrieval technology has gotten good enough that you extract musical metadata from your sound files with some degree of accuracy. Find out how to use Python (along with third-party APIs) to determine everything from the key/tempo of a song to the pitch/timbre of individual notes. Then we'll do some amusing analysis of popular tunes.

    https://us.pycon.org/2012/schedule/presentation/6/

What does it mean?
++++++++++++++++++

* taking an audio file (bits and bytes) and turning it into musical information (notes)
* use python to take an mp3 and extract musical information from it
* Adrian spends a ton of free time trying to figure out songs on his guitar
* Would be awesome if we could do this automatically

What are we going to use?
+++++++++++++++++++++++++

* Using python and echonest (free api, I think)
* Using tip toe through the tulips as the example song; a solo guitar piece

Getting Basic Information
+++++++++++++++++++++++++

* pip install pyechonest
* get api key from developer.echonest.com
* import stuff and use track_from_file from echonest
* Lots of stuff available about the track by using that function
    * beats, sample rate, encoding quality, tempo, key
* get confidence numbers on the returned values
* sections tell you when the song is changing
    * not perfect, but close
* Tatums (the lowest regular pulse of the music)
* Segments ("relatively uniform" pieces of the sound)
    * In practice, every note or drum beat
    * This is awesome, love it (my comment)
    * Loudness (in decibles) - part of a segment
    * Pitches - can almost extract the notes from this
        * good start for automated music transcription
    * Timbre - not sure exactly what this means or represents (the color of sound)
        * loudness, flatness, attack, brightness

What can we do with this?
+++++++++++++++++++++++++

* HacKey - shows what keys your songs are in from your last.fm profile
* The Loudness War (Paul Lamere)
* Click track detection (labs.echonest.com/click)
    * Django Reinhardt (a jazz musican named after a programming framework)
* LOL, nickelback (Nickelback to Bickelnack)
* moreCowbell.dj
* Swinger and the Deswinger

