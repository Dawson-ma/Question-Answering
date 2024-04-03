# Question Answering

This project focuses on utilizing BERT for the downstream question answering task, achieving a notable accuracy rate of **84.18%**. The model ranks in the **top 6% out of 1000 teams**.

## Task
The task involves providing answers to questions based on information extracted from a Chinese paragraph. An example scenario includes:

**Paragraph:**  
新加坡、馬來西亞的華文學術界在1970年代後開始統一使用簡體中文；然而繁體字在媒體中普遍存在著，例如華人商店的招牌、舊告示及許多非學術類中文書籍，香港和臺灣所出版的書籍也有在市場上流動。當地許多中文報章都會使用「標題繁體字，內容簡化字」的方式讓簡繁中文並存。除此之外，馬來西亞所有本地中文報章之官方網站都是以繁體中文為主要文字。  
  
**Questions:** 新加坡的華文學術界在哪個年代後開始使用簡體中文？  
**Answer:** 1970  
**Questions:** 馬來西亞的華人商店招牌主要使用什麼文字？  
**Answer:** 繁體字

## Data Preprocessing
1. Conversion of answer's start/end positions in paragraph_text to start/end positions in tokenized_paragraph.
2. Obtaining a single window by slicing the portion of the paragraph containing the answer.
3. Slicing question/paragraph and adding special tokens (101: CLS, 102: SEP).
4. Conversion of answer's start/end positions in tokenized_paragraph to start/end positions in the window.
5. Padding sequence and obtaining inputs to model.

## BERT
The model utilized in this project is [MacBERT](https://huggingface.co/hfl/chinese-macbert-large), which employs similar words for masking purposes instead of using a mask token.

## Training Techniques
- Slicing paragraph into overlapping windows.
- Automatic mixed precision.
- Gradient accumulation.
- Warmup learning rate.
- Polynomial decay scheduler.

## Dataset
The [DRCD](https://github.com/DRCKnowledgeTeam/DRCD) and [ODSQA](https://github.com/Chia-Hsuan-Lee/ODSQA) datasets serve as the primary data sources for this project, accessible [here](https://drive.google.com/file/d/1vtHFad3SndGHF_Vhp-F37DkPy6j1IUOR/view?usp=sharing).

For detailed implementation and usage instructions, please refer to the provided [code](https://github.com/Dawson-ma/Question-Answering/blob/main/QuestionAnswering.ipynb).
