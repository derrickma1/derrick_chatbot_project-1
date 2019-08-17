# derrick_chatbot_project
Chatbot using Telegram and Rasa (with NYTimes API)

# Build Chatbot with Rasa
## Installation
Install latest rasa_NLU
```
pip install rasa_nlu
```
Install latest rasa_core_sdk
```
pip install rasa_core_sdk
```
For dependencies: spaCy+sklearn
```
pip install rasa_nlu[spacy]
python3 -m spacy download en
python3 -m spacy download en_core_web_md
python3 -m spacy link en_core_web_md en
```
Tensorflow (pipeline)
```
pip install rasa_nlu[tensorflow]
```

## Train rasa_nlu
```
python -m rasa_nlu.train -c nlu/nlu_config.yml --data nlu/nlu_data.md -o models --fixed_model_name nlu --project current --verbose
```
to test model you can run
```
python3 nlu_model.py
```

## Train rasa_core
```
python -m rasa_core.train -d core/domain.yml -s core/stories.md -o models/current/dialogue -c policy.yml
```
run below command to run the action (keep it running...)
```
python -m rasa_core_sdk.endpoint --actions actions
```

## Run following code in a new terminal to launch the chatbot
```
python3 -m rasa_core.run -d models/current/dialogue -u models/current/nlu --endpoints endpoints.yml
```

# Run chatbot on Telegram

## Create your new bot
add @botfather in Telegram and follow the bofather's instructions to build your new bot and **remember your token**

## webhook setup
using ngrok or similar tunneling service to create your own server and setup by:
```
https://api.telegram.org/bot{bot token}/setWebhook?url={webhook url}
```
**note: replace the bot token which got from botfather and webhook url got from tunneling service**

## Let's chat!
replace your bot token in main.py and run main.py 
```
python3 main.py
```

