# Fine-tuning mBART and LLaMa3 for text summarization

These repository contains two jupyter notebooks in which you respectively fine-tune **mBART** and **LLaMa3** to perform the task of text-summarization.

## Dataset used
To perform the fine-tuning the Fanpage dataset was used ([https://huggingface.co/datasets/ARTeLab/fanpage](https://huggingface.co/datasets/ARTeLab/fanpage)), which features an average summary length of 1.96 sentences and 43 85 words. Comprising 84.365 rows, this dataset was divided into training (67,492), validation (8,436), and test sets (8,437)

## Metrics adopted

To evaluate the models performance, several metrics were used: ROUGE-1, ROUGE-2, ROUGE-L,
and BLEU. These metrics provided a comprehensive assessment of the model’s accuracy in generating text. Specifically, ROUGE measures the overlap between the generated summary and the reference summary, while BLEU evaluates the generated text against the original text by scoring based on word overlap.

## mBART
The configuration for this model included a batch size of 22 and a micro-batch size of 8, with a training process of 10 epochs. We implemented a warm-up ratio of 0.1 to gradually introduce the learning rate and set the logging steps to 10 for regular updates during training. The gradient accumulation steps were calculated as the integer division of the batch size by the micro-batch size. Our learning rate was set to 1e-7, and we used Torch’s AdamW optimizer. We have set the maximum length of the source sequence to 1024 tokens and the maximum length of the target sequence to 512 tokens.

## LLaMa3
For the LLAMA3 Model the training process lasted 10 epochs, with a batch size per device set to 8 and a total batch size of 32. The total number of training steps was 60. The learning-rate was set to 1e-7, the optimizer used was AdamW and we adopted a number of gradient accumulation steps of 4. Additionaly a maximum sequence length of 6000 tokens was chosen by studying the length of articles and summaries before and after cleaning.

## Result example

**Source**
Come ogni opera d'arte raffinata, Bowlus è il risultato di un design spettacolare e di un'artigianato meticoloso. Non c'è niente al mondo come un'avventura Bowlus. Romanzi epici di viaggi su strada come Travels with Charley di John Steinbeck, On the Road di Jack Kerouac e Blue Highways di William Least Heat-Moon ci lasciano sempre desiderosi di quelle piccole strade e terre pubbliche dimenticate che collegano e intrecciare le nostre narrazioni di viaggio insieme. La nostra ispirazione per il campeggio fuori dalla rete nasce dal desiderio di avventurarci nell'ignoto.

**Target**
Bowlus è un iconico rimorchio in alluminio che oggi rappresenta il camper più sostenibile e tecnologico al mondo. La sua storia risale a più di 90 anni fa e oggi viene reinventata in chiave moderna ed ecologica per offrire la migliore esperienza di viaggio su strada che qualsiasi avventuriero, anche il più esigente, potrebbe desiderare.

**mBART**
Bowlus è il risultato di un design spettacolare e di un'artigianato meticoloso. Non c'è niente al mondo come un'avventura Bowlus

**LLaMa3**
Bowlus road chief, azienda americana produttrice camper e rimorchi d'avventura, riporta in auge l'iconico bowlus ideato quasi 90 anni fa dal designer, ingegnere e costruttore di aerei hawley bowlus. bowlus oggi rappresenta il rimorchio da viaggio più sostenibile e tecnologico al mondo.