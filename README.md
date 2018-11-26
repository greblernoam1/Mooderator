# Mooderator-
AI algorithm that understands a song's mood

Unlock your iPhone, plug in your earphones, go into Spotify and blast some music. This has become an everyday habit for a large amount of people around the world. Music is a way to escape the present and feel something different from our mundane lives. However, a general habit in the world of music is to classify the songs by genre (e.g. Jazz, Hip Hop, etc...). This clearly contradicts the idea of listening to music to feel something as a jazz song can bring us to feel the same mood than a hip-hop song, but two jazz songs might awaken very different moods in us. Through our research of past literature on this matter we found two papers that inspired our project. The first paper (Kim and André) investigates a musical induction method that spontaneously leads subjects to real emotional states. The second paper (Yang and Lee) we found explains introduces an algorithm that tries to understand the mood of a song by analyzing its lyrics. Knowing that a song can change our mood and that an algorithm can understand the mood of a song through its lyrics we decided to create an algorithm that understands the mood of a song by analyzing all of its components (e.g. timber, pitch, etc..) but lyrics. This idea seemed interesting to us as, by simply using this app we could help people feel the way they want. From this idea we create The Mooderator, an neural network that is able to understand the mood of a song by simply analyzing its musical components and ignore the lyrics.

Our Solution

Our Solution is based in several steps:

1) The code directly intakes a list of 30 seconds audio files which we took from a library
of songs that were classified by genre and we manually classified them by mood and then names each file by their mood and number e.g. happy079.wav. The code does this for training and validation data.

2) It then grabs each file individually and serializes it by breaking it up into four basic musical features. We used librosa (Python audio analysis lib.), to extract four identifying features from various pieces of music: pitch (Chromagram), intensity (loudness, by Constant Q-Transform), timbre (MFCC), and tempo for each beat. It then takes an average of all the beats to give a categorization for the whole file for each feature. We end up saving this numbers in arrays.
These are some spectrograms showing our work:

  a) Mel power spectrogram
  
  b) Beat-synchronous MFCC (Timbre)
  
  c) Beat-synchronous CQT (Intensity)
  
  d) Percussive vs. Harmonic components
  
  e) Beat-synchronous Chroma (Pitch)
  
  f) We used a table to help us classify how each feature of a song translates to its mood
  
3) Pass this serialization through our model and then use it as a training/validation data
which mean that the f vector is the serialization and the expected result, g vector, is
the name of the song.

4) Then once the model is ready we take an audio file and drop it into our Web-App
5) Same serialization as in step 2.

6) Use this serialization to figure out the mood of each beat and the mood of the whole
song.

7) This information is then passed to the front end which outputs some graphics that are
dependent on mood/beat.
