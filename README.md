
## Credits

Credits for the base repository go to [this](https://github.com/HendrikStrobelt/detecting-fake-text/) academic team. Credits for the other tools go to Google, Stripe, and OpenAI. I will also take ths opportunity to give thanks to all humans who perform selfless acts for others, in big ways and small. Thank you, please keep doing that.  


## Dependencies

- Flask
- GPT-2 model
- D3.js
- Stripe
- Firebase
- Copyleaks API
- Tensorflow.js

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

