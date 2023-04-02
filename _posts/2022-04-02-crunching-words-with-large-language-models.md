---
layout: post
title:  "Crunching Words With Large Language Models"
date:   2023-04-02 20:43:21 +0400
categories: jekyll update
---

One of the most common misuses of large language models (LLMs) like ChatGPT is treating them as search engines. But I can definitely see why people do this.

If you ask an LLM a question, it will answer it. Using it as an alternative to a search engine like Google is therefore one of the most obvious applications. For many search queries, this also works quite well. BUT: It’s also going to quickly get you into trouble.

Ted Chiang’s classic essay [ChatGPT Is a Blurry JPEG of the Web](https://www.newyorker.com/tech/annals-of-technology/chatgpt-is-a-blurry-jpeg-of-the-web) helps explain why:

> Think of ChatGPT as a blurry jpeg of all the text on the Web. It retains much of the information on the Web, in the same way that a jpeg retains much of the information of a higher-resolution image, but, if you’re looking for an exact sequence of bits, you won’t find it; all you will ever get is an approximation. But, because the approximation is presented in the form of grammatical text, which ChatGPT excels at creating, it’s usually acceptable.

The model behind [ChatGPT](https://openai.com/blog/chatgpt) is huge, but not big enough to accurately store all the facts it encountered in its training set.

It can give a convincing answer to anything, but that does not mean that it reflects the actual facts in its answers. You always have to remain skeptical and check what it tells you.

LLMs are also known to ["hallucinate"](https://en.wikipedia.org/wiki/Hallucination_(artificial_intelligence)). That they invent new facts that fit into the sentence structure even though they have no basis in the underlying data.

There are many facts about the world that people do not agree on. With a normal search, you can compare these versions and consider their sources. A language model might instead try to compute some sort of average of all the opinions it has been trained on. This may sometimes be desirable, but often not.

This becomes even more obvious when looking at smaller language models. [LLaMA 7B](https://arxiv.org/pdf/2302.13971v1.pdf) can be represented as a 3.9 GB file. It contains an amazing amount of information, but obviously this is not enough storage to accurately answer every question you might have.

So if they’re not reliable for use as a search engines, what are LLMs even good for?

## An instrument for crunching words
I like to think of language models like ChatGPT as somesort of a calculator for words.

This is reflected in their name. A "language model" implies that they are tools for working with language. That's what they've been trained to do, and they really excel at language manipulation.

Should they work with specific facts? Then add them to the language model as part of the original prompt.

Applications where LLMs excel include such things as

- Summarize: give them an essay or article and ask them to summarize it.
- Answering questions: use these sections of text to answer a specific question about the information they contain.
- Fact extraction: ask for bullet points that show the facts presented in an article.
- Rephrasing: Rephrase things to be more "punchy" or "professional", etc. 
- Suggest titles 
- Use them as a thesaurus. "I need a word that indicates X"
- Fun, creative, wild stuff. Let well-known characters jump into others shoes and see how they would think about certain things
A calculator for words is an incredibly powerful thing.

## LLMs as an extention of search engines
Here's where it gets a little more complicated. Some language models can function as search engines. The two most obvious are Microsoft Bing and Google Bard, but there are many other examples of this pattern. There is even an alpha feature of ChatGPT called "Browsing Mode" that can do this. You can think of these search tools as augmented language models.

The way it works is that the language model recognizes when a search might be helpful in answering a question. When that is the case, it runs that search through a connected search engine via an API.

It then copies data from the search results back into itself as part of an invisible prompt, and uses that new context to answer the original question of the user.

This is virtually the same as running a search, then copying and pasting information into the language model and asking it a question about that data.

It's important to point out that there's still a risk of hallucination here, even if you feed the system the facts it's supposed to use. I've caught Bing inserting made-up things in the middle of text that should have come entirely from their search results.

## Using LLMs is like cooking
Many of the challenges associated with language models can be traced back to the following. They look much simpler than they actually are.

In order to maximize their utility and mitigate the numerous risks associated with their use, one must invest considerable effort in familiarizing oneself with their operation, capabilities, and potential vulnerabilities, thus cultivating a precise mental framework.

What makes LLMs different from number crunchers (calculators) in that they are based on probabilities and therefore do not always give the same answer for a given input.

All analogies are imperfect, but some are even more imperfect than others.
