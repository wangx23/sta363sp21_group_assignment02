# What makes a song popular?

In this group assignment we will be working with data obtained from Spotify through the Spotify developers API. 

Our ultimate goal is to build statistical models to determine what makes a song popular, and to build models to predict popularity of songs.

## Structure of the assignment

This group assignment is being segmented into two parts. 

### Part 1 - Data Processing and EDA

In this part of the assignment you will work on some data handling and model building for explanation.

### Part 2 - Modeling for Predicting

In the second part of the assigment (will be made available next week), you will perform a validation study on several models and determine a model that works well for predicting popularity. You will use that model to predict the popularity score for a set of songs not included in the initial data.

### Working as a group

This assignment is general structured that it builds on itself. That is, performing the data processing in Question 1 should help the data processing in later parts. Several of the earlier questions provide insight that should be helpful when building your regression model.  Therefore, it is HIGHLY RECOMMENDED that you DO NOT adapt the divide-and-conquer strategy many teams used on the first assignment (Alice does #1, Bob does #2, Carol does #3, and so on). Not only would this be an unfair distribution of workload, but it may delay completion of the assignment.

## Data

All data needed for part 1 of the assigment is available in the file `spr21_spotifyData.RData`. The `RData` contains five datasets and can be inported into R with the `load()` function. The datasets included are

* `artist_df` -- A data.frame containing the names, and Spotify IDs for 389 artist.  These artist were selected based on having a popular song sometime over the past 5 years on the Pop Music, Rock Music or Country charts.
* `album_artist_df` -- A data.frame mapping the artist (and their Spotify IDs) to all their recorded studio albums, including the album name, its Spotify ID, its type (album, compilation or single) and its release date (either a date or a year).
* `tracks_df` -- A data.frame with 72156 rows recording a track (i.e., song) name, Spotify track ID, an indicator determining if the song includes *explicit lyrics* and the Spotify **popularity** score.
* `album_track_df` -- A data.frame with 72156 rows but only two columns mapping all Spotify track IDs with their correspond Spotify album IDs.
* `track_features` -- A data.frame with 72143 rows record track IDs along with a series of audio *features* as reported by Spotify. This includes
   + duration_ms - the duration of the track in milliseconds.
   + time_signature - An estimated overall time signature of a track. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure). Note: common time is 4.
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

## Part 1 - Specifics

Below we outline all the individual questions to answer. The first question is for fun and to get you moving. The next NUMBER questions involve some data processing and are design to provide some insight that will help you build a model. You are being tasked with making some decision and to use knowledge we have covered since the first day of class -- yes, material from In-class 01 appears on this assignment! Many of these questions will involve data processing (think `mutate`, `filter`, `group_by`, *joining*) and may also require for you to learn some new functions.

Some other items to note: the same song may be in the data multiple times (each time with a unique track ID) because the song is released on multiple albums (original album, a *greatest hits* and a single). Likewise, some albums are in the data multiple times (multiple releases of an album, or a "clean" version versus one with explicit lyrics). These nuances will be addressed below.


### Question 1

Write R code to find the 15 most popular full albums (not singles) in terms of average popularity score of all tracks on the album (hint: the 15th highest average popularity score is 74.7). How many of the artist and albums on the list do you know?  How many do you think your instructor knows?

### Question 2

The variables key, time_signature and mode are recorded as numeric variables but are categorical in context. Perform any necessary data processing to treat these variables as categorical and explore the relationship between the different category levels and popularity scores.

### Question 3

In this question we will study the effects of track length on popularity. Categorize the duration of the Songs as such: tracks under 2 minutes and thirty seconds are considered short, while songs between 2:30 and 3 minutes and 30 seconds are "Radio Friendly". Songs from 3:30 to 4:30 in duration are "Longer Radio" songs, songs from 4 minutes and 30 seconds to 5:30 are "Long Songs" and songs over 5 minutes and 30 seconds are "Very Long Songs".  When a song by a specific artist is in the data multiple times, using the average duration and average popularity score of all versions of the song. What effect does song length appear to have on popularity? What does this imply about using song length as a predictor variable in a model? Hint: in this class we have discussed 'linear' models -- does the relationship follow that pattern?

### Question 4

Explicit lyrics comparison.

### Question 5

Processing for modeling

### Question 6

Fit a model that explains popularity scores.

