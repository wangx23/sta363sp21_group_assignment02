# What makes a song popular?

In this group assignment we will be working with data obtained from Spotify through the Spotify developers API. 

Our ultimate goal is to build statistical models to determine what makes a song popular, and to build models to predict popularity of songs.

## Structure of the assignment

This group assignment is being segmented into two parts. 

### Part 1 - Data Processing and EDA

In this part of the assignment you will work on some data handling and model building for explanation.

### Part 2 - Modeling for Predicting

In the second part of the assigment (will be made available next week), you will perform a validation study on several models and determine a model that works well for predicting popularity. You will use that model to predict the popularity score for a set of songs not included in the initial data.

## Data

All data needed for part 1 of the assigment is available in the file `spr21_spotifyData.RData`. The `RData` contains five datasets and can be inported into R with the `load()` function. The datasets included are

* `artist_df` -- A data.frame containing the names, and Spotify IDs for 389 artist.  These artist were selected based on having a popular song sometime over the past 5 years on the Pop Music, Rock Music or Country charts.
* `album_artist_df` -- A data.frame mapping the artist (and their Spotify IDs) to all their recorded studio albums, including the album name, its Spotify ID, its type (album or single) and its release date (either a date or a year).
* `tracks_df` -- A data.frame with 72156 rows recording a track (i.e., song) name, Spotify track ID, an indicator determining if the song includes *explicit lyrics* and the Spotify **popularity** score.
* `album_track_df` -- A data.frame with 72156 rows but only two columns mapping all Spotify track IDs with their correspond Spotify album IDs.
* `track_features` -- A data.frame with 72143 rows record track IDs along with a series of audio *features* as reported by Spotify. This includes
   + duration_ms - the duration of the track in (milliseconds)
   + time_signature - The time signature for the track (common time is 4)
   + danceability - Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable
   + energy - Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy.
   + key - The key the track is in. Integers map to pitches using standard Pitch Class notation; see https://en.wikipedia.org/wiki/Pitch_class
   + loudness - The overall loudness of a track in decibels (dB). Loudness values are averaged across the entire track and are useful for comparing relative loudness of tracks. 
   + mode - Mode indicates the modality (major or minor) of a track, the type of scale from which its melodic content is derived. Major is represented by 1 and minor is 0.
   + speechiness - Speechiness detects the presence of spoken words in a track. The more exclusively speech-like the recording (e.g. talk show, audio book, poetry), the closer to 1.0 the attribute value.
   + acousticness - A confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.
   + instrumentalness - Predicts whether a track contains no vocals. “Ooh” and “aah” sounds are treated as instrumental in this context. Rap or spoken word tracks are clearly “vocal”. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content.
   + livenss - Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live.
   + valence - A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).
   + tempo - The overall estimated tempo of a track in beats per minute (BPM). In musical terminology, tempo is the speed or pace of a given piece and derives directly from the average beat duration.
