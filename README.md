# 提示工程指南

这份指南包含了一系列有关提示工程的最新论文、学习指南和工具。该仓库旨在为实践者和开发者提供研究和教育参考，但不能完整列出主题所有的资源。

提示工程是一门相对较新的学科，旨在开发和优化提示，以有效地使用语言模型（LMs）用于各种应用和研究课题。提示工程技能有助于更好地了解大型语言模型（LLMs）的功能和局限性。研究人员利用提示工程来提高 LLMs 在各种常见和复杂任务（如问答和算术推理）上的能力。开发人员使用提示工程来设计与 LLMs 和其他工具接口的稳健有效的提示技术。

受到开发 LLM 的高度兴趣的推动，我们创建了这本新的提示工程指南，其中包含了所有与提示工程相关的最新论文、学习指南、讲座、参考资料和工具。

🎉 提示工程讲座正在此处直播！[笔记本](https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/notebooks/pe-lecture.ipynb)和[幻灯片](https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/lecture/Prompt-Engineering-Lecture-Elvis.pdf)皆包含其中。

- [加入我们的 Discord](https://discord.gg/SKgkVT8BGJ)
- [关注我们的推特](https://twitter.com/dair_ai)
- [关注知乎专栏](https://www.zhihu.com/column/c_1611777728105156608)

---

## Table of Contents

- [Lecture](#lecture)
- [Guides](#guides)
- [Papers](#papers)
- [Tools & Libraries](#tools--libraries)
- [Datasets](#datasets)
- [Blog, Guides, Tutorials and Other Readings](#blog-guides-tutorials-and-other-readings)

## 目录

- [讲座](#lecture)
- [指南](#guides)
- [论文](#papers)
- [工具和库](#tools--libraries)
- [数据集](#datasets)
- [博客、指南、教程和其他阅读](#blog-guides-tutorials-and-other-readings)

---

## 讲座

我们发布了一个 1 小时的讲座，提供了对提示技术，应用程序和工具的全面概述。

- [视频讲座](https://youtu.be/dOxUroR57xs)
- [带有代码的笔记本](https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/notebooks/pe-lecture.ipynb)
- [幻灯片](https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/lecture/Prompt-Engineering-Lecture-Elvis.pdf)

---

## 指南

以下是我们开发的提示工程指南。 指南正在研发中。

- [提示工程-介绍](/guides/prompts-intro.md)
- [提示工程-基本提示](/guides/prompts-basic-usage.md)
- [提示工程-高级提示](/guides/prompts-advanced-usage.md)
- [提示工程-对抗提示](/guides/prompt-adversarial.md)
- [提示工程-杂项主题](/guides/prompt-miscellaneous.md)

---

## 论文

以下是关于提示工程的最新论文（按发布日期排序）。我们每天更新这些论文，并添加新的论文。我们每周都会将这些论文的摘要添加到上面的指南中：

- 调查/概述：

  - [增强语言模型的探索](https://arxiv.org/abs/2302.07842)（2023 年 2 月）
  - [上下文学习调查](https://arxiv.org/abs/2301.00234)（2022 年 12 月）
  - [朝着大型语言模型的推理：一项调查](https://arxiv.org/abs/2212.10403)（2022 年 12 月）
  - [大型语言模型的新兴能力](https://arxiv.org/abs/2206.07682)（2022 年 6 月）
  - [文本到图像生成的提示修饰器分类](https://arxiv.org/abs/2204.13988)（2022 年 4 月）
  - [训练、提示和预测：自然语言处理中提示方法的系统调查](https://arxiv.org/abs/2107.13586)（2021 年 7 月）

- 技术/方法：

  - [可扩展的语言模型半监督学习提示生成](https://arxiv.org/abs/2302.09236)（2023 年 2 月）
  - [通过提示约束界定大型语言模型在开放文本生成中的能力范围](https://arxiv.org/abs/2302.09185)（2023 年 2 月）
  - [À-la-carte Prompt Tuning（APT）：通过可组合的提示结合不同的数据](https://arxiv.org/abs/2302.07994)（2023 年 2 月）
  - [GraphPrompt：图形神经网络的预训练和下游任务的统一](https://arxiv.org/abs/2302.08043)（2023 年 2 月）
  - [大型语言模型在道德自我纠正中的能力](https://arxiv.org/abs/2302.07459)（2023 年 2 月）
  - [SwitchPrompt：为低资源域中的分类学习领域特定的门控软提示](https://arxiv.org/abs/2302.06868)（2023 年 2 月）
  - [评估离散提示的鲁棒性](https://arxiv.org/abs/2302.05619) (Feb 2023)
  - [上下文学习的组合示例](https://arxiv.org/abs/2302.05698) (Feb 2023)
  - [硬提示变得容易：基于梯度的离散优化用于提示调整和发现](https://arxiv.org/abs/2302.03668) (Feb 2023)
  - [多模态连锁思维推理在语言模型中](https://arxiv.org/abs/2302.00923) (Feb 2023)
  - [大型语言模型容易被无关的上下文分散注意力](https://arxiv.org/abs/2302.00093) (Feb 2023)
  - [合成提示：为大型语言模型生成思维演示](https://arxiv.org/abs/2302.00618) (Feb 2023)
  - [渐进提示：语言模型的持续学习](https://arxiv.org/abs/2301.12314) (Jan 2023)
  - [批处理提示：LLM API 的高效推理](https://arxiv.org/abs/2301.08721) (Jan 2023)
  - [再想想，让我们不要一步一步地思考！零点推理中的偏见和毒性](https://arxiv.org/abs/2212.08061) (Dec 2022)
  - [宪政 AI：来自 AI 反馈的无害性](https://arxiv.org/abs/2212.08073) (Dec 2022)
  - [连续提示：解决复杂问题](https://arxiv.org/abs/2212.04092) (Dec 2022)
  - [通过模型编写的评估发现语言模型行为](https://arxiv.org/abs/2212.09251) (Dec 2022)
  - [结构提示：将上下文学习扩展至 1000 个例子](https://arxiv.org/abs/2212.06713) (Dec 2022)
  - [PAL：程序辅助语言模型](https://arxiv.org/abs/2211.10435) (Nov 2022)
  - [大型语言模型是人类级别的提示工程师](https://arxiv.org/abs/2211.01910) (Nov 2022)
  - [忽略先前提示：语言模型的攻击技术](https://arxiv.org/abs/2211.09527) (Nov 2022)
  - [机器生成文本：威胁模型和检测方法的综合研究](https://arxiv.org/abs/2210.07321) (Nov 2022)
  - [通过上下文学习教授算法推理](https://arxiv.org/abs/2211.09066) (Nov 2022)
  - [通过自然语言推理增强预训练语言模型的自我一致性和性能](https://arxiv.org/abs/2211.11875) (Nov 2022)
  - [随便问问：提示语言模型的简单策略](https://paperswithcode.com/paper/ask-me-anything-a-simple-strategy-for) (Oct 2022)
  - [ReAct：在语言模型中协同推理和行动](https://arxiv.org/abs/2210.03629) (Oct 2022)
  - [提示 GPT-3 可靠](https://arxiv.org/abs/2210.09150) (Oct 2022)
  - [分解提示：解决复杂任务的模块化方法](https://arxiv.org/abs/2210.02406) (Oct 2022)
  - [语言模型是贪婪的推理者：思路链的系统形式分析](https://arxiv.org/abs/2210.01240v3) (Oct 2022)
  - [通过手工设计的对抗性例子评估预先训练语言模型的易感性](https://arxiv.org/abs/2209.02128)（2022 年 9 月）
  - [Promptagator：从 8 个例子中获取少量的密集检索](https://arxiv.org/abs/2209.11755)（2022 年 9 月）
  - [推动语言模型变得更好的推理者](https://arxiv.org/abs/2206.02336)（2022 年 6 月）
  - [大型语言模型是零点推理者](https://arxiv.org/abs/2205.11916)（2022 年 5 月）
  - [MRKL 系统：一种模块化的神经符号架构，结合大型语言模型，外部知识源和离散推理](https://arxiv.org/abs/2205.00445)（2022 年 5 月）
  - [通过生成提示的毒性检测](https://arxiv.org/abs/2205.12390)（2022 年 5 月）
  - [学习转移提示以用于文本生成](https://arxiv.org/abs/2205.01543)（2022 年 5 月）
  - [少量提示的文本推理说明的不可靠性](https://arxiv.org/abs/2205.03401)（2022 年 5 月）
  - [用于文本到图像生成的提示修改器分类](https://arxiv.org/abs/2204.13988)（2022 年 4 月）
  - [PromptChainer：通过可视化编程链接大型语言模型提示](https://arxiv.org/abs/2203.06566)（2022 年 3 月）
  - [自我一致性提高语言模型的思路链推理](https://arxiv.org/abs/2203.11171)（2022 年 3 月）
  - [使用人类反馈训练语言模型以执行指令](https://arxiv.org/abs/2203.02155)
  - [重新审视示范的作用：什么使上下文学习成功？](https://arxiv.org/abs/2202.12837)（2022 年 2 月）
  - [想法链接提示引发大型语言模型的推理](https://arxiv.org/abs/2201.11903)（2022 年 1 月）
  - [展示你的工作：与语言模型中间计算的暂存器](https://arxiv.org/abs/2112.00114)（2021 年 11 月）
  - [基于生成知识提示的常识推理](https://arxiv.org/abs/2110.08387)（2021 年 10 月）

  - [多任务提示训练可实现零射击任务泛化](https://arxiv.org/abs/2110.08207) (Oct 2021)
  - [重构指令提示以适应 GPTk 的语言](https://arxiv.org/abs/2109.07830) (Sep 2021)
  - [文本到图像生成模型的设计准则](https://arxiv.org/abs/2109.06977) (Sep 2021)
  - [使预训练语言模型成为更好的少样本学习器](https://aclanthology.org/2021.acl-long.295) (Aug 2021)
  - [神奇有序的提示及其位置：克服少量提示顺序敏感性](https://arxiv.org/abs/2104.08786) (April 2021)
  - [BERTese：学会与 BERT 交谈](https://aclanthology.org/2021.eacl-main.316) (April 2021)
  - [参数有效的提示调整的规模之力](https://arxiv.org/abs/2104.08691) (April 2021)
  - [大型语言模型的提示编程：超越少量提示范式](https://arxiv.org/abs/2102.07350) (Feb 2021)
  - [使用前校准：提高语言模型的少样本性能](https://arxiv.org/abs/2102.09690) (Feb 2021)
  - [前缀调整：优化用于生成的连续提示](https://arxiv.org/abs/2101.00190) (Jan 2021)
  - [AutoPrompt：通过自动生成的提示从语言模型中提示知识](https://arxiv.org/abs/2010.15980) (Oct 2020)
  - [语言模型是少量学习者](https://arxiv.org/abs/2005.14165) (May 2020)
  - [我们如何知道语言模型知道什么？](https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00324/96460/How-Can-We-Know-What-Language-Models-Know) (July 2020)

- 应用：

  - [格林童话：使用 Midjourney 进行提示工程以诠释童话故事](https://arxiv.org/abs/2302.08961) (2023 年 2 月)
  - [LabelPrompt：有效的基于提示的关系分类学习](https://arxiv.org/abs/2302.08068) (2023 年 2 月)
  - [深度神经网络的提示调整，用于说话人适应的视觉语音识别](https://arxiv.org/abs/2302.08102) (2023 年 2 月)
  - [大型语言模型中的道德自我纠正能力](https://arxiv.org/abs/2302.07459) (2023 年 2 月)
  - [多模态仇恨 Meme 分类的提示](https://arxiv.org/abs/2302.04156) (2023 年 2 月)
  - [PLACES：提示语言模型以合成社交对话](https://arxiv.org/abs/2302.03269) (2023 年 2 月)
  - [基于常识的提示，用于可控的移情对话生成](https://arxiv.org/abs/2302.01441) (2023 年 2 月)
  - [爬取语言模型的内部知识库](https://arxiv.org/abs/2301.12810) (2023 年 1 月)
  - [法律提示工程，用于多语言法律判断预测](https://arxiv.org/abs/2212.02199) (2022 年 12 月)
  - [探索扩散模型中的提示工程](https://arxiv.org/abs/2211.15462) (2022 年 11 月)
  - [学习解释：通过思维链进行多模态推理，用于科学问题解答](https://arxiv.org/abs/2209.09513v2) (2022 年 9 月)
  - [与 Copilot 交谈：探索使用自然语言解决 CS1 问题的提示工程](https://arxiv.org/abs/2210.15157) (2022 年 10 月)
  - [驾驶 Copilot 和 Codex：高温、低提示，还是黑魔法？](https://arxiv.org/abs/2210.14699) (2022 年 10 月)
  - [从头开始编写情节预训练语言模型](https://aclanthology.org/2022.inlg-main.5) (2022 年 7 月)

- 集合：
  - [思维链论文](https://github.com/Timothyxxx/Chain-of-ThoughtsPapers)
  - [带代码的论文](https://paperswithcode.com/task/prompt-engineering)
  - [提示论文](https://github.com/thunlp/PromptPapers#papers)

---

## 工具 & 库

#### (按名称排序)

- [AI 测试厨房](https://aitestkitchen.withgoogle.com)
- [更好的提示](https://github.com/krrishdholakia/betterprompt)
- [DreamStudio](https://beta.dreamstudio.ai)
- [DUST](https://dust.tt)
- [Dyno](https://trydyno.com)
- [EveryPrompt](https://www.everyprompt.com)
- [GPT 索引](https://github.com/jerryjliu/gpt_index)
- [GPTTools](https://gpttools.com/comparisontool)
- [hwchase17/对抗性提示](https://github.com/hwchase17/adversarial-prompts)
- [交互式作曲探索器](https://github.com/oughtinc/ice)
- [LangChain](https://github.com/hwchase17/langchain)
- [LearnGPT](https://www.learngpt.com)
- [Lexica](https://lexica.art)
- [织轴](https://github.com/socketteer/loom)
- [Metaprompt](https://metaprompt.vercel.app/?task=gpt)
- [OpenAI playground](https://beta.openai.com/playground)
- [OpenPrompt](https://github.com/thunlp/OpenPrompt)
- [Playground](https://playgroundai.com)
- [Prodia](https://app.prodia.com/#/)
- [Prompt Base](https://promptbase.com)
- [Prompt Engine](https://github.com/microsoft/prompt-engine)
- [OpenAI 的 DALL-E 2 的提示生成器](http://dalle2-prompt-generator.s3-website-us-west-2.amazonaws.com)
- [Promptable](https://promptable.ai)
- [PromptInject](https://github.com/agencyenterprise/PromptInject)
- [Prompts.ai](https://github.com/sevazhidkov/prompts-ai)
- [PromptSource](https://github.com/bigscience-workshop/promptsource)
- [Scale SpellBook](https://scale.com/spellbook)
- [sharegpt](https://sharegpt.com)
- [ThoughtSource](https://github.com/OpenBioLink/ThoughtSource)
- [可视提示构建器](https://tools.saxifrage.xyz/prompt)

---

## 数据集

#### (按名称排序)

- [Anthropic 的 Red Team 数据集](https://github.com/anthropics/hh-rlhf/tree/master/red-team-attempts), [(paper)](https://arxiv.org/abs/2209.07858)
- [Awesome ChatGPT 提示](https://huggingface.co/datasets/fka/awesome-chatgpt-prompts)
- [DiffusionDB](https://github.com/poloclub/diffusiondb)
- [Midjourney Prompts](https://huggingface.co/datasets/succinctly/midjourney-prompts)
- [P3 - 公共提示池](https://huggingface.co/datasets/bigscience/P3)
- [PartiPrompts](https://parti.research.google)
- [Real Toxicity Prompts](https://allenai.org/data/real-toxicity-prompts)
- [Stable Diffusion Dataset](https://huggingface.co/datasets/Gustavosta/Stable-Diffusion-Prompts)
- [WritingPrompts](https://www.reddit.com/r/WritingPrompts)

---

## 博客、指南、教程和其他文章

#### (按名称排序)

- [3 Principles for prompt engineering with GPT-3](https://www.linkedin.com/pulse/3-principles-prompt-engineering-gpt-3-ben-whately)
- [A beginner-friendly guide to generative language models - LaMBDA guide](https://aitestkitchen.withgoogle.com/how-lamda-works)
- [A Complete Introduction to Prompt Engineering for Large Language Models](https://www.mihaileric.com/posts/a-complete-introduction-to-prompt-engineering)
- [A Generic Framework for ChatGPT Prompt Engineering](https://medium.com/@thorbjoern.heise/a-generic-framework-for-chatgpt-prompt-engineering-7097f6513a0b)
- [AI Content Generation](https://www.jonstokes.com/p/ai-content-generation-part-1-machine)
- [Awesome ChatGPT Prompts](https://github.com/f/awesome-chatgpt-prompts)
- [Best 100+ Stable Diffusion Prompts](https://mpost.io/best-100-stable-diffusion-prompts-the-most-beautiful-ai-text-to-image-prompts)
- [Best practices for prompt engineering with OpenAI API](https://help.openai.com/en/articles/6654000-best-practices-for-prompt-engineering-with-openai-api)
- [Building GPT-3 applications — beyond the prompt](https://medium.com/data-science-at-microsoft/building-gpt-3-applications-beyond-the-prompt-504140835560)
- [ChatGPT, AI and GPT-3 Apps and use cases](https://gpt3demo.com)
- [CMU Advanced NLP 2022: Prompting](https://youtube.com/watch?v=5ef83Wljm-M&feature=shares)
- [Curtis64's set of prompt gists](https://gist.github.com/Curtis-64)
- [DALL·E 2 Prompt Engineering Guide](https://docs.google.com/document/d/11WlzjBT0xRpQhP9tFMtxzd0q6ANIdHPUBkMV-YB043U/edit#)
- [DALL·E 2 Preview - Risks and Limitations](https://github.com/openai/dalle-2-preview/blob/main/system-card.md)
- [DALLE Prompt Book](https://dallery.gallery/the-dalle-2-prompt-book)
- [DALL-E, Make Me Another Picasso, Please](https://www.newyorker.com/magazine/2022/07/11/dall-e-make-me-another-picasso-please?)
- [Diffusion Models: A Practical Guide](https://scale.com/guides/diffusion-models-guide)
- [Exploiting GPT-3 Prompts](https://twitter.com/goodside/status/1569128808308957185)
- [Exploring Prompt Injection Attacks](https://research.nccgroup.com/2022/12/05/exploring-prompt-injection-attacks)
- [Extrapolating to Unnatural Language Processing with GPT-3's In-context Learning: The Good, the Bad, and the Mysterious](http://ai.stanford.edu/blog/in-context-learning)
- [Generative AI with Cohere: Part 1 - Model Prompting](https://txt.cohere.ai/generative-ai-part-1)
- [Giving GPT-3 a Turing Test](https://lacker.io/ai/2020/07/06/giving-gpt-3-a-turing-test.html)
- [GPT3 and Prompts: A quick primer](https://buildspace.so/notes/intro-to-gpt3-prompts)
- [How to Draw Anything](https://andys.page/posts/how-to-draw)
- [How to get images that don't suck](https://www.reddit.com/r/StableDiffusion/comments/x41n87/how_to_get_images_that_dont_suck_a)
- [How to write good prompts](https://andymatuschak.org/prompts)
- [Introduction to Reinforcement Learning with Human Feedback](https://www.surgehq.ai/blog/introduction-to-reinforcement-learning-with-human-feedback-rlhf-series-part-1)
- [In defense of prompt engineering](https://simonwillison.net/2023/Feb/21/in-defense-of-prompt-engineering/)
- [Language Models and Prompt Engineering: Systematic Survey of Prompting Methods in NLP](https://youtube.com/watch?v=OsbUfL8w-mo&feature=shares)
- [Learn Prompting](https://learnprompting.org)
- [Methods of prompt programming](https://generative.ink/posts/methods-of-prompt-programming)
- [Mysteries of mode collapse](https://www.lesswrong.com/posts/t9svvNPNmFf5Qa3TA/mysteries-of-mode-collapse)
- [NLP for Text-to-Image Generators: Prompt Analysis](https://heartbeat.comet.ml/nlp-for-text-to-image-generators-prompt-analysis-part-1-5076a44d8365)
- [NLP with Deep Learning CS224N/Ling284 - Lecture 11: Promting, Instruction Tuning, and RLHF](http://web.stanford.edu/class/cs224n/slides/cs224n-2023-lecture11-prompting-rlhf.pdf)
- [Notes for Prompt Engineering by sw-yx](https://github.com/sw-yx/ai-notes)
- [OpenAI Cookbook](https://github.com/openai/openai-cookbook)
- [OpenAI Prompt Examples for several applications](https://platform.openai.com/examples)
- [Pretrain, Prompt, Predict - A New Paradigm for NLP](http://pretrain.nlpedia.ai)
- [Prompt Engineering 101 - Introduction and resources](https://www.linkedin.com/pulse/prompt-engineering-101-introduction-resources-amatriain)
- [Prompt Engineering 101: Autocomplete, Zero-shot, One-shot, and Few-shot prompting](https://youtube.com/watch?v=v2gD8BHOaX4&feature=shares)
- [Prompt Engineering 101](https://humanloop.com/blog/prompt-engineering-101)
- [Prompt Engineering - A new profession ?](https://www.youtube.com/watch?v=w102J3_9Bcs&ab_channel=PatrickDebois)
- [Prompt Engineering by co:here](https://docs.cohere.ai/docs/prompt-engineering)
- [Prompt Engineering by Microsoft](https://microsoft.github.io/prompt-engineering)
- [Prompt Engineering: The Career of Future](https://shubhamsaboo111.medium.com/prompt-engineering-the-career-of-future-2fb93f90f117)
- [Prompt engineering davinci-003 on our own docs for automated support (Part I)](https://www.patterns.app/blog/2022/12/21/finetune-llm-tech-support)
- [Prompt Engineering Guide: How to Engineer the Perfect Prompts](https://richardbatt.co.uk/prompt-engineering-guide-how-to-engineer-the-perfect-prompts)
- [Prompt Engineering in GPT-3](https://www.analyticsvidhya.com/blog/2022/05/prompt-engineering-in-gpt-3)
- [Prompt Engineering Template](https://docs.google.com/spreadsheets/d/1-snKDn38-KypoYCk9XLPg799bHcNFSBAVu2HVvFEAkA/edit#gid=0)
- [Prompt Engineering Topic by GitHub](https://github.com/topics/prompt-engineering)
- [Prompt Engineering: From Words to Art](https://www.saxifrage.xyz/post/prompt-engineering)
- [Prompt Engineering with OpenAI's GPT-3 and other LLMs](https://youtube.com/watch?v=BP9fi_0XTlw&feature=shares)
- [Prompt injection attacks against GPT-3](https://simonwillison.net/2022/Sep/12/prompt-injection)
- [Prompt injection to read out the secret OpenAI API key](https://twitter.com/ludwig_stumpp/status/1619701277419794435?s=20&t=GtoMlmYCSt-UmvjqJVbBSA)
- [Prompting in NLP: Prompt-based zero-shot learning](https://savasy-22028.medium.com/prompting-in-nlp-prompt-based-zero-shot-learning-3f34bfdb2b72)
- [Prompting Methods with Language Models and Their Applications to Weak Supervision](https://snorkel.ai/prompting-methods-with-language-models-nlp)
- [Prompts as Programming by Gwern](https://www.gwern.net/GPT-3#prompts-as-programming)
- [Reverse Prompt Engineering for Fun and (no) Profit](https://lspace.swyx.io/p/reverse-prompt-eng)
- [So you want to be a prompt engineer: Critical careers of the future](https://venturebeat.com/ai/so-you-want-to-be-a-prompt-engineer-critical-careers-of-the-future/)
- [Simulators](https://www.lesswrong.com/posts/vJFdjigzmcXMhNTsx/simulators)
- [Start with an Instruction](https://beta.openai.com/docs/quickstart/start-with-an-instruction)
- [Talking to machines: prompt engineering & injection](https://artifact-research.com/artificial-intelligence/talking-to-machines-prompt-engineering-injection)
- [the Book - Fed Honeypot](https://fedhoneypot.notion.site/25fdbdb69e9e44c6877d79e18336fe05?v=1d2bf4143680451986fd2836a04afbf4)
- [The ChatGPT Prompt Book](https://docs.google.com/presentation/d/17b_ocq-GL5lhV_bYSShzUgxL02mtWDoiw9xEroJ5m3Q/edit#slide=id.gc6f83aa91_0_79)
- [Using GPT-Eliezer against ChatGPT Jailbreaking](https://www.alignmentforum.org/posts/pNcFYZnPdXyL2RfgA/using-gpt-eliezer-against-chatgpt-jailbreaking)
- [What Is ChatGPT Doing … and Why Does It Work?](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/)

---

如果你认为缺少了什么，欢迎提交一个 PR。也欢迎反馈和建议。
