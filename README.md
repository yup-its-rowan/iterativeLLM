# Iterative LLM



## Diary
---
### Day 1
I have this idea of developing a simple LLM that I can train on my computer, with outputs similar to that of GTP-1 or GPT-2. 
There's been a boom in the capabilities of processors and graphics cards since their initial development, and I hope that more advanced training techniques would result in a similarly better model.
I hope to spend no longer than a couple hours on a training session on my desktop, but we will see how that goes. 

First thing to do is to understand the structure of creating an LLM. Then I will decide what languages to use, and move on from there. I'll probably hit a couple dozen roadblocks but I have the time, and probably the willpower. Let's do this.

It looks like the main areas of work for training LLMs are in Pretraining, Alignment, and Human Reinforcement Learning. We aren't doing the last one because I don't want to spend money on it. I also should learn about transformers and the process of embedding.

Let's begin!

### Day 2
Everything is absurdly confusing and makes very little sense to me. It feels like every component of this process is uniquely abstracted in ways that only make sense when you put all of the pieces together.
I really doubt I will be able to write any usable code for this for a long while.
Let's start with my understanding of the basic user flow of an LLM, and I'll put in a little red flag every time there's a complication.

**The inputs**
1) A user inputs a sentence.
2) That sentence is broken up into tokens (words or parts of words) 🚩
3) These tokens are replaced with token IDs (just a number, an index), so that we can more easily reference their higher dimensional embeddings 🚩
4) Now the token IDs are replaced with those token embeddings, basically large vector spaces that contain the individual context of every word

At this point, we have a bunch of vectors representing the rich context of each token

**Transformer-land**
5) Self-attention mechanisms are order agnostic, so before putting these token embeddings through a transformer, make sure to add additional positional encoding to the token embeddings so the resultant embedding contains semantic information of the word and its position in the sentence 🚩🚩

*Encoder*
6) The positionally aware token embeddings are then passed as a matrix to three different Linear Layers named the Query, Key, and Value layers, to create the Query, Key, and Value matrices 🚩🚩🚩
7) The Query and Key matrices are multiplied together to create an attention filter, which represents how much each token cares about every other token
8) This attention filter is then scaled 

The process of writing out this list has taken many many hours. Every time I felt like I didn't understand why we were doing something, I would spend another hour bouncing between blogs and instructional videos, which themselves created more niche gaps in my understanding. I feel much more confident in my understanding of what is going on under the hood, but I would not recommend recreating this at all. It sucked. 