# Response to Reviewer 6f5c

This repository will answer the rest of questions posted by Reviewer 6f5c.

$\textbf{Q4:}$ Insufficient interpretability of the TaskReport module.

$\textbf{A4:}$ Thank you for your advice. Due to the space limits, we did not attach our detailed prompting and our figure. So it may cause some confusions in interpretability. 

Next, we will provide more details about our TaskReport. In our TaskReport, we designed a **zero-shot prompting** to LLM models (i.e., Claude Sonnet) to generate the report related to downstream tasks. In order to evaluate the quality of the generated report, we employ different LLM models (i.e., Claude Sonnet 3.5 and GPT-4o) to assess the factuality and clarity. 

Below this link https://anonymous.4open.science/r/TaskReport-4AD5/TaskReport.md provides the detailed prompting of TaskReport and the detailed prompting of **LLM-as-a-Judge** for assessing the quality of the reports. To improve the clarity, we also provide a figure to illustrate the differences between reports generated by human investigators and LLM models. We hope this link can facilitate your understanding of our TaskReport. 

While existing methods can generate reports, our TaskReport module is specifically designed to interpret complex e-commerce relationships learned by RelationEmbed. It provides insights into group-wise behaviors and multi-modal features, which are not typically addressed by general-purpose interpretation methods. We'll emphasize these unique aspects more clearly in the paper.

$\textbf{Q5:}$ Incomplete experimental design: The experimental setup does not specify how the training, validation, and test sets are divided, nor does it mention the source of the dataset used in the experiments, which might lead readers to suspect that a specific dataset was used, possibly causing experimental bias.

$\textbf{A5:}$ Thanks for your comments. While we need to say, these experimental setups including data splitting (**line 617- 619 for Dataset 1 on M1 market, and line 625- 626 for Dataset 2 on  M2 market**) and data details are already introduced in Section 5.1.1. Specifically, for data splitting strategy, **we split the labeled data into three sets, i.e., training dataset, validation dataset, and testing dataset, according to their action time**. Let us take abuser detection data as an example. We collect the time period data from Sept 1st, 2024 to Sept 30th, 2024. If the action date of users and groups before Sept 15th, 2024, then they are considered as labeled abusive data for model training. If the action date of users and groups  is between Sept 15th and Sept 30th, they are considered as validation data. If the action date of users and groups is after Sept 30th, these users and groups are considered as testing data. Due to the privacy issues of customer data, we are unable to disclose more details about that. We hope this explanation can alleviate your concerns.

$\textbf{Q6:}$  Lack of deep analysis in experimental results in Table 1 and Table 2.

$\textbf{A6:}$ Thanks for your suggestions. We will have a deep analysis on the experimental results of two downstream tasks in Tables 1 and 2.  

First of all, RelationEmbed consistently outperforms all baseline methods across different tasks and markets. This consistency demonstrates the model's robustness and generalizability. The reason is that the hypergraph structure and dual-level contrastive learning approach allow RelationEmbed to capture complex relationships that are common across different e-commerce scenarios, regardless of the specific task or market.

Besides, In Table 1, RelationEmbed shows stronger performance in merchant detection compared to customer and group detection. This could indicate that merchant behavior patterns are more distinctive or that the model is particularly effective at capturing merchant-related features. Merchants likely have more consistent and identifiable patterns of behavior across multiple transactions and customer interactions, making their representations easier to learn and distinguish.

Moreover, Table 2 shows that Weight-L2 consistently outperforms Hadamard for link prediction across all models.
The reason can be Weight-L2 operation might be more effective at capturing the relationship between products and customers in the embedding space because it allows for a more nuanced comparison of feature importance. The L2 distance can capture both the magnitude and direction of differences in the embedding space, which may be more relevant for e-commerce relationships than the element-wise multiplication of Hadamard.

I hope these deep analysis can facilitate your understanding of our experiments.


$\textbf{Q7:}$ Unclear result calculation and interpretation: In the experimental results in Table 3, the authors do not explain how the authenticity and clarity metrics were calculated, nor do they clarify how the values in Table 3 were obtained or what they represent.

$\textbf{A7:}$ As discussed in **Lines 896 - 901 in Section 5.3**,  factuality aims to assess whether these statements in the report are correct or not based on the input data (i.e., relation triplets and predicted labels of associated users). clarity aims to evaluate whether the report is clear and easy to understand.  Specifically, factuality and clarity were evaluated on a 1-3 scale by two LLM models (Claude 3 Sonnet 3.5 and GPT-4o) acting as judges. **As discussed in Lines 902 - 905, for each task, 500 reports were generated and evaluated. The values in Table 3 represent the mean scores across these 500 reports, with standard deviations provided.** A score of 1 indicates incorrect/unclear, 2 indicates partially correct/clear, and 3 indicates correct/clear.

$\textbf{Q8:}$ Necessity of using LLMs for interpretability reports.

$\textbf{A8:}$ While it's true that many existing methods can improve interpretability, the use of LLMs in our TaskReport module offers several unique advantages that make it particularly well-suited for our e-commerce representation learning framework. 

First of all, LLMs have a deep understanding of language and context, allowing them to generate reports that consider the nuanced **relationships between merchants, customers, products, and group behaviors** in e-commerce scenarios. This contextual understanding is crucial for interpreting complex patterns learned by RelationEmbed. 

Besides, unlike rule-based or template-based approaches, LLMs can generate reports for a wide variety of scenarios and tasks **without requiring extensive manual configuration.** 

What’s more, LLMs excel at producing human-readable explanations that are more **accessible to non-technical stakeholders**, bridging the gap between complex model outputs and business insights.


We sincerely hope our responses have addressed your concerns. If we have sufficiently addressed all of your concerns in this rebuttal, we would be grateful if you would consider revising your score to reflect this. We welcome any further comments or questions you may have, and we thank you for your thorough review and valuable feedback.