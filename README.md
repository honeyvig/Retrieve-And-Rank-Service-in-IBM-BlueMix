# Retrieve-And-Rank-Service-in-IBM-BlueMix
IBM IBM Cloud (formerly known as IBM Bluemix) provides various services to help with cloud development, including a Retrieve and Rank service that is used for building and deploying search engines. The Retrieve and Rank service allows you to rank documents based on their relevance to a given query, making it useful for applications like search engines and recommendation systems.

The IBM Retrieve and Rank service combines a search engine with ranking models. It can be used to rank and retrieve information in a way that is customized for your application.
Steps to Use Retrieve and Rank Service on IBM Cloud:

    Create a Retrieve and Rank Service on IBM Cloud:
        Sign in to your IBM Cloud account at IBM Cloud.
        From the IBM Cloud dashboard, click on "Create Resource."
        Search for Retrieve and Rank and create a new instance of the service.
        After the service is created, you'll be provided with credentials to access the service (API keys, URL, etc.).

    Set up the IBM Watson SDK: IBM provides SDKs in different languages, including Python, to interact with their services. In this example, we will use the Python SDK.

    Python Code to Interact with IBM Retrieve and Rank:
        First, install the necessary Python package for interacting with IBM Cloud services:

    pip install watson-developer-cloud

    Basic Code Example to Use IBM Retrieve and Rank:

Here’s an example code that demonstrates how to interact with the IBM Retrieve and Rank service to rank documents based on a query.

from watson_developer_cloud import RetrieveAndRankV1
import json

# Initialize the Retrieve and Rank service client
retrieve_and_rank = RetrieveAndRankV1(
    username='YOUR_IBM_CLOUD_USERNAME', # Replace with your username
    password='YOUR_IBM_CLOUD_PASSWORD', # Replace with your password
    version='2016-05-19'
)

# Set the Retrieve and Rank service credentials
credentials = {
    'username': 'YOUR_IBM_CLOUD_USERNAME',
    'password': 'YOUR_IBM_CLOUD_PASSWORD',
    'url': 'YOUR_SERVICE_URL'
}

# Replace with the actual collection name and ranking model name
collection_name = 'your-collection-name'
ranking_model_name = 'your-ranking-model'

# Sample document data
document = {
    'id': '1',
    'title': 'IBM Watson',
    'body': 'IBM Watson is an AI platform that allows you to build cognitive applications.'
}

# Index the document
response = retrieve_and_rank.index_document(collection_name, document)
print('Document indexed:', response)

# Create a search query
query = 'AI platform'

# Perform a query and retrieve ranked results
query_response = retrieve_and_rank.query(collection_name, query=query, ranking_model=ranking_model_name)
print('Query results:')
print(json.dumps(query_response, indent=2))

Explanation of the Code:

    Install Watson SDK: We begin by importing the watson_developer_cloud library, which allows us to interact with IBM Watson services.

    RetrieveAndRankV1 Initialization: We create an instance of the RetrieveAndRankV1 class, providing it with the required authentication information (username, password, and API endpoint).

    Document Indexing:
        The index_document method is used to index documents. In this example, we have a document with an ID, title, and body text.
        The response will contain information about the indexed document.

    Search Query:
        We perform a query (query = 'AI platform') on the collection and retrieve the ranked results.
        The results are returned in a structured JSON format, which we print to display.

Key Components:

    Collection Name: A collection in IBM Retrieve and Rank holds the indexed documents. You should replace your-collection-name with your actual collection name.
    Ranking Model: The ranking model is used to rank the results based on their relevance to the query. Replace your-ranking-model with your ranking model name.
    Document Indexing: You need to index your documents before running a query. Each document is a JSON object that must include an id, and other fields that will be used to rank the documents.
    Querying: After indexing documents, you can send queries to retrieve the documents ranked according to relevance.

Setup Instructions:

    Replace with IBM Cloud Credentials:
        Replace YOUR_IBM_CLOUD_USERNAME and YOUR_IBM_CLOUD_PASSWORD with your actual IBM Cloud credentials.
        Replace 'YOUR_SERVICE_URL' with the service URL obtained from your IBM Retrieve and Rank instance.

    Replace with Collection and Ranking Model Names:
        Make sure you use the correct collection and ranking model that you created in the IBM Cloud Retrieve and Rank service.

    Document and Query:
        Replace the sample document with your actual documents to index.
        Change the query to test different search scenarios.

Example Output:

If you have indexed a set of documents and executed a query, the output would look something like this:

Query results:
{
  "docs": [
    {
      "id": "1",
      "title": "IBM Watson",
      "body": "IBM Watson is an AI platform that allows you to build cognitive applications.",
      "score": 3.8
    },
    {
      "id": "2",
      "title": "AI Technologies",
      "body": "AI technologies are rapidly evolving, enabling new ways to solve problems.",
      "score": 2.9
    }
  ]
}

In the output, the documents are ranked by relevance to the query, with the highest-scoring documents listed first.
Conclusion:

This Python code demonstrates how to interact with IBM's Retrieve and Rank service to index documents and perform search queries with ranking. By using the IBM Watson Developer Cloud SDK, you can easily integrate this functionality into your application for creating powerful search engines or recommendation systems.
