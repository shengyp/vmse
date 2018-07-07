# Visualizing Multi-Document Semantics via Open Domain Information Extraction

Our system uses a large collection of news articles released by Signal Media. It consists of 734,488 news articles and 265,512 blog articles, in total around 1 million English-language articles, with an average article length of 405 words. The articles stem from a variety of news sources and were collected during a period of one month (1-30 September 2015). It can be [downloaded](http://research.signalmedia.co/newsir16/signal-dataset.html) from here.


## Basic idea
In today's interconnected world, there is an endless 24/7 stream of new articles appearing online. Faced with these overwhelming amounts of data, it is often helpful to consider only the key entities and concepts and their relationships. This is challenging, as relevant connections may be spread across a number of disparate articles and sources. 

We present a system that extracts salient entities, concepts, and their relationships from a set of related documents, discovers connections within and across them, and presents the resulting information in a graph-based visualization. We rely on a series of natural language processing methods, including open-domain information extraction, a special filtering method to maintain only meaningful relationships, and a heuristic to form a graph with high coverage rate of topic entities and concepts. Our graph visualization then allows users to explore these connections. In our demonstration, we use a large collection of news crawled from the Web and show how connections within this data can be explored.


## How dose the system works?
The objective of our system is to support the user in quickly finding salient connections and facts from a collection of news articles, with a beginner-friendly interactive visualization interface. Our system is componsed of three major components:
* Fact extraction module 
* Fact filtering module
* Conceptual graph construction module

In the following, we will give a concrete example to illustrate the intermediate result of our system. 

By default, the system lists five predefined trending news topics, e.g. the Syria refugee crisis, Iran nuclear issue, Volkswagen scandal, US presidential election, and the Chinese cooperation with Sudan. For each topic, the user can select relevant high-frequency keywords. For example, the user select several topic keywords of US presidential election, the system shows a list of documents ranked by their weight as selected, in which we select the top-25 documents for further processing, they can be [retrieved](https://github.com/shengyp/Multi-Docs-semantics/tree/master/data/elections/documents) from here.

We rely on a series of natural language processing methods that provided by the fact module, including open-domain information extraction and coreference resolution, to achieve this while accounting for linguistic phenomena, e.g., handling pronouns such as ''she''. While previous work on open information extraction has extracted large numbers of subject-predicate-object triples, our method attempts to maintain only those that are most likely to correspond to meaningful relationships. For above top-25 documents, we can obtain corresponding result as [retrieved](https://github.com/shengyp/Multi-Docs-semantics/tree/master/data/elections/extracted-facts) from here.

This data can be filtered such that only the most salient connections are maintained. That is, a set of entities and concepts as nodes and their connections as links to mark those facts assessed as salient, confident, and compatible after applying the filtering algorithm. The result of fact filtering module can be [download](https://github.com/shengyp/Multi-Docs-semantics/blob/master/data/elections/filtering-facts) from here.
 
The annotators with NLP background employ a heuristic to merge these subgraphs that formed in fact filtering module to a full conceptual graph, it guarantees the connected component of 25 entities and concepts or less remains. 
 
  
## Evaluation 
The evaluation metrics for our include:  
 
* Coverage Rate. We evaluation coverage rate of the topic concepts. Coverage rate is the number of topic concepts for which assigns correct divided by the total number of all entities and concepts in the conceptual graph.

* ROUGE Criterion. Due to ROUGE criteria is mainly appropriate for document abstract evaluation. We use Submodular1 algorithm to generate the abstract for specific multi-document as reference graph, then present our conceptual graph across these documents to tidy up in the form of documents abstract, in which those facts sorting might be complemented with annotators. In comparison with reference graph using different ROUGE methods, we can compute performance params that on average and fill in Table 2.

<div align=center><img width="500" height="370" src="http"/></div>



The correspondence between the summarization methods and the summarization tasks is shown in the following table:

| Method  | Avg_Precision | Avg_Recall | Avg_F-Score |
|:-----------:|:--------:| :--------:| :-------:|
| ROUGE-2 | 0.643 | 0.438 | 0.521 |
| ROUGE-L | 0.517 | 0.259 | 0.346 |
| ROUGE-S | 0.344 | 0.384 | 0.362 |




## References
Fu, R., Guo, J., Qin, B., Che, W., Wang, H., & Liu, T. (2014). Learning Semantic Hierarchies via Word Embeddings. In ACL (1) (pp. 1199-1209).

Novak J D, Cañas A J. Theoretical origins of concept maps, how to construct them, and uses in education[J]. Reflecting Education, 2007(1-2).

Manning C D, Surdeanu M, Bauer J, et al. The Stanford CoreNLP Natural Language Processing Toolkit[C]// Meeting of the Association for Computational Linguistics: System Demonstrations. 2014.

Mihalcea R, Tarau P. TextRank: Bringing Order into Texts[C]// Conference on Empirical Methods in Natural Language Processing, EMNLP 2004, A Meeting of Sigdat, A Special Interest Group of the Acl, Held in Conjunction with ACL 2004, 25-26 July 2004, Barcelona, Spain. DBLP, 2004:404-411.

Pilehvar M T, Jurgens D, Navigli R. Align, Disambiguate and Walk: A Unified Approach for Measuring Semantic Similarity[C]// Meeting of the Association for Computational Linguistics. 2013.

Li, Jingxuan, Lei Li, and Tao Li. 2012. Multi-document summarization via submodularity. Applied Intelligence 37.3: 420-430.



## Contact us
Welcome to contact us if you have any questions or suggestions about our system. 

Contact person: Yongpan Sheng

Contact email: shengyp2011@163.com





