


## Overview 

This is the blog post for  for **TextBrain**, a tool  that automatically grades and validates texts. In order to validate texts, it uses the copyleaks API to check for plagiarism. It also uses a modified version of GPT-2 to detect the likelihood that the text was real or fake. Then it outputs a validation score using these 2 scores. In order to grade the text, it uses a neural network model trained on the automatic essay/text grading dataset on Kaggle found here [here](https://www.kaggle.com/c/asap-aes/data) .Take this project and go build a profitable startup with it...!!!


#### See the full Jupyter Notebook For TextBrain [here](https://github.com/soumyadip1995/TextBrain---Building-an-AI-start-up-using-NLP/blob/master/TextBrain_Building_an_AI_start_up_using_NLP_ipynb.ipynb). 
- #### You can Run the Full Jupyter Notebook In google Colab
#### Read The full Blog post for TextBrain [here](https://soumyadip1995.blogspot.com/2019/05/textbrain-building-ai-startup-using-nlp.html).







## Language Models

![alt_text](http://gltr.io/figs/histogram.png)


In recent years, the natural language processing community has seen the development of increasingly larger and larger language models.

A language model is a machine learning model that is trained to predict the next word given an input context. As such, a model can generate text by generating one word at a time. These predictions can even, to some extent, be constrained by human-provided input to control what the model writes about. Due to their modeling power, large language models have the potential to generate textual output that is indistinguishable from human-written text to a non-expert reader.

Language models achieve this with incredibly accurate distributional estimates of what words may follow in a given context. If a generation system uses a language model and predicts a very likely next words, the generation will look similar to what word a human would have picked in similar situation, despite not having much knowledge about the context itself. This opens up paths for malicious actors to use these tools to generate fake reviews, comments or news articles to influence the public opinion.

To prevent this from happening, we need to develop forensic techniques to detect automatically generated text. We make the assumption that computer generated text fools humans by sticking to the most likely words at each position, a trick that fools humans. In contrast, natural writing actually more frequently selects unpredictable words that make sense to the domain. That means that we can detect whether a text actually looks too likely to be from a human writer!

represents a visually forensic tool to detect text that was automatically generated from large language models.

#### Check Out my blog post on OpenAi's GPT-2 [here](https://soumyadip1995.blogspot.com/2019/02/language-models-unsupervised-multi-task.html)

## Credits

Credits for the base repository go to [this](https://github.com/HendrikStrobelt/detecting-fake-text/) academic team and Siraj Raval. Credits for the other tools go to Google, Stripe, and OpenAI. I will also take ths opportunity to give thanks to all humans who perform selfless acts for others, in big ways and small. Thank you, please keep doing that.  


## Dependencies used

- Flask
- GPT-2 model
- D3.js
- Stripe
- Firebase
- Copyleaks API
- Tensorflow.js

note- D3.js is already integrated

## Quickstart

Install dependencies for Python >3.6 :

```bash
pip install -r requirements.txt
```

run server for `gpt-2-small`:

```bash
python server.py

```

The demo instance now 
## Run the BERT server

start the server for `BERT`:
```bash
python server.py --model BERT
```

the instance runs now at [http://localhost:5001/client/index.html?nodemo](http://localhost:5001/client/index.html?nodemo). HINT: we only provide demo texts for `gpt2-small`.


## server.py options

```
usage: server.py [-h] [--model MODEL] [--nodebug NODEBUG] [--address ADDRESS]
                 [--port PORT] [--nocache NOCACHE] [--dir DIR] [--no_cors]

optional arguments:
  -h, --help         show this help message and exit
  --model MODEL		 choose either 'gpt-2-small' (default) or 'BERT' or your own
  --nodebug NODEBUG  server in non-debugging mode
  --port PORT	     port to launch UI and API (default:5001)
  --no_cors          launch API without CORS support (default: False)

```


## Extend backend

The backend defines a number of model api's that can be invoked by the server by starting it with the parameter `--model NAME`. To add a custom model, you need to write your own api in `backend/api.py` and add the decorator `@register_api(name=NAME)`.

Each api needs to be a class that inherits from `AbstractLanguageChecker`, which defines two functions `check_probabilities` and `postprocess`. Please follow the documentation within `api.py` when implementing the class and the functions.


## Extend frontend
the source code for the front-end is in `client/src`.

To modify, installing of node dependencies is necessary:

```bash
cd client/src; npm install; cd ../..
```
re-compilation of front-end:

```bash
> rm -rf client/dist;cd client/src/; npm run build; cd ../..
```


#### check out the live demo of the GLTR [here](http://gltr.io/dist/index.html)
## Result

![alt_text](https://github.com/soumyadip1995/TextBrain---Building-an-AI-start-up-using-NLP/blob/master/Screenshot%20(151).png?raw=true)
