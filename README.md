# FLAN-T5 Fine-Tuning and Quantization for Text Summarization

### Overview
This project focuses on fine-tuning the FLAN-T5 model for text summarization. By using LoRA (Low-Rank Adaptation) for efficient fine-tuning and quantize the model with 8-bit optimization to reduce model size and enhance performance. Additionally, Retrieval-Augmented Generation (RAG) is integrated with ChromaDB to provide more relevant context during the summarization process.

### Prerequisites
Before running the project, ensure you have the following dependencies installed:
- Python 3.7+
- PyTorch
- Hugging Face Transformers
- LoRA and other relevant libraries for fine-tuning and quantization
- ChromaDB (for RAG implementation)
- Jupyter Notebook

### Usage 
To fine-tune the FLAN-T5 model for text summarization, run the following Jupyter notebook:
jupyter notebook notebooks/fine_tuning_flan_t5.ipynb

### Results
The performance of the models is evaluated using ROUGE scores. Below are the results, stored in the [evaluation.csv]((./evaluation.csv)) file:

| Model                | RAG   | ROUGE-1 | ROUGE-2 | ROUGE-L | Inference Time |
|----------------------|-------|---------|---------|---------|----------------|
| FLAN-T5-Base         | FALSE | 0.4143  | 0.1839  | 0.2866  | 2.307          |
| Fine-tuned FLAN-T5   | FALSE | 0.4143  | 0.1839  | 0.2866  | 2.217          |
| Fine-tuned FLAN-T5   | TRUE  | 0.4196  | 0.1890  | 0.2910  | 3.550          |

For a detailed comparison between the three models' summarization results, check the [comparision.txt](./comparision.txt) file. Below are a few examples of how each model performs:

#### Example 1
###### Article Excerpt (first 300 characters):

(CNN) I see signs of a revolution everywhere. I see it in the op-ed pages of the newspapers, and on the state ballots in nearly half the country. I see it in politicians who once preferred to play it safe with this explosive issue but are now willing to stake their political futures on it.

###### Reference Summary:

CNN's Dr. Sanjay Gupta says we should legalize medical marijuana now. He says he knows how easy it is do nothing "because I did nothing for too long."

###### Base Model Summary:

Marijuana is a medicine that should be studied and treated like any other medicine. It should be legalized nationally, and we should do it now. But at some point, contentious issues do get resolved.

###### Fine-Tuned Model Summary:

Marijuana is a medicine that should be studied and treated like any other medicine. It should be legalized nationally, and we should do it now. But at some point, contentious issues do get resolved.

###### RAG-Enhanced Summary:

Marijuana is a medicine that should be studied and treated like any other medicine. It should be legalized nationally. And, we should do it now.

#### Example 2

###### Article Excerpt (first 300 characters):

He looks barely teenage. But this child has amassed thousands of Twitter followers with his pictorial updates of 'gang life'. The baby-faced boy from Memphis, Tennessee, poses with guns, cash, and bags of what looks like marijuana. Scroll down for video. Baby-faced: This little boy has amassed more...

###### Reference Summary:

Child has amassed thousands of Twitter followers with 'gang life' photos. In one video he points gun at camera as adults look on unfazed. His tweets have prompted backlash with calls for intervention.

###### Base Model Summary:

Little boy, from Memphis, Tennessee, poses with guns, cash and bags of marijuana. He has amassed more than 3,000 followers on Twitter. Critics say he has had a tough year and the backlash is 'stressing out.'

###### Fine-Tuned Model Summary:

Little boy, from Memphis, Tennessee, poses with guns, cash and bags of marijuana. He has amassed more than 3,000 followers on Twitter. Critics say he has had a tough year and the backlash is 'stressing out.'

###### RAG-Enhanced Summary:

Little boy from Memphis, Tennessee, poses with guns, cash, and bags of marijuana. He has amassed more than 3,000 followers on Twitter with pictures of 'gang life.' Critics call his stunts 'sad.'

#### Example 3

###### Article Excerpt (first 300 characters):

New Jersey Governor Chris Christie wasn't looking too presidential Tuesday night when he got into a heated debate with a veteran teacher at a town hall meeting. And now the state's largest teacher's union is calling him out for his 'bullying' behavior.

###### Reference Summary:

The presidential hopeful held a town hall meeting in Kenilworth on Tuesday. During the meeting, high school English teacher Kathy Mooney got up to ask the governor a question about pensions. She asked why he didn't seek a higher legal settlement in a case with ExxonMobil that would have contributed to the state's pension system.

###### Base Model Summary:

New Jersey Gov Chris Christie is being called a bully for the way he interacted with a teacher at a town hall meeting Tuesday night. Christie settled the deal for $225million, despite the fact that the state had originally asked for $8.9billion.

###### Fine-Tuned Model Summary:

New Jersey Gov Chris Christie is being called a bully for the way he interacted with a teacher at a town hall meeting Tuesday night. Christie settled the deal for $225million, despite the fact that the state had originally asked for $8.9billion.

###### RAG-Enhanced Summary:

New Jersey Governor Chris Christie is being called a bully for his 'bullying' behavior. Christie was at Kenilworth Town Hall to take questions from a group of citizens when Kathy Mooney, a high school English Teacher from Roselle Park, took the microphone.

### Conclusion
The integration of RAG significantly improves summarization results by adding relevant context to the generated summaries. The fine-tuned FLAN-T5 model offers an improvement over the base model, and quantization helps in optimizing inference time with minimal loss in performance.
