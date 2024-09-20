---
layout: blog
---
<span class="post-title">Fine-tuning LLMs for Argument Stance Detection in Unseen Domain</span>

## <span class="section-bar"></span> Abstract

[Stance detection](https://paperswithcode.com/task/stance-detection) is the task of identifying the position or opinion of a speaker or a writer on a given topic. For example, whether they are for or against a certain policy, or whether they agree or disagree with a claim. This is a very useful skill for analyzing social media posts, political debates, and other forms of communication.

In our work, we fine-tuned various Large Language Models (LLMs) through Low-Rank Adaptation (LoRA) for argument stance detection task on twitter datasets, testing how well they generalize on unseen news articles datasets. We find that MISTRAL-7B outperforms other LLMs, as well as the reported baselines.

## <span class="section-bar"></span> Dataset

We used two datasets to train and evaluate our model for stance detection. The first dataset, [SemEval2016](https://aclanthology.org/S16-1003/), contains data from Twitter on six different targets ranging from politics to religion. Each tweet is labeled as either in "Favor", "Neutral" or "Against" the target. The second dataset, [IBM-debater](https://aclanthology.org/E17-1024/), contains claims and evidence manually collected from hundreds of Wikipedia articles targeting 33 controversial topics. We also used a third dataset, consisting of articles about the murder of Samuel Paty, a French teacher who was killed by a terrorist, to demonstrate a real-world application of our model. This dataset was chosen because it relates to sensitive topics such as religious fundamentalism.

## <span class="section-bar"></span> Fine-Tuning

We used Low-Rank Adaptation (LoRA) to fine-tune three large language models (LLMs) for stance detection: MISTRAL-7B, LLAMA-2-7B, and PHI-1.5. We experimented with different values of the LoRA rank hyper-parameter and different proportions of the training set. We also trained and tested our models on both datasets. We found that MISTRAL-7B, was the best performing model for our task, and that it benefited from fine-tuning on both datasets with LoRA rank=16. We also compared the zero-shot performance of MISTRAL-7B with the other LLMs and showed that it was superior to them. Our results demonstrate the effectiveness of LoRA and MISTRAL-7B for stance detection. The performance of the best model (rank=16, trained on both datasets) are reported in the table:

<table style="border-collapse: collapse; font-size: 14px; width: 100%;">
  <tr>
    <th style="border:1px; padding: 8px 5px; text-align: center;"></th>
    <th style="border:1px; padding: 8px 5px; text-align: center;">Abortion</th>
    <th style="border:1px; padding: 8px 5px; text-align: center;">Atheism</th>
    <th style="border:1px; padding: 8px 5px; text-align: center;">Climate change</th>
    <th style="border:1px; padding: 8px 5px; text-align: center;">Feminist movement</th>
    <th style="border:1px; padding: 8px 5px; text-align: center;">Hillary Clinton</th>
    <th style="border:1px; padding: 8px 5px; text-align: center;">SemEval2016 (weighted avg)</th>
    <th style="border:1px; padding: 8px 5px; text-align: center;">IBM-debater (weighted avg)</th>
  </tr>
  <tr>
    <td style="border:1px; padding: 8px 5px; text-align: left;">BERTweet (baseline)</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.65</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.76</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.79</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.65</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.69</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.70</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
  </tr>
  <tr>
    <td style="border:1px; padding: 8px 5px; text-align: left;">RoBERTa (baseline)</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.54</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;"><b>0.79</b></td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.80</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.64</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.71</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.68</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
  </tr>
  <tr>
    <td style="border:1px; padding: 8px 5px; text-align: left;">StanceBERTa (baseline)</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">-</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.61</td>
  </tr>
  <tr>
    <td style="border:1px; padding: 8px 5px; text-align: left;">MISTRAL-7B-INSTRUCT-V0.1 (zero-shot)</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.54</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.33</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.55</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.57</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.66</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.54</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.44</td>
  </tr>
  <tr>
    <td style="border:1px; padding: 8px 5px; text-align: left;">MISTRAL-7B fine-tuned (ours)*</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;"><b>0.71</b></td>
    <td style="border:1px; padding: 8px 5px; text-align: center;">0.73</td>
    <td style="border:1px; padding: 8px 5px; text-align: center;"><b>0.84</b></td>
    <td style="border:1px; padding: 8px 5px; text-align: center;"><b>0.76</b></td>
    <td style="border:1px; padding: 8px 5px; text-align: center;"><b>0.80</b></td>
    <td style="border:1px; padding: 8px 5px; text-align: center;"><b>0.76</b></td>
    <td style="border:1px; padding: 8px 5px; text-align: center;"><b>0.92</b></td>
  </tr>
</table>

## <span class="section-bar"></span> Qualitative Evaluation

We used our best model, which is MISTRAL-7B fine-tuned with LoRA rank=16, to predict the stance of arguments extracted from articles about the murder of Samuel Paty, a French teacher who was killed by a terrorist. We used [RoBERTArg](https://huggingface.co/chkla/roberta-argument), a model trained to detect arguments, to obtain the data. We analyzed the strengths and weaknesses of our model and compared it with the baseline, which predicted “Neutral” most of the time. We experimented with different targets for stance detection, such as “Islam”, “Islamism and fundamentalism are bad for French safety and society”, and “Equality”. We found that our model performed better with the short and general target of “Islam”, but it still had some challenges, such as dealing with implicit arguments, factual statements, and nuanced opinions. We also tried to combine the predictions of the stance towards multiple targets, but we did not find a clear advantage of this approach. We concluded that our model showed promising results on unseen datasets, but it also needed further improvement and investigation.

## <span class="section-bar"></span> Conclusion

In our experiments, we prove MISTRAL-7B to be the best performing LLM for stance detection, working well even in low data regimes. The most interesting finding is its generalizability on an unseen datasets, even outperforming models fine-tuned on SemEval2016 itself for some classes.