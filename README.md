# Golf NLP Chatbot

The objective of this project is to build a chatbot to answer basic golf improvement questions. This includes three different processes - tf-idf, sentence transformers, and openAI - to build three different models and compare the results of each.

## Data Collection
The data is collected using transcript data from [Golf Digest](https://www.golfdigest.com/story/the-50-best-teachers-in-america) Top 50 Instructor Mike Malaska's YouTube videos. By searching in YouTube "Mike Malaska Golf", I was able to quickly obtain a list of 204 of his golf videos. The IDs were extracted from the URL and then I used the 'youtube_transcript_api' to extract the transcript and other relevant info for each YouTube video. As long as a YouTube video has the 'CC' option, the API will extract the transcript as seen on the video. After collecting the data, some final data cleaning included the removal of '[Music]' or '[Applause]' at the start of several videos.
