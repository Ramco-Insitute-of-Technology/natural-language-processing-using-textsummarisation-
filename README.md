# natural-language-processing-using-textsummarisation-
importnltk
nltk.download('punkt')
nltk.download('stopwords')
fromnltk.tokenizeimportsent_tokenize, word_tokenize
fromnltk.corpusimportstopwords
fromnltk.probabilityimportFreqDist
deftext_summarization(text, num_sentences):
    # Tokenize the text into sentences
    sentences = sent_tokenize(text)

    # Tokenize each sentence into words
    words = word_tokenize(text.lower())

    # Remove stop words
    stop_words = set(stopwords.words('english'))
    words = [word for word in words if word notinstop_words]

    # Calculate word frequency
    word_freq = FreqDist(words)
    sentence_scores = {}
    for sentence in sentences:
        for word inword_tokenize(sentence.lower()):
            if word inword_freq:
                if sentence notinsentence_scores:
                    sentence_scores[sentence] = word_freq[word]
                else:
                    sentence_scores[sentence] += word_freq[word]

    # Sort sentences by score and select top n sentences for summary
    top_sentences = sorted(sentence_scores.items(), key=lambda x: x[1], reverse=True)[:num_sentences]
    summary = ' '.join([sentence[0] for sentence intop_sentences])

    return summary
text = """

num_sentences = 3  # Number of sentences in the summary
summary = text_summarization(text, num_sentences)
print(summary
