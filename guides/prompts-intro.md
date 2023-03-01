# 提示工程介绍

提示工程是一门相对较新的学科，旨在开发和优化提示，以有效地使用语言模型（LLM）完成各种应用和研究课题。提示工程技能有助于更好地理解大型语言模型（LLM）的能力和局限性。研究人员利用提示工程来改善 LLM 在各种常见和复杂任务（如问答和算术推理）上的能力。开发人员利用提示工程来设计有效的提示技术，用于开发基于语言模型的应用。

本指南介绍标准提示的基础知识，提供如何使用 prompt 与 语言模型 交互和指导的思路。

所有示例都使用`text-davinci-003`（使用 OpenAI 的 playground）测试，除非另有说明。它使用默认配置，例如`temperature=0.7`和`top-p=1`。

主题:

- [基本提示](#基本提示)
- [语言模型设置一览](#语言模型设置一览)
- [标准提示](#标准提示)
- [提示元素](#提示元素)
- [设计人工智能提示的基本技巧](#设计人工智能提示的基本技巧)

---

## 基本提示

您已经可以通过提示实现很多功能，但结果的质量取决于您向模型提供的信息量。提示可以包含您传递给 语言模型 的`指令`或`问题`等信息，以及其他诸如`输入`或`示例`的细节。

这里有一个简单提示的基本示例：

_提示_

```
天空是
```

_输出_

```
天空是蔚蓝色的，太阳晒着柔和的阳光，阳光下的世界一片欢欣。蓝色的天空中点缀着一片片白云，飘来飘去，形成奇妙的图案。风儿拂过湖面，湖面上泛起涟漪，波光粼粼，景色宜人。空气中弥漫着淡淡的花香，让人心旷神怡，心旷神怡。
```

正如你所看到的，语言模型输出一系列根据上下文“天空是”而让人理解的字符串。输出的结果可能出乎意料，或者与我们想要完成的任务相差甚远。

这个基本的例子也突显了提供更多上下文或关于我们想要实现的特定任务的指令的必要性。

让我们试着把它改进一点：

_提示_

```
完成这句话:

天空是
```

_输出_

```
蓝色的。
```

是不是更好了？嗯，我们告诉模型完成这句话，所以结果看起来好多了，因为它正是按照我们所说的去做（“完成句子”）。设计最佳提示以指导模型完成任务的这种方法被称为**提示工程**。

以上的例子是当今 语言模型 可能实现的基本概念的简单说明。语言模型 能够完成各种复杂的任务，从文本摘要到数学推理再到代码生成。

在本指南中，我们会深入讨论这些功能，并就高级提示技巧和提示引擎相关的研究课题等其他方面做出讨论。

---

## 语言模型设置一览

在使用提示时，您将通过 API 或直接与 语言模型 交互。您可以配置一些参数以获得提示的不同结果。

**Temperature ** -简而言之，Temperature 越低，结果就越具有决定性，因为总是选择具有最高概率的下一个令牌。增加温度可能会导致更多随机性，从而鼓励更多不同或创造性的输出。我们本质上是在增加其他可能令牌的权重。在应用上，我们可能希望使用较低的 Temperature 来处理基于事实的 QA，以鼓励更多的事实和简洁的响应。对于诗歌创作或其他创意任务来说，增加 Temperature 可能有益。

**Top_p** - 同样，通过使用温度的采样技术 top_p，您可以控制生成响应的确定性。如果您正在寻找确切和事实性的答案，请将其保持低。如果您正在寻找更多样化的响应，请将其提高到更高的值。

一般的建议是改变一个而不是两个。

在开始一些基本的示例之前，请记住，您的结果可能会根据您使用的 语言模型 版本而有所不同。

---

## 标准提示

在上面，我们尝试了一个非常简单的提示。标准提示的格式如下：

```
<问题>?
```

这可以格式化为 QA 格式，这是许多 QA 数据集中的标准格式，如下所示：

```
Q：<问题>？
A：
```

基于上述标准格式，一种流行且有效的提示技术被称为少量提示，我们提供示例。少量提示的格式如下：

```
<问题>？
<答案>

<问题>？
<答案>

<问题>？
<答案>

<问题>？

```

---

问答格式的版本大概会是这样：

```
Q: <问题>?
A: <答案>

Q: <问题>?
A: <答案>

Q: <问题>?
A: <答案>

Q: <问题>?
A:
```

请记住，不一定非要采用问答格式。格式取决于当前的任务。例如，可以执行简单的分类任务，并给出演示任务的实例，如下所示：

_提示_

```
这太棒了！ // 正面
这太糟糕了！ // 负面
哇，那部电影真棒！ // 正面
真是太糟糕了！ //
```

_输出_

```
负面
```

少量的提示可以实现上下文学习，也就是语言模型只有给出少量示例就能学习任务的能力。我们将在接下来的指南中更加详细地了解这方面的内容。

---

## 提示要素

随着我们涵盖越来越多可以使用提示工程实现的例子和应用，您会注意到组成提示的某些要素。

提示可以包含以下任何组件：

**指令** - 您希望模型执行的特定任务或指令

**上下文** - 可以涉及可以引导模型产生更好回复的外部信息或附加上下文

**输入数据** - 我们感兴趣找到回复的输入或问题

**输出指示器** - 指示输出的类型或格式。

不是所有组件都是提示所必需的，格式取决于手头的任务。我们将在以后的指南中更详细地介绍更具体的例子。

---

## 设计人工智能提示的基本技巧

在设计提示时，请记住以下几点：

### 由易到难

开始设计提示时，您应该牢记，这是一个迭代过程，需要大量实验才能获得最佳结果。使用类似 OpenAI 或 Cohere 的 playground 是一个不错的起点。

你可以从简单的提示开始，并随着优化而不断增加元素和上下文。所以对提示进行版本控制是至关重要的。当我们阅读本指南时，你会看到许多例子，其中特定性、简洁性和简明性往往会给你带来更好的结果。

当你面临一项包含许多不同子任务的大型任务时，可以尝试将任务分解为更简单的子任务，并在获得较好结果的同时逐步累积。这可以避免在一开始就对提示设计过程增加太多的复杂性。

### 指令

您可以为各种简单的任务设计有效的提示，通过使用命令来指示模型您想要实现的目标，例如“写入”、“分类”、“总结”、“翻译”、“排序”等。

要记住，你还需要做大量的实验，看看什么最有效。尝试使用不同的指令、关键词、上下文和数据，看看对你的场景什么最合适。通常，上下文与你要完成的任务越相关越好。在即将到来的指南中，我们将讨论采样和添加更多上下文的重要性。

建议把说明放在提示的开头。也建议使用一些清晰的分隔符，如“###”来分隔说明和上下文。

例如

_提示:_

```
### Instruction ###
Translate the text below to Spanish:

Text: "hello!"
```

_输出:_

```
¡Hola!
```

### 特异性

请非常明确地指出模型要执行的指令和任务。提示越详细描述，结果就越好。当你期望达到某种特定的结果或风格时，这尤为重要。没有特定的标记或关键字可以获得更好的结果。更重要的是有一个良好的格式和描述性的提示。事实上，在提示中提供示例可以有效地获得特定格式的期望输出。

设计提示时，还要考虑提示的长度，因为语言模型的输入长度有限制。考虑你应该多具体是值得的。提供更多不必要的细节并不一定是好主意。细节应该是相关的，有助于手头的任务。这是你需要大量实验的东西。我们鼓励大量的实验和迭代，以优化你的应用程序的提示。

作为一个例子，让我们试着从一段文本中提取特定信息来试试。
_Prompt:_

```
Extract the name of places in the following text.

Desired format:
Place: <comma_separated_list_of_company_names>

Input: "Although these developments are encouraging to researchers, much is still a mystery. “We often have a black box between the brain and the effect we see in the periphery,” says Henrique Veiga-Fernandes, a neuroimmunologist at the Champalimaud Centre for the Unknown in Lisbon. “If we want to use it in the therapeutic context, we actually need to understand the mechanism.""
```

_Output:_

```
Place: Champalimaud Centre for the Unknown, Lisbon
```

输入文本来源[this Nature article](https://www.nature.com/articles/d41586-023-00509-z).

### 避免不精确

根据上面关于详细性和改进格式的提示，很容易陷入想要对提示过于聪明的陷阱，并可能创建不准确的描述。最好是给出具体直接的提示。这里的类比非常类似于人和人之间的高效沟通--更直接，信息传达的效果就越好。

例如，您可能有兴趣学习提示工程的概念。您可以尝试：

```
Explain the concept prompt engineering. Keep the explanation short, only a few sentences, and don't be too descriptive.
```

该提示并未清晰说明需要使用多少句话以及用什么样的风格。你可能仍然会以上述提示获得不错的回应，但更好的提示应该是非常具体、简洁明了的。诸如：

```
Use 2-3 sentences to explain the concept of prompt engineering to a high school student.
```

### 做还是不做

另一个设计提示的常见技巧是避免说不要做什么，而是说应该做什么。这鼓励更具体和专注于那些能够让模型产生良好反应的细节。
这是一个电影推荐聊天机器人失败的例子，正是由于我编写指令时，专注于不要做什么，导致了它失败。
_Prompt:_

```
The following is an agent that recommends movies to a customer. DO NOT ASK FOR INTERESTS. DO NOT ASK FOR PERSONAL INFORMATION.

Customer: Please recommend a movie based on my interests.
Agent:
```

_Output:_

```
Sure, I can recommend a movie based on your interests. What kind of movie would you like to watch? Do you prefer action, comedy, romance, or something else?
```

一个更好的提示

_Prompt:_

```
The following is an agent that recommends movies to a customer. The agent is responsible to recommend a movie from the top global trending movies. It should refrain from asking users for their preferences and avoid asking for personal information. If the agent doesn't have a movie to recommend, it should respond "Sorry, couldn't find a movie to recommend today.".

Customer: Please recommend a movie based on my interests.
Agent:
```

_Output:_

```
Sorry, I don't have any information about your interests. However, here's a list of the top global trending movies right now: [list of movies]. I hope you find something you like!
```

上面的一些示例摘自[“使用 OpenAI API 进行提示工程的最佳实践”一文。](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api)

[下一节（基本提示）](https://www.prompting.work/post/3)
