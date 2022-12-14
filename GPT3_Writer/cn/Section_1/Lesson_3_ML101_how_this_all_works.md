


您可能想知道这个东西是如何工作的——准确说，了解它是如何工作的会让您更好地使用它。

*注意：如果您已经知道 GPT-3 的工作原理（深度学习），请随时跳过此部分。*

### GPT-3 背后的基础知识。

您可能听说过 GPT-3 由许多“参数”组成——每个参数都有一个**专用数字**。 当你将一个句子输入 GPT-3 时，它会将该句子与其所有参数结合起来，以预测句子中接下来会发生什么。

GPT-3 拥有**1750 亿个这些参数**并且有 800 GB。

每个参数实际上看起来像这样：

```
output = input * parameter
```



*注意：我在这里大大简化了数学，我们只是想在这里理解概念。 GPT-3 中发生了很多微积分，但是，我现在不想教你关于导数的知识，哈哈。*

所以在上面的例子中，“输入”是我们输入的句子，“参数”也是一个唯一的数字。 **我们收集了 1750 亿个唯一参数的所有输出，将它们组合起来，得到我们的最终输出：完成句子的单词。**

您可能想知道我们如何将一个句子与一堆数字相乘。 基本上，每个句子都被分解成“**tokens**”，句子基本上被转换成一组数字。

GPT-3 有一个它创建的字典，可以将单词片段映射到数字。 例如，单词“gang”可能用“4332”作为标记。

通过这样做，一切都只是 GPT-3 的数字。

它看不到单词、句子等。**它看到的都是数字。**即使它输出一些东西，它也输出为数字——但是，在 Playground 中，它会根据它的自动将标记转换为英语单词 字典。

这太疯狂了——这意味着 GPT-3 不像我们那样理解语言。 相反，它将语言理解为数字的集合以及这些数字与参数之间的关系。

当我们看到“I eat food and I”时，我们知道它的意思，因为我们理解这些词。 因此，我们将知道如何完成句子。

当 GPT-3 看到“I ate food and I”时，它可能会将其视为 *“40222 5332 13211 433 45455”。*它接受这些输入，**将它们与其参数组合**，并输出“*45533 2233 4543” * 完成了“我吃了很好的食物”的句子。

### 参数——GPT-3 的核心

参数在这里似乎很神奇，你就在那里。

GPT-3 到底是怎么知道如何完成句子的？

**好吧，因为参数是在一个数据集上“训练”的，该数据集包括来自整个互联网的大量文本**——维基百科、新闻文章、博客、github repos、twitter、论坛，所有这些东西。 GPT-3 接受了来自互联网的近 5000 亿个令牌的训练。 所有那些 YouTube 评论、所有那些电影评论、所有那些产品登陆页面，GPT-3 都看到了。

那么，根据这些数据“训练”参数是什么意思？

这是我从火影忍者的维基百科页面中摘录的一句话：

```
A powerful fox known as the Nine-Tails attacks Konoha
```



在训练 GPT-3 时，发生的事情是我们**删除**最后一个词，并告诉 GPT-3 预测接下来会发生什么。 例如，在训练期间我们会说：
```
A powerful fox known as the Nine-Tails attacks
```



现在，如果 GPT-3 在这句话的末尾输出“India”，会发生什么？ 好吧，我们需要告诉 GPT-3 它错了！ 但是我们如何告诉 GPT-3——“嘿，你应该说木叶，而不是印度”。

我们在这里所做的是计算“India”和“Konoha”之间的差异——请记住，GPT-3 以数字进行交易。 所以我们可能会说，“嘿，你给了我们 4333 但我们需要 32213”。 我们将差异计算为“错误”。

*请注意：我正在对此进行简化，在幕后发生的用于计算误差的数学运算要复杂得多。 但是，只是想让你从概念上理解它！*

这个错误，然后被用来更新模型中的每个参数——我们告诉 GPT-3 它与正确答案相差 x 量，并稍微调整它的所有参数，这样它接下来更有可能输出正确答案 时间。

这称为“无监督训练”，请参见 [此处](https://jalammar.github.io/images/gpt3/03-gpt3-training-step-back-prop.gif) 的视觉效果。

**这个过程一直持续下去。**

在训练时，我们不断给 GPT-3 **十亿** 的句子来完成，直到它真的非常擅长完成句子。 它一直这样做……在很多文本上持续了很长时间。

有趣的事实：训练 GPT-3 需要大约 500 万美元的 GPU 时间。

### 还有更多的方法。

因为它的 GPT-3 在参数数量方面是巨大的，而且因为用于训练它的数据集非常庞大，我们得到了一些神奇的东西——一个感觉它对语言、上下文、文化和事实知识有真正理解的模型 .

**这是一头受过数十亿互联网用户生成数据训练的野兽。**而且，这也是 GPT-3 如此出色的主要原因之一。 用于训练它的数据集是互联网，它是如此庞大和多样化。

我上面向你解释的实际上是所谓“深度学习”的基础——而且，深度学习是 GPT-3 的核心。

你可能还有很多问题——*这件事背后的数学原理是什么？ 究竟什么是参数，参数如何更新？ 深度学习到底是什么？*

**这是我的建议：继续搞乱 GPT-3 并完成这个构建，不要沉迷于它现在的工作方式。**一旦你完成这个项目，我建议你去 [这里](https://course. fast.ai/Lessons/lesson3.html），如果您好奇的话，可以学习更多关于深度学习的知识。

另外——如果你只是**不明白这个东西是如何工作的/不关心**并且只想使用它，那就太酷了。 我怀疑你们中 99% 的人并不*深刻*理解智能手机中的电路板是如何工作的。 我们大多数人都不在乎！ 我们只想使用我们的智能手机。

没关系。 你不需要全部了解。

只要您了解基本概念，我们就可以开始了！