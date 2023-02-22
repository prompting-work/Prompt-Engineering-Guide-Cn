# 高级提示

到这一步，应该很明显，改进提示可以在不同的任务中获得更好的结果。这就是提示工程背后的整个思想。

在我们开始探索更多高级概念之前，让我们正式涵盖一些概念。

主题:

- [少量提示](#few-shot-prompts)
- [联想提示](#chain-of-thought-prompting)
- [零点提示](#zero-shot-cot)
- [自我一致性](#self-consistency)
- [知识生成提示](#generated-knowledge-prompting)
- [自动提示工程师](#automatic-prompt-engineer-ape)

---

## 少量提示

在深入学习更多高级概念之前，让我们回顾一下使用少量提示的例子。

你还记得之前的例子吗，我们提供了下面的任务吗？

```
The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.

A:
```

如果我们再尝试一次，模型将输出以下内容：

```
Yes, the odd numbers in this group add up to 107, which is an even number.
```

再次，这不是正确的回应，这不仅突出了这些系统的局限性，还表明有必要开发更先进的提示工程。
让我们尝试添加一些示例，看看这是否会改善结果。

```
The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
A: The answer is False.

The odd numbers in this group add up to an even number: 17,  10, 19, 4, 8, 12, 24.
A: The answer is True.

The odd numbers in this group add up to an even number: 16,  11, 14, 4, 8, 13, 24.
A: The answer is True.

The odd numbers in this group add up to an even number: 17,  9, 10, 12, 13, 4, 2.
A: The answer is False.

The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.
A:
```

Output

```
The answer is True.
```

这没有奏效。似乎基本的标准提示不足以获得可靠的回应，以解决这类推理问题。上面的例子提供了有关任务的基本信息，即使有例子。如果仔细看看任务，它确实涉及更多的推理步骤。

最近,联想（CoT）提示已被普及用于解决更复杂的算术，常识和符号推理任务。因此，让我们接下来讨论 CoT，看看我们是否可以解决上述任务。

根据[Min 等人（2022）]（https://arxiv.org/abs/2202.12837）的研究结果，以下是在进行少量示范/示例时的一些更多提示：

- 示范指定的输入文本的标签空间和分布都是关键（无论标签是否正确）
- 您使用的格式在性能上也起着关键作用；即使只使用随机标签，也比没有标签要好得多。
- 额外的结果表明，从真实标签分布（而不是均匀分布）中选择随机标签也有帮助。

让我们尝试几个例子。首先尝试一个使用随机标签（意思是将负面和正面标签随机分配给输入）的例子：

```
This is awesome! // Negative
This is bad! // Positive
Wow that movie was rad! // Positive
What a horrible show! //
```

Output

```
Negative
```

即使标签被重新排序，我们仍然能够得到正确的答案。请注意，我们也保持了格式，这也有帮助。事实上，经过进一步的实验，我们正在尝试的新的 GPT 模型似乎变得更加健壮，甚至可以随机调整格式。例子：

```
Positive This is awesome!
This is bad! Negative
Wow that movie was rad!
Positive
What a horrible show! --
```

Output

```
Negative
```

上面的格式没有一致性，但这仍然会影响模型预测正确的标签。我们必须进行更彻底的分析，以确认这对于不同和更复杂的任务是否成立。

---

## Chain-of-Thought Prompting

[Wei 等人(2022)](https://arxiv.org/abs/2201.11903)引入的链式思维(CoT)提示功能可以通过中间推理步骤实现复杂的推理能力。您可以将其与少量提示相结合，以在需要在回应之前进行推理的更复杂的任务上获得更好的结果。

```
The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
A: Adding all the odd numbers (9, 15, 1) gives 25. The answer is False.

The odd numbers in this group add up to an even number: 17,  10, 19, 4, 8, 12, 24.
A: Adding all the odd numbers (17, 19) gives 36. The answer is True.

The odd numbers in this group add up to an even number: 16,  11, 14, 4, 8, 13, 24.
A: Adding all the odd numbers (11, 13) gives 24. The answer is True.

The odd numbers in this group add up to an even number: 17,  9, 10, 12, 13, 4, 2.
A: Adding all the odd numbers (17, 9, 13) gives 39. The answer is False.

The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.
A:
```

Output

```
Adding all the odd numbers (15, 5, 13, 7, 1) gives 41. The answer is False.
```

哇！当我们提供推理步骤时，我们可以看到一个完美的结果。实际上，我们可以通过提供更少的示例来解决这个任务，也就是说，只需一个示例就足够了：

```
The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
A: Adding all the odd numbers (9, 15, 1) gives 25. The answer is False.

The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1.
A:
```

Output

```
Adding all the odd numbers (15, 5, 13, 7, 1) gives 41. The answer is False.
```

记住，作者声称这是一种随着语言模型足够大而出现的自发能力。

---

## 零点提示

最近有一个新的想法是 zero-shot CoT（Kojima et al. 2022）的想法，它基本上涉及在原始提示中添加“让我们一步一步思考”。让我们尝试一个简单的问题，看看模型的表现：

```
我去市场买了 10 个苹果。 我给了邻居 2 个苹果，给了修理工 2 个。 然后我又买了 5 个苹果，吃了 1 个。我还剩下多少个苹果？
```

Output

```
我还剩下12个苹果。
```

答案不正确！现在让我们尝试使用特殊提示。

```
我去市场买了 10 个苹果。 我给了邻居 2 个苹果，给了修理工 2 个。 然后我又买了 5 个苹果，吃了 1 个。我还剩下多少个苹果？

让我们一步一步地思考。
```

Output

```
首先，我们买了 10 个苹果。

给邻居 2 个：10 - 2 = 8

给修理工 2 个：8 - 2 = 6

买了 5 个：6 + 5 = 11

吃了 1 个：11 - 1 = 10

所以，我还剩下 10 个苹果。
```

实际上，这个简单的提示在这项任务中表现出色。在提示中没有太多示例可用的情况下，这尤其有用。

---

## 自我一致性

也许，在提示工程中，自我一致性是最先进的技术之一。由[Wang et al.（2022）]（https://arxiv.org/pdf/2203.11171.pdf）提出，自我一致性旨在“取代用于链式思维提示的天真贪婪解码”。这个想法是通过少量的CoT采样多个不同的推理路径，并使用生成来选择最一致的答案，从而帮助提高链式思维提示在涉及算术和常识推理的任务中的性能。

下面这个算术推理的例子，我们来试试吧。

```
When I was 6 my sister was half my age. Now
I’m 70 how old is my sister?
```

Output

```
35
```

输出显然是错误的！我们如何利用自发一致性来改进它呢？让我们尝试一下。我们将使用 Wang 等人 2022 年（表 17）的少样本例子：

```
Q: There are 15 trees in the grove. Grove workers will plant trees in the grove today. After they are done,
there will be 21 trees. How many trees did the grove workers plant today?
A: We start with 15 trees. Later we have 21 trees. The difference must be the number of trees they planted.
So, they must have planted 21 - 15 = 6 trees. The answer is 6.

Q: If there are 3 cars in the parking lot and 2 more cars arrive, how many cars are in the parking lot?
A: There are 3 cars in the parking lot already. 2 more arrive. Now there are 3 + 2 = 5 cars. The answer is 5.

Q: Leah had 32 chocolates and her sister had 42. If they ate 35, how many pieces do they have left in total?
A: Leah had 32 chocolates and Leah’s sister had 42. That means there were originally 32 + 42 = 74
chocolates. 35 have been eaten. So in total they still have 74 - 35 = 39 chocolates. The answer is 39.

Q: Jason had 20 lollipops. He gave Denny some lollipops. Now Jason has 12 lollipops. How many lollipops
did Jason give to Denny?
A: Jason had 20 lollipops. Since he only has 12 now, he must have given the rest to Denny. The number of
lollipops he has given to Denny must have been 20 - 12 = 8 lollipops. The answer is 8.

Q: Shawn has five toys. For Christmas, he got two toys each from his mom and dad. How many toys does
he have now?
A: He has 5 toys. He got 2 from mom, so after that he has 5 + 2 = 7 toys. Then he got 2 more from dad, so
in total he has 7 + 2 = 9 toys. The answer is 9.

Q: There were nine computers in the server room. Five more computers were installed each day, from
monday to thursday. How many computers are now in the server room?
A: There are 4 days from monday to thursday. 5 computers were added each day. That means in total 4 * 5 =
20 computers were added. There were 9 computers in the beginning, so now there are 9 + 20 = 29 computers.
The answer is 29.

Q: Michael had 58 golf balls. On tuesday, he lost 23 golf balls. On wednesday, he lost 2 more. How many
golf balls did he have at the end of wednesday?
A: Michael initially had 58 balls. He lost 23 on Tuesday, so after that he has 58 - 23 = 35 balls. On
Wednesday he lost 2 more so now he has 35 - 2 = 33 balls. The answer is 33.

Q: Olivia has $23. She bought five bagels for $3 each. How much money does she have left?
A: She bought 5 bagels for $3 each. This means she spent 5

Q: When I was 6 my sister was half my age. Now I’m 70 how old is my sister?
A:
```

Output 1:

```
When I was 6 my sister was half my age, so she was 3. Now I am 70, so she is 70 - 3 = 67. The answer is 67.
```

Output 2:

```
When the narrator was 6, his sister was half his age, which is 3. Now that the narrator is 70, his sister would be 70 - 3 = 67 years old. The answer is 67.
```

Output 3:

```
When I was 6 my sister was half my age, so she was 3. Now I am 70, so she is 70/2 = 35. The answer is 35.
```

计算最终答案需要几个步骤（查看论文以获取详细信息），但为了简单起见，我们可以清楚地看到已经出现了多数答案，因此最终答案就应该是这个。

---

## 知识生成提示

大模型不断改进，其中一种流行的技术包括能够结合知识或信息以帮助模型做出更准确的预测的能力。

使用类似的想法，模型也可以用来在做出预测前生成知识吗？这就是[Liu 等人 2022 年]（https://arxiv.org/pdf/2110.08387.pdf）论文所尝试的——生成要用作提示的知识。特别是，这对于常识推理等任务有多大帮助？

让我们试试一个简单的提示：

```
Part of golf is trying to get a higher point total than others. Yes or No?
```

Output

```
Yes.
```

这种错误暴露了 LLMs 在执行需要更多关于世界的知识的任务时的局限性。我们如何通过知识生成来改善此情况？

首先我们生成一些“知识”：

```
Input: Greece is larger than mexico.
Knowledge: Greece is approximately 131,957 sq km, while Mexico is approximately 1,964,375 sq km, making Mexico 1,389% larger than Greece.

Input: Glasses always fog up.
Knowledge: Condensation occurs on eyeglass lenses when water vapor from your sweat, breath, and ambient humidity lands on a cold surface, cools, and then changes into tiny drops of liquid, forming a film that you see as fog. Your lenses will be relatively cool compared to your breath, especially when the outside air is cold.

Input: A fish is capable of thinking.
Knowledge: Fish are more intelligent than they appear. In many areas, such as memory, their cognitive powers match or exceed those of ’higher’ vertebrates including non-human primates. Fish’s long-term memories help them keep track of complex social relationships.

Input: A common effect of smoking lots of cigarettes in one’s lifetime is a higher than normal chance of getting lung cancer.
Knowledge: Those who consistently averaged less than one cigarette per day over their lifetime had nine times the risk of dying from lung cancer than never smokers. Among people who smoked between one and 10 cigarettes per day, the risk of dying from lung cancer was nearly 12 times higher than that of never smokers.

Input: A rock is the same size as a pebble.
Knowledge: A pebble is a clast of rock with a particle size of 4 to 64 millimetres based on the Udden-Wentworth scale of sedimentology. Pebbles are generally considered larger than granules (2 to 4 millimetres diameter) and smaller than cobbles (64 to 256 millimetres diameter).

Input: Part of golf is trying to get a higher point total than others.
Knowledge:
```

Knowledge 1:

```
The objective of golf is to play a set of holes in the least number of strokes. A round of golf typically consists of 18 holes. Each hole is played once in the round on a standard golf course. Each stroke is counted as one point, and the total number of strokes is used to determine the winner of the game.
```

Knowledge 2:

```
Golf is a precision club-and-ball sport in which competing players (or golfers) use many types of clubs to hit balls into a series of holes on a course using the fewest number of strokes. The goal is to complete the course with the lowest score, which is calculated by adding up the total number of strokes taken on each hole. The player with the lowest score wins the game.
```

我们正在使用 [Liu 等人在论文中提供的提示。 2022](https://arxiv.org/pdf/2110.08387.pdf)。

下一步是整合知识并做出预测。 我将问题重新格式化为 QA 格式以指导答案格式。

```
Question: Part of golf is trying to get a higher point total than others. Yes or No?

Knowledge: The objective of golf is to play a set of holes in the least number of strokes. A round of golf typically consists of 18 holes. Each hole is played once in the round on a standard golf course. Each stroke is counted as one point, and the total number of strokes is used to determine the winner of the game.

Explain and Answer:
```

Answer 1 (高置信度):

```
No, the objective of golf is not to get a higher point total than others. Rather, the objective is to play a set of holes in the least number of strokes. The total number of strokes is used to determine the winner of the game, not the total number of points.
```

```
Question: Part of golf is trying to get a higher point total than others. Yes or No?

Knowledge: Golf is a precision club-and-ball sport in which competing players (or golfers) use many types of clubs to hit balls into a series of holes on a course using the fewest number of strokes. The goal is to complete the course with the lowest score, which is calculated by adding up the total number of strokes taken on each hole. The player with the lowest score wins the game.

Explain and Answer:
```

Answer 2 (低置信度):

```
Yes, part of golf is trying to get a higher point total than others. Each player tries to complete the course with the lowest score, which is calculated by adding up the total number of strokes taken on each hole. The player with the lowest score wins the game.
```

有些非常有趣的事情发生在这个例子中。在第一个答案中，模型非常有信心，但在第二个答案中却不是那么有信心。我简化了这个过程以便演示，但在得出最终答案时，还有很多细节需要考虑。更多细节可以参考论文。

---

## 自动提示工程师 (APE)

![](../img/APE.png)

[Zhou et al., (2022)](https://arxiv.org/abs/2211.01910) 提出了自动提示工程师(APE)框架，用于自动指令生成和选择。将指令生成问题框架化为自然语言综合，并作为一个黑盒优化问题，使用 LLMs 来生成和搜索候选解决方案。选择问题被提出为强化学习问题，以从生成的池中选择最佳指令。

首先要使用一个大型语言模型（作为推理模型），给定输出示例以生成某项任务的指令候选者。这些候选解决方案将指导搜索过程。指令是使用目标模型执行的，然后根据计算出的评估分数选择最合适的指令。

APE 发现了比 Kojima 等人（2022）提出的人工设计的“让我们一步一步思考”提示更好的零点 CoT 提示。

提示“让我们一步一步地解决这个问题，以确保我们得出正确的答案。”引发链式思维，提高了 MultiArith 和 GSM8K 基准测试的性能。

![](../img/ape-zero-shot-cot.png)

本文涉及了一个重要的主题，即自动优化提示的概念。虽然我们在本指南中没有深入讨论这个主题，但如果您对此感兴趣，这里有几篇关键论文：

- [AutoPrompt](https://arxiv.org/abs/2010.15980) - 提出了一种基于梯度引导搜索自动为各种任务创建提示的方法。
- [Prefix Tuning](https://arxiv.org/abs/2101.00190) - 一种轻量级的微调替代方案，可以为 NLG 任务预先添加可训练的连续前缀。
- [Prompt Tuning](https://arxiv.org/abs/2104.08691) - 提出了一种通过反向传播学习软提示的机制。

---

[上一节（基本提示）](./prompts-basic-usage.md)

[下一节（对抗提示）](./prompt-adversarial.md)
