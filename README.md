# Human-AI Interactive Crossword Solving
This repository contains all logs (json) and visualizations (html) for the crossword solving task from the paper [Evaluating Human-Language Model Interaction](https://arxiv.org/abs/2212.09746), where crowdworkers try to solve a crossword puzzle under 30 minutes with unrestricted help from an "AI Teammate" based on an underlying language model (LM).  If you find this data useful, please consider citing:

```
@article{humanlminteract2022,
  title={Evaluating Human-Language Model Interaction},
  author={Mina Lee and Megha Srivastava and Amelia Hardy and John Thickstun and Esin Durmus and Ashwin Paranjape and Ines Gerard-Ursin and Xiang Lisa Li and Faisal Ladakh and Frieda Rong and Rose E. Wang and Minae Kwon and Joon Sung Park and Hancheng Cao and Tony Lee and Rishi Bommasani and Michael Bernstein and Percy Liang},
  journal={arXiv},
  year={2022},
  volume={abs/2212.09746}
}
```

If you have any questions, please contact Megha Srivastava at megha@cs.stanford.edu! :)

## Overview

We recruit crowdworkers to try to complete an entire crossword puzzle with the ability to query an LM-based “AI Teammate” via a chat-based interface. Players can message the AI Teammate with free-form text, where each individual message is used as the full prompt to the underlying LM. An example visualization with the interface is shown below:

<img width="2000" alt="Crossword Puzzle Interface" src="https://user-images.githubusercontent.com/5402873/224000494-90f9cfd0-f2cb-4ab5-b7be-c1aa3bdfafba.png">

As the example above shows, the crowdworker immediately starts to use well-formed "W" questions to help solve crossword clues, which the text-davinci-001 LM is largely successful at answering, although it struggles (unsurprisingly) to satisfy specified lexical constraints. 

While the visualization (html) shows the final crossword state and entire chat history with the AI Teammate, the logs (json) contain more granular key-stroke events. Specifically, json logs contain the following event types: `NewClueSelected`, `Ask`, `ModelAnswer`, and `CellUpdate`, and the full current crossword state is logged for every event. 

## Data

We collect data and provide logs from crowdworkers interacting with AI Teammates based on 4 different LMs: three variants of OpenAI’s GPT-3 (text-davinci-001, text-babbage-001, and davinci) and AI21's Jurassic-1 (ai21-jumbo), with the following overall counts:


| Language Model | # of Logs | 
| ------------- | ------------- | 
| text-davinci-001 | 88  |
| text-babbage-001 | 82  |
| davinci | 86 |
| ai21-jumbo | 91|

Furthermore, crowdworkers are asked to solve one of 5 different puzzles, with the puzzle ID found in the first past of the filename, such as in this example (puzzle ID 191): `game_191_user_2c3c84df1b7610fa6d5c5089107f6112_model_text-davinci.html`. We use the following mapping from puzzle ID to name in the paper: 

| Puzzle ID | Puzzle Name | 
| ------------- | ------------- | 
| 61 | NYT-1  |
|151 | NYT-2  |
| 173 | ELECT |
| 187 | SIT|
| 191 | LOVE|

All user ID's are replaced with an anonymized hash, and we remove any personal identifiable information (PII) from the released data. 
