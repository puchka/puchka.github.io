---
layout: post
comments: true
---

The idea came when I searched for corpora for the project
I'm currently working in my intership.

I came across a (https://github.com/facebookresearch/fastText/blob/master/pretrained-vectors.md#models)[fastTex]
pre-trained models built by Facebook Research.

I wrote about an experiment around it in a blog post in Malagasy
(http://www.famaky.com/2017/03/19/fikirakirana-modely-voakajy-taminny-teny-malagasy/)[Using model built with malagasy language]
in the malagasy digitial community blog.

These models was trained on (https://www.wikipedia.org/)[Wikipedia] for 90 languages including Malagasy.

I found when experimenting with this model that it has less quality
than for example the
(https://s3.amazonaws.com/dl4j-distribution/GoogleNews-vectors-negative300.bin.gz)[Google News corpus model]
povided by Google that was trained on Google News 3 billions running words corpus.

When searching in large list of corpora too, I didn't find mention to Malagasy.

- (https://nlp.stanford.edu/links/statnlp.html)[Statistical natural language processing and
corpus-based computational linguistics: An annotated list of resources - Stanford NLP]
- (https://en.wikipedia.org/wiki/List_of_text_corpora)[List of text corpora - Wikipedia]

Beside this fact, I found that malgasy web sites was indexed by some open crawling and archiving
of the Web projects like (http://commoncrawl.org)[Common Crawl] and (https://archive.org)[Archive.org].

I get to know it by requesting people in the facebook group
(https://www.facebook.com/groups/facedev.mg/permalink/1433233820034113/)[facedev.mg] to and in comment malagasy websites that they know.

I just found that there was a repository list for malagasy website too : (http://takelaka.org)[Malagasy sites]

By requesting the index of (http://index.commoncrawl.org)[CommonCrawl Index API] and
(https://archive.org/help/wayback_api.php)[Wayback CDX Server API],
I get to know that there are crawling records of malagasy web sites.

My proposition is to use these already crawled data to begin to build a corpus for malagasy language.

If the interest remaing and if we find use cases of frequently crawling malagasy websites,
we can begin to run a crawler targetting malagasy web sites using
(https://github.com/commoncrawl/commoncrawl-crawler)[The CommonCrawl Crawler Engine and Related MapReduce code] or
(https://github.com/internetarchive/wayback)[Internet Archive's public Wayback Machine].

But for these, we'll need some infrastructure resources and operational effort.
I hope to engage more people interested to Natural Language Processing to this project.

A priori, the interest should be there according to recent interest to Bot development.
