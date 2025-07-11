<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "f53ba0fa49164f9323043f1c6b11f2b1",
  "translation_date": "2025-05-19T13:02:55+00:00",
  "source_file": "01-introduction-to-genai/README.md",
  "language_code": "en"
}
-->
# Introduction to Generative AI and Large Language Models

[![Introduction to Generative AI and Large Language Models](../../../translated_images/01-lesson-banner.f4869237c4117400e7a80dd1e19ba2929e1491e5dbe494ad705533362f402e81.en.png)](https://aka.ms/gen-ai-lesson-1-gh?WT.mc_id=academic-105485-koreyst)

_(Click the image above to view video of this lesson)_

Generative AI is artificial intelligence capable of generating text, images, and other types of content. What makes it a fantastic technology is that it democratizes AI; anyone can use it with as little as a text prompt, a sentence written in a natural language. There's no need for you to learn a language like Java or SQL to accomplish something worthwhile; all you need is to use your language, state what you want, and out comes a suggestion from an AI model. The applications and impact for this are huge; you can write or understand reports, create applications, and much more, all in seconds.

In this curriculum, we’ll explore how our startup leverages generative AI to unlock new scenarios in the education world and how we address the inevitable challenges associated with the social implications of its application and the technology limitations.

## Introduction

This lesson will cover:

- Introduction to the business scenario: our startup idea and mission.
- Generative AI and how we landed on the current technology landscape.
- Inner workings of a large language model.
- Main capabilities and practical use cases of Large Language Models.

## Learning Goals

After completing this lesson, you will understand:

- What generative AI is and how Large Language Models work.
- How you can leverage large language models for different use cases, with a focus on education scenarios.

## Scenario: our educational startup

Generative Artificial Intelligence (AI) represents the pinnacle of AI technology, pushing the boundaries of what was once thought impossible. Generative AI models have several capabilities and applications, but for this curriculum, we'll explore how it's revolutionizing education through a fictional startup. We'll refer to this startup as _our startup_. Our startup works in the education domain with the ambitious mission statement of

> _improving accessibility in learning, on a global scale, ensuring equitable access to education, and providing personalized learning experiences to every learner, according to their needs_.

Our startup team is aware we’ll not be able to achieve this goal without leveraging one of the most powerful tools of modern times – Large Language Models (LLMs).

Generative AI is expected to revolutionize the way we learn and teach today, with students having at their disposal virtual teachers 24 hours a day who provide vast amounts of information and examples, and teachers able to leverage innovative tools to assess their students and give feedback.

![Five young students looking at a monitor - image by DALLE2](../../../translated_images/students-by-DALLE2.f0fce818ebbcca8f5f9e8733e3c67158a1162fe0089c498c35da405fc9e9ee4e.en.png)

To start, let’s define some basic concepts and terminology we’ll be using throughout the curriculum.

## How did we get Generative AI?

Despite the extraordinary _hype_ created lately by the announcement of generative AI models, this technology is decades in the making, with the first research efforts dating back to the 60s. We're now at a point with AI having human cognitive capabilities, like conversation as shown by, for example, [OpenAI ChatGPT](https://openai.com/chatgpt) or [Bing Chat](https://www.microsoft.com/edge/features/bing-chat?WT.mc_id=academic-105485-koreyst), which also uses a GPT model for the web search Bing conversations.

Backing up a bit, the very first prototypes of AI consisted of typewritten chatbots, relying on a knowledge base extracted from a group of experts and represented into a computer. The answers in the knowledge base were triggered by keywords appearing in the input text. However, it soon became clear that such an approach, using typewritten chatbots, did not scale well.

### A statistical approach to AI: Machine Learning

A turning point arrived during the 90s, with the application of a statistical approach to text analysis. This led to the development of new algorithms – known as machine learning – capable of learning patterns from data without being explicitly programmed. This approach allows machines to simulate human language understanding: a statistical model is trained on text-label pairings, enabling the model to classify unknown input text with a pre-defined label representing the intention of the message.

### Neural networks and modern virtual assistants

In recent years, the technological evolution of hardware, capable of handling larger amounts of data and more complex computations, encouraged research in AI, leading to the development of advanced machine learning algorithms known as neural networks or deep learning algorithms.

Neural networks (and in particular Recurrent Neural Networks – RNNs) significantly enhanced natural language processing, enabling the representation of the meaning of text in a more meaningful way, valuing the context of a word in a sentence.

This is the technology that powered the virtual assistants born in the first decade of the new century, very proficient in interpreting human language, identifying a need, and performing an action to satisfy it – like answering with a pre-defined script or consuming a 3rd party service.

### Present day, Generative AI

So that’s how we came to Generative AI today, which can be seen as a subset of deep learning.

![AI, ML, DL and Generative AI](../../../translated_images/AI-diagram.cab4093fe39583ffc0d19c22eab2ef79aaf4ef307ea91ac18f97aa008abeb45c.en.png)

After decades of research in the AI field, a new model architecture – called _Transformer_ – overcame the limits of RNNs, being able to get much longer sequences of text as input. Transformers are based on the attention mechanism, enabling the model to give different weights to the inputs it receives, ‘paying more attention’ where the most relevant information is concentrated, regardless of their order in the text sequence.

Most of the recent generative AI models – also known as Large Language Models (LLMs), since they work with textual inputs and outputs – are indeed based on this architecture. What’s interesting about these models – trained on a huge amount of unlabeled data from diverse sources like books, articles, and websites – is that they can be adapted to a wide variety of tasks and generate grammatically correct text with a semblance of creativity. So, not only did they incredibly enhance the capacity of a machine to ‘understand’ an input text, but they enabled their capacity to generate an original response in human language.

## How do large language models work?

In the next chapter, we are going to explore different types of Generative AI models, but for now let’s have a look at how large language models work, with a focus on OpenAI GPT (Generative Pre-trained Transformer) models.

- **Tokenizer, text to numbers**: Large Language Models receive a text as input and generate a text as output. However, being statistical models, they work much better with numbers than text sequences. That’s why every input to the model is processed by a tokenizer, before being used by the core model. A token is a chunk of text – consisting of a variable number of characters, so the tokenizer's main task is splitting the input into an array of tokens. Then, each token is mapped with a token index, which is the integer encoding of the original text chunk.

![Example of tokenization](../../../translated_images/tokenizer-example.09b30260020c3c1d21640d5729bf21332e179331bef6b8b6944627f6f722caf8.en.png)

- **Predicting output tokens**: Given n tokens as input (with max n varying from one model to another), the model is able to predict one token as output. This token is then incorporated into the input of the next iteration, in an expanding window pattern, enabling a better user experience of getting one (or multiple) sentence as an answer. This explains why, if you ever played with ChatGPT, you might have noticed that sometimes it looks like it stops in the middle of a sentence.

- **Selection process, probability distribution**: The output token is chosen by the model according to its probability of occurring after the current text sequence. This is because the model predicts a probability distribution over all possible ‘next tokens’, calculated based on its training. However, not always is the token with the highest probability chosen from the resulting distribution. A degree of randomness is added to this choice, in a way that the model acts in a non-deterministic fashion - we do not get the exact same output for the same input. This degree of randomness is added to simulate the process of creative thinking and it can be tuned using a model parameter called temperature.

## How can our startup leverage Large Language Models?

Now that we have a better understanding of the inner workings of a large language model, let’s see some practical examples of the most common tasks they can perform pretty well, with an eye to our business scenario. We said that the main capability of a Large Language Model is _generating a text from scratch, starting from a textual input, written in natural language_.

But what kind of textual input and output?
The input of a large language model is known as a prompt, while the output is known as a completion, a term that refers to the model mechanism of generating the next token to complete the current input. We are going to dive deep into what a prompt is and how to design it in a way to get the most out of our model. But for now, let’s just say that a prompt may include:

- An **instruction** specifying the type of output we expect from the model. This instruction sometimes might embed some examples or some additional data.

  1. Summarization of an article, book, product reviews, and more, along with extraction of insights from unstructured data.
    
    ![Example of summarization](../../../translated_images/summarization-example.657a46c47f91b0bd88f66bff8ffe222aa191de2b57ca790b3791a29ad224a807.en.png)
  
  2. Creative ideation and design of an article, an essay, an assignment, or more.
      
     ![Example of creative writing](../../../translated_images/creative-writing-example.c739bb30fe99dc42dc039c166694fd644983376af24548793db26b582b149e7b.en.png)

- A **question**, asked in the form of a conversation with an agent.
  
  ![Example of conversation](../../../translated_images/conversation-example.b2c7cda5634819bd2f67f36084e3cf38f867b18b6628b66d340398525fa9edb1.en.png)

- A chunk of **text to complete**, which implicitly is an ask for writing assistance.
  
  ![Example of text completion](../../../translated_images/text-completion-example.524a39b86473c6d85f9ad472e7c5ee569c040fa6f42f54b2a08e28118b9f13c2.en.png)

- A chunk of **code** together with the ask of explaining and documenting it, or a comment asking to generate a piece of code performing a specific task.
  
  ![Coding example](../../../translated_images/coding-example.5c46e1eb38083c0fffad9a244a1fb53394d080fce299ec0d121f4263cacee014.en.png)

The examples above are quite simple and are not intended to be an exhaustive demonstration of Large Language Models' capabilities. They are meant to show the potential of using generative AI, in particular but not limited to educational contexts.

Also, the output of a generative AI model is not perfect and sometimes the creativity of the model can work against it, resulting in an output which is a combination of words that the human user can interpret as a mystification of reality, or it can be offensive. Generative AI is not intelligent - at least in the more comprehensive definition of intelligence, including critical and creative reasoning or emotional intelligence; it is not deterministic, and it is not trustworthy, since fabrications, such as erroneous references, content, and statements, may be combined with correct information, and presented in a persuasive and confident manner. In the following lessons, we’ll be dealing with all these limitations and we’ll see what we can do to mitigate them.

## Assignment

Your assignment is to read up more on [generative AI](https://en.wikipedia.org/wiki/Generative_artificial_intelligence?WT.mc_id=academic-105485-koreyst) and try to identify an area where you would add generative AI today that doesn't have it. How would the impact be different from doing it the "old way"? Can you do something you couldn't before, or are you faster? Write a 300-word summary on what your dream AI startup would look like and include headers like "Problem", "How I would use AI", "Impact" and optionally a business plan.

If you did this task, you might even be ready to apply to Microsoft's incubator, [Microsoft for Startups Founders Hub](https://www.microsoft.com/startups?WT.mc_id=academic-105485-koreyst). We offer credits for both Azure, OpenAI, mentoring, and much more. Check it out!

## Knowledge check

What's true about large language models?

1. You get the exact same response every time.
2. It does things perfectly, great at adding numbers, producing working code, etc.
3. The response may vary despite using the same prompt. It's also great at giving you a first draft of something, be it text or code. But you need to improve on the results.

A: 3, an LLM is non-deterministic; the response varies. However, you can control its variance via a temperature setting. You also shouldn't expect it to do things perfectly; it's here to do the heavy-lifting for you, which often means you get a good first attempt at something that you need to gradually improve.

## Great Work! Continue the Journey

After completing this lesson, check out our [Generative AI Learning collection](https://aka.ms/genai-collection?WT.mc_id=academic-105485-koreyst) to continue leveling up your Generative AI knowledge!

Head over to Lesson 2 where we will look at how to [explore and compare different LLM types](../02-exploring-and-comparing-different-llms/README.md?WT.mc_id=academic-105485-koreyst)!

Certainly! Here is the translated text in English:

---

**Disclaimer**:  
This document has been translated using AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). While we strive for accuracy, please be aware that automated translations may contain errors or inaccuracies. The original document in its native language should be considered the authoritative source. For critical information, professional human translation is recommended. We are not liable for any misunderstandings or misinterpretations arising from the use of this translation.