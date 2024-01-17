# Golf NLP Chatbot

The objective of this project is to build a chatbot to answer basic golf improvement questions. This includes three different processes - TF-IDF, sentence transformers, and openAI - to build three different models and compare the results of each.

## Data Collection
The data is collected using transcript data from [Golf Digest](https://www.golfdigest.com/story/the-50-best-teachers-in-america) Top 50 Instructor Mike Malaska's YouTube videos. By searching in YouTube "Mike Malaska Golf", I was able to quickly obtain a list of 204 of his golf videos. The IDs were extracted from the URL and then I used the 'youtube_transcript_api' to extract the transcript and other relevant info for each YouTube video. As long as a YouTube video has the 'CC' option, the API will extract the transcript as seen on the video. After collecting the data, some final data cleaning included the removal of '[Music]' or '[Applause]' at the start of several videos.

![](/images/_nlp_golfdata.png)

The biggest obstacle to the dataset is the lack of punctuation in the transcripts. Because of this, the TF-IDF and sentence transformer models struggled to perform adequately. Other obstacles include the casual nature of video conversation not being as specific as written text, and also the fact that some video conversation is not able to pick up the visual context of a video. That being said, the OpenAI chatbot was able to overcome these challenges and outperformed expectations. With more time, the model could be improved by further cleaning up the text transcripts by eliminating some sentences and by replacing some videos with others that have more informative text transcripts in the video.

## Results
For the TF-IDF model, the text is cleaned by removing stop words, punctuations, contractions, special characters, and words less than three characters long. Then, the tokens are lemmatized with the most frequent bigrams added as well. Here are the tokens with the top 10 highest mean TF-IDF scores, as well as the most frequent tokens and bigrams in the corpus. 

<img src="/images/_nlp_golf_top10_tfidf.png" width="500">

Because of the lack of punctuation, textwrap is used to end the sentences at roughly 100 characters. Due to the lack of sentence quality, the TF-IDF and sentence transformer models (which uses ‘multi-qa-MiniLM-L6-cos-v’ SentenceTransformer model from Hugging Face) were greatly outperformed by the OpenAI model.

The OpenAI chatbot is created by first getting an API key from OpenAI. From there, the API key is privately stored in Google Cloud. Then, LlamaIndex is the interface between the text data and the OpenAI LLM. A lot of this material is constantly evolving, so the most helpful resources for this process were [LlamaIndex](https://docs.llamaindex.ai/en/stable/understanding/putting_it_all_together/chatbots/building_a_chatbot.html) and [this](https://shweta-lodha.medium.com/create-chatbot-based-on-the-data-feed-by-you-gpt-index-llamaindex-openai-3efd7abe3ed9) article on the topic. With more time, I'd like to explore how the following parameters can improve the accuracy of the model: max_input, tokens, chunk_size, chunk_overlap_ratio, and temperature. I used the ‘text-davinci-003’ model from OpenAI and created the index using promptHelper, llmPredictor and GPTVectorStoreIndex. Here is an example of the results from the chatbot:

<img src="/images/_nlp_golf_openai_chatbot.png" width="1000">
