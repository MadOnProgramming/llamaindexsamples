llm
--------------
	-AI trained on massive datasets of text and code
	-Two types
		-Open source
			- cost effective
			- can be deployed in our own infrastructure(private cloud, on-premises)
			- security needs to be implemented by us
			ex: model from hugging face
				llama2 model from facebook
		-Proprietary
			openAI chatgpt4

Terme:
-------------
	Tokens
		- all these models works on tokens rather than words
	
	Prompts
		- is the inital instruction given to the model
	
	Context window
		- is the maximum number of tokens the model can handle at once

	Temperature
		- controls the randomness of the model output
		higher the value - output will be more random
		lower the value - output will be focused and deterministic

	Hallucinations
		- model is making things up
	
	Fine-Tune
		- is a process of training a already trained model is further trained on a specialized
		dataset to make it adopt at a particular task.
		- fine tune can be expensive, so this is where RAG pattern and llama index are here to help

Which one to use Fine-tune/Training/RAG?
-------------------------------------------
	1)training a base model with new data 
		(here model quality will be higher/but cost is also higher)
	2)RAG uses prompt engineering to supplement or guide the model in real time
		-is like a onspot learning without fine-tune costs/ very economical for business to use llms
		-guids llm using addition data in the form of prompts
		-RAG integrates a fact-verification components into your existing models
		-you can update ur model without the additional expenses
		-you can customize the model with our specific business data

keywords
----------------------
chatbots
smart agents
smart workflows

Concept
---------
	RAG-Retrieval Augumented Generation
	--------------------------------------
		-combines llm models with the custom data
		-the new data will be broken down to smaller segment as chunks, llamaindex calls them nodes.
		-llamaindex transforms data into various indexes, the most common of them is vector index
		where nodes are embedded into vectors for most efficient search
		-transformed data is stored in an easily accessible location where is can be easily queried
		-Two stages
			1)indexing
					-Ingests data from various sources through data connectors
					-this ingesting data represented as documents and nodes where a node represents
					as a chunk of a source document
					-then llamaindex indexes the data in a format thats easy to retrieve with a vector index
			2)quering
					-in the quering stage, llamaindex retreives context(relevant content) from the knowledge base 
					based on the user query
					-this context(relevant content) is then passed to an LLM along with the user query to 
					generate a response

LangChain vs llamaindex
---------------------------
	common capabilities
	-----------------------
		question answering or chat over specific documents
		they can be used to build chatbots
		they both make agents that can be different things
		they can interact with different APIs
	
	llamaindex
	-----------
		its an interface between LLM and external data sources
		(LLM ---- llamaIndex ---- external data sources)

	LangChain
	----------
		its a framework for building and managing LLM powered applications.

Varaious llm in the market
------------------------------
1)GPT4 - accuracy,1.5 trillion parameters, paid
2)LLama2 - best in open source llm
3)orca - by microsoft, designed to run on laptop
4)claude - best for coding , largest context window
5)gpt3.5 - good with somne haullicination
6)lambda - by google brain
7)palm 2 - by google
8)openai codex - best for coding , used in copilot
9)cohere - robust 
10)alpaca-7b by standford - can function locally
11)Gopher by Deepmind -math ,science,humanity, medicine

Data connectors
	- are used to connect to the data source where our custom data is available
	- data loaders are available in llama hub
	- we can also write our own data loaders

Node parsers
	- Its the process of chunking data from document to smaller chunks of data called nodes.
	- We can configure the node parsers and tell the chunk size in tokens and overlap between chunked nodes.

chunking
	- Its the process done by TokenTextSplitter
	- by default, chunk size - 1024 and overlap - 20 tokens

Entire process-
------------------------------
Documents are chunked and pased into node(light weight) objects

								   Node Parsers
DATA SORUCE-------<<data loader>>---------->DOCUMENT/NODES--------<<Indexing>>-------->Index

         			llamahub										Embdedding/
		 		simpleDirReader									   vector stores


Vector store options - pinecone(cloud only),chroma(self hosted only),weavite(cloud and self hosted)


Querying
----------------
contains
	retreivers
		retreivers are responsible for getting data from the data sources
	node processors
		for data transformation
	response synthesizers
		gives the final result to the llm for the response
	
	routers
		responsible for decision making between different data sources
		two types of data sources
			-llm selectors
			-pydantic selectors


Tokenization
---------------
tokenization is done by "Byte Pair Encoding"
One Token = 4 characters in english

Various types of embeddings
----------------------------------
Word embeddings
	- they get the word level meaning, good for text classification, sentiment analysis & named entity recognition
Sentence/Document embeddings
	- gets the meaning of whole Sentence level instead of word level.
	- used for more general purpose (overall meaning)
Transformer based embeddings
	- they are derived from transformer models can be used for various NLP tasks. but costly
TFIDF embeddings
	- gives more weight to more important words in document while ignoring common/unimportant words
Instructor embeddings
	- not just gives important to words but also to context 
	- used for context aware scenarios
	- deeper understanding of text



create a virtual environment for your project
-------------------------------------------------
	python3 -m venv myenv


activate ur environment
-----------------------------------
	./myenv/Scripts/activate


install llama-index plugin
-----------------------------------
	pip install llama-index


as we will loaders and tools from llama-hub, install it
--------------------------------------------------------
	pip install llama-hub

plugin for openai, by default llama index uses openai, but we can change it to other llms
---------------------------------------------------------------------------------------------
	pip install openai


openai api key i created
------------------------------
privatekey - madhansekar@llmlearning
apikey - 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

get all packages in an environment in a text file
---------------------------------------------------
pip freeze > requirements.txt

install all packages in one shot
------------------------------------
pip install -r requirements.txt