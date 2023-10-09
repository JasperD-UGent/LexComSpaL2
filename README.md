# LexComSpaL2

This repository includes the LexComSpaL2 (**Lex**ical **Com**plexity for **Spa**nish **L2**) corpus, which can be employed to train personalised word-level difficulty classifiers for learners of Spanish as a foreign/second language (L2). The dataset contains 2,240 in-context target words with the corresponding difficulty judgements of 26 L2 learners of Spanish, resulting in a total of 58,240 annotations. The target words are divided over 200 sentences from 4 different domains (economics, health, law, and migration), which have been selected based on their suitability to be included in L2 learning materials. As the annotation scheme, a customised version of the 5-point lexical complexity prediction scale<sup>[[1]](#references)</sup> is used, tailored to the vocabulary knowledge continuum (which ranges from no knowledge over receptive mastery to productive mastery<sup>[[2]](#references)</sup>). The LexComSpaL2 corpus aims to address the lack of relevant data for multi-category difficult prediction at word level for L2 learners of other languages than English. Full details on the data collection, data labelling and dataset statistics can be found in [anonymised_paper]<sup>[[3]](#references)</sup>.  The corpus consists of 4 files, whose contents are described in detail below.

## Main corpus file
The `LexComSpaL2_all.tsv` file links the in-context target words to their annotations (i.e. the difficulty judgements from the 26 L2 Spanish learners). The file follows the same format as the [CompLex corpus](https://github.com/MMU-TDMLab/CompLex), the first extensive dataset for lexical complexity prediction<sup>[[1]](#references)</sup>. The only difference is that one extra column is added in which the individual annotations are provided. Below, a brief explanation of each column in the TSV file is given:

- `id`: ID of the corpus instance, consisting of three parts (each separated by an underscore). The first part corresponds to the ID of the corpus (see [anonymised_paper]<sup>[[3]](#references)</sup>); the second part is the sentence ID; the third and last part corresponds to the index of the target word in the sentence.
- `corpus`: topic area of the corpus.
- `sentence`: full sentence in tokenised format (each token is separated by a white space).
- `token`: target word.
- `complexity`: average difficulty values, per proficiency level (PL) and overall. The data are provided in a Python dictionary format, with the proficiency levels as the keys ("PL1", "PL2", "PL3", and "overall") and the corresponding average scores as the values.
- `annotations`: new column containing the individual annotations for each participant. The data are again provided in a Python dictionary format, with the participant IDs as the keys and the annotations as the values.


## Participant features
The `LexComSpaL2_participantFeatures.tsv` file contains the participant data, which can be used as features in machine learning models to obtain personalised predictions. Below, a brief explanation of each column in the TSV file is given:

- `participant_ID`: unique ID of the participant.
- `proficiency`: proficiency level of the participant (see the [section on participant metadata](#participant-metadata) for more details).
- `years_experience`: number of years the participant has been studying Spanish in a higher education setting.
- `native_langauge`: native language of the participant (see the [section on participant metadata](#participant-metadata) for more details).

## Participant metadata
The `LexComSpaL2_participantFeatures_metadata.json` file contains descriptions of the participant features included in the `LexComSpaL2_participantFeatures.tsv` file. The data are again provided in the form of a Python dictionary.

## Dataset split
Finally, the corpus also comes with a fixed dataset split into 10 different random training/validation/test splits according to an 80/10/10 distribution. This should allow for a fair comparison between models being trained on the LexComSpaL2 corpus. The sets are constructed at sentence level (to enable training machine learning models which take into account the context, such as neural networks with BiLSTM layers), and the different domains are always equally distributed within each set. Statistics on the different splits are provided in the table below, with the 3 values separated by `|` corresponding to, respectively, the number of sentences, the number of target words, and the number of annotations in the set:

| Split |      Training set      |   Validation set   |      Test set      |
|:-----:|:----------------------:|:------------------:|:------------------:|
|   1   | 160 \| 1,796 \| 46,696 | 20 \| 216 \| 5,616 | 20 \| 228 \| 5,928 |
|   2   | 160 \| 1,797 \| 46,722 | 20 \| 227 \| 5,902 | 20 \| 216 \| 5,616 |
|   3   | 160 \| 1,787 \| 46,462 | 20 \| 226 \| 5,876 | 20 \| 227 \| 5,902 |
|   4   | 160 \| 1,775 \| 46,150 | 20 \| 239 \| 6,214 | 20 \| 226 \| 5,876 |
|   5   | 160 \| 1,799 \| 46,774 | 20 \| 202 \| 5,252 | 20 \| 239 \| 6,214 |
|   6   | 160 \| 1,818 \| 47,268 | 20 \| 220 \| 5,720 | 20 \| 202 \| 5,252 |
|   7   | 160 \| 1,803 \| 46,878 | 20 \| 217 \| 5,642 | 20 \| 220 \| 5,720 |
|   8   | 160 \| 1,804 \| 46,904 | 20 \| 219 \| 5,694 | 20 \| 217 \| 5,642 |
|   9   | 160 \| 1,775 \| 46,150 | 20 \| 246 \| 6,396 | 20 \| 219 \| 5,694 |
|  10   | 160 \| 1,766 \| 45,916 | 20 \| 228 \| 5,928 | 20 \| 246 \| 6,396 |

## References
[1] Shardlow, M., Cooper, M., & Zampieri, M. (2020). CompLex - A New Corpus for Lexical Complexity Prediction from Likert Scale Data. *Proceedings of the 1st Workshop on Tools and Resources to Empower People with REAding DIfficulties (READI)*, 57–62. https://aclanthology.org/2020.readi-1.9

[2] Schmitt, N. (2019). Understanding vocabulary acquisition, instruction, and assessment: A research agenda. *Language Teaching*, *52*(02), 261–274. https://doi.org/10.1017/S0261444819000053

[3] anonymised_paper
