# 提示工程实战

在本指南中，我们将介绍一些使用提示工程来现实问题的案例。

主题:

- [PAL（编程辅助语言模型）：代码作为推理](#编程辅助语言模型)
- 即将推出！

## 编程辅助语言模型

[Gao 等人，（2022）]提出了一种使用 LLM 读取自然语言问题并生成作为中间推理步骤的程序的方法。称为程序辅助语言模型（PAL），它和联想提示不同，它不是使用自然语言来获得解决方案，而是将解决方案步骤推送到程序运行时，如 Python 解释器。

![](../img/pal.png)

让我们看一个基于 LangChain 和 gpt3 来例子。开发一个能够通过利用 Python 解释器来解释问题并提供答案的简单应用程序。

具体来说，我们有兴趣创建一个功能，允许使用 LLM 来回答需要日期理解的问题。我们将为 LLM 提供一个包含几个案例的提示，这些案例采用[这里]（https://github.com/reasoning-machines/pal/blob/main/pal/prompt/date_understanding_prompt.py）。

我们需要导入以下内容：

```python
import openai
from datetime import datetime
from dateutil.relativedelta import relativedelta
import os
from langchain.llms import OpenAI
from dotenv import load_dotenv
```

首先，我们来配置一些环境:

```python
load_dotenv()

# API configuration
openai.api_key = os.getenv("OPENAI_API_KEY")

# for LangChain
os.environ["OPENAI_API_KEY"] = os.getenv("OPENAI_API_KEY")
```

设置模型:

```python
llm = OpenAI(model_name='text-davinci-003', temperature=0)
```

设置提示和问题:

```python
question = "Today is 27 February 2023. I was born exactly 25 years ago. What is the date I was born in MM/DD/YYYY?"

DATE_UNDERSTANDING_PROMPT = """
# Q: 2015 is coming in 36 hours. What is the date one week from today in MM/DD/YYYY?
# If 2015 is coming in 36 hours, then today is 36 hours before.
today = datetime(2015, 1, 1) - relativedelta(hours=36)
# One week from today,
one_week_from_today = today + relativedelta(weeks=1)
# The answer formatted with %m/%d/%Y is
one_week_from_today.strftime('%m/%d/%Y')
# Q: The first day of 2019 is a Tuesday, and today is the first Monday of 2019. What is the date today in MM/DD/YYYY?
# If the first day of 2019 is a Tuesday, and today is the first Monday of 2019, then today is 6 days later.
today = datetime(2019, 1, 1) + relativedelta(days=6)
# The answer formatted with %m/%d/%Y is
today.strftime('%m/%d/%Y')
# Q: The concert was scheduled to be on 06/01/1943, but was delayed by one day to today. What is the date 10 days ago in MM/DD/YYYY?
# If the concert was scheduled to be on 06/01/1943, but was delayed by one day to today, then today is one day later.
today = datetime(1943, 6, 1) + relativedelta(days=1)
# 10 days ago,
ten_days_ago = today - relativedelta(days=10)
# The answer formatted with %m/%d/%Y is
ten_days_ago.strftime('%m/%d/%Y')
# Q: It is 4/19/1969 today. What is the date 24 hours later in MM/DD/YYYY?
# It is 4/19/1969 today.
today = datetime(1969, 4, 19)
# 24 hours later,
later = today + relativedelta(hours=24)
# The answer formatted with %m/%d/%Y is
today.strftime('%m/%d/%Y')
# Q: Jane thought today is 3/11/2002, but today is in fact Mar 12, which is 1 day later. What is the date 24 hours later in MM/DD/YYYY?
# If Jane thought today is 3/11/2002, but today is in fact Mar 12, then today is 3/1/2002.
today = datetime(2002, 3, 12)
# 24 hours later,
later = today + relativedelta(hours=24)
# The answer formatted with %m/%d/%Y is
later.strftime('%m/%d/%Y')
# Q: Jane was born on the last day of Feburary in 2001. Today is her 16-year-old birthday. What is the date yesterday in MM/DD/YYYY?
# If Jane was born on the last day of Feburary in 2001 and today is her 16-year-old birthday, then today is 16 years later.
today = datetime(2001, 2, 28) + relativedelta(years=16)
# Yesterday,
yesterday = today - relativedelta(days=1)
# The answer formatted with %m/%d/%Y is
yesterday.strftime('%m/%d/%Y')
# Q: {question}
""".strip() + '\n'
```

```python
llm_out = llm(DATE_UNDERSTANDING_PROMPT.format(question=question))
print(llm_out)
print(born)
```

这将输出：`1998年02月27日`

完整文档 [here](../notebooks/pe-pal.ipynb)

[上一节（高级提示）](https://www.prompting.work/post/4)

[下一节（对抗主题）](https://www.prompting.work/post/5)
