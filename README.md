#### complete rewrite of the original tut by Mervin Praison

[Here is How You Create AI Operating System from Scratch - YouTube](https://www.youtube.com/watch?v=GEQTooW02-E)

[code](https://mer.vin/2024/05/phidata-llm-os/)

issues faced and fixed

1. db_url = "postgresql+psycopg://ai:ai@localhost:5532/ai" fix db_url = "postgresql+psycopg2://ai:ai@localhost:5532/ai"
***edit:*** 
db_url = "postgresql+psycopg://ai:ai@localhost:5532/ai" should work.. just check the following
check if psycopg-binary is installed (pip list) else install (pip install psycopg-binary) 
2. most of us don't have access to gpt-4o hence llm_id="gpt-3.5-turbo" from #llm_id="gpt-4o"
3. export api key creqtes lot of hassels on windows machine hence instead used dotenv with .env file

````
from dotenv import load_dotenv
load_dotenv()  # take environment variables

# api_key=os.environ.get("OPENAI_API_KEY")
# model_name="gpt-3.5-turbo"
# model_name=os.environ.get("OPENAI_MODEL_NAME")```
````
Install the PostgrSQL
```
docker run -d -e POSTGRES_DB=ai -e POSTGRES_USER=ai -e POSTGRES_PASSWORD=ai -e PGDATA=/var/lib/postgresql/data/pgdata -v pgvolume:/var/lib/postgresql/data -p 5532:5432 --name pgvector phidata/pgvector:16
```

#### How to run the PDF Q&A
```
cd aios
conda create -n .llmos python=3.12
conda activate .llmos
pip install -r requirments.txt
# i am installing both psycopg and psycopg2 psycopg-binary==3.1.18 psycopg2-binary
# make sure you have all the keys required in the .env file
python run app.py
```
#### how to run the llm_os phidata
```
# make sure you have all the keys required in the .env file
cd llm_os
pip install -r requirments.txt
streamlit run app.py
```
#### TODO
clean up the code unnecessary lib imported in the example and duplicate of many in llm_os app.py
