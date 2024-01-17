# Golf NLP Chatbot

The objective of this project is to build a chatbot to answer basic golf improvement questions. This includes three different processes - tf-idf, sentence transformers, and openAI - to build three different models and compare the results of each.

## Data Collection
The data is collected using transcript data from [Golf Digest](https://www.golfdigest.com/story/the-50-best-teachers-in-america) Top 50 Instructor Mike Malaska's YouTube videos. By searching in YouTube "Mike Malaska Golf", I was able to quickly obtain a list of 204 of his golf videos. The IDs were extracted from the URL and then I used the 'youtube_transcript_api' to extract the transcript and other relevant info for each YouTube video. As long as a YouTube video has the 'CC' option, the API will extract the transcript as seen on the video. After collecting the data, some final data cleaning included the removal of '[Music]' or '[Applause]' at the start of several videos.

![](/images/_nlp_golfdata.png)

The biggest obstacle to the dataset is the lack of punctuation in the transcripts. Because of this, the tf-idf and sentence transformer models struggled to perform adequately. Other obstacles include the casual nature of video conversation not being as specific as written text, and also the fact that some video conversation is not able to pick up the visual context of a video. That being said, the OpenAI chatbot was able to overcome these challenges and outperformed expectations. With more time, the model could be improved by further cleaning up the text transcripts by eliminating some sentences and by replacing some videos with others that have more informative text transcripts in the video.

## Results

![](/images/_nlp_golf_top10_tfidf.png)

<img src="/images/_nlp_golf_top10_tfidf.png" width="200">


### TF-IDF
