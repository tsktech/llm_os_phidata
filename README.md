#### complete rewrite of the original tut by Mervin Praison

[Here is How You Create AI Operating System from Scratch - YouTube](https://www.youtube.com/watch?v=GEQTooW02-E)

[code](https://mer.vin/2024/05/phidata-llm-os/)

issues faced and fixed

1. db_url = "postgresql+psycopg://ai:ai@localhost:5532/ai" fix db_url = "postgresql+psycopg2://ai:ai@localhost:5532/ai"
2. most of us don't have access to gpt-4o hence llm_id="gpt-3.5-turbo" from #llm_id="gpt-4o"
3. export api key creqtes lot of hassels on windows machine hence instead used dotenv with .env file

````
from dotenv import load_dotenv
load_dotenv()  # take environment variables

# api_key=os.environ.get("OPENAI_API_KEY")
# model_name="gpt-3.5-turbo"
# model_name=os.environ.get("OPENAI_MODEL_NAME")```
````

#### TODO
clean up the code unnecessary lib imported in the example and duplicate of many in llm_os app.py
