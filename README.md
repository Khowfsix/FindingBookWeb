# Searching - Suggesting Book Website - DjangoWeb with ElasticSearch

Final Project for Information Retrieval

**Description**: Build a bookstore management website integrated Search Engine using ElasticSearch.
**Role**: Python developer.
**Main Features:**

- Manage, display lists and details with book datasets collected from other bookstore websites.
- Search by relevance of book title, book category, author,... with TFIDF algorithm.
- Filter search results by price, number of pages, publication date and other information.
- Suggest books related to the book you are viewing.
- Autocomplete searching bar with relevant information.

**Technologies:**

- Web application: Django, Bootstrap, SqlLite.
- Data processing: Selenium, ElasticSearch, Kibana.

**Responsibilities:**

- Scrape data from other bookstore websites to get data for analysis.
- Analyze the scraped data and build totems analysis set, ranking set according to each data component.
- Initiate the project and build a bookstore management website.
- Implement the function of suggesting related books by each book and search feature.

**Team:** 4 members.

## Elastic Search

Elasticsearch is an open source data search and analysis engine built on top of Apache Lucene. Elasticsearch allows storing, searching, and analyzing structured and unstructured documents at very high speed and with excellent scalability.

It is widely used in web applications, where Elasticsearch is often used to search and display relevant results to users. Elasticsearch is also a key component of the Elastic Stack ecosystem, which includes applications such as Logstash, Kibana, and Beats, to collect, process, and display log data and other information from systems and applications.

## What is Django web

Django is a web development framework written in Python. It provides developers with a fairly easy approach to developing complex web applications. Django includes many features, including ORM (Object-Relational Mapping), multi-language support, URL handling system, authentication and session management, and several other components that make developing web applications easier. It also has a large open-source development community and has a lot of documentation and libraries available to support development.

Some of the features of Django include:

1. MTV model: Django is built on the MTV (Model-Template-View) model, which helps separate data, logic, and user interface.

2. ORM: Django provides an ORM (Object-Relational Mapping) tool to interact with the database, making it easier for developers to manage data.
3. Multilingual Support: Django supports multilingual application development.

4. Security: Django has built-in security features such as authentication, authorization, and anti-CSRF (Cross-site request forgery).

5. Open source development community: Django has a large development community, so it is easy to find documentation and support libraries.

6. Easy integration with other tools: Django allows easy integration with other tools such as HTML, CSS, JavaScript, jQuery, and Bootstrap.

Django is one of the most popular frameworks in the world and is used by many large companies to develop web applications.

## How to integrate Elastic search into Django web

To integrate Elasticsearch into Django web, you can use some popular libraries such as elasticsearch-dsl and django-elasticsearch-dsl. The basic steps to integrate Elasticsearch into Django web are as follows:

1. Install *Elasticsearch*: To use *Elasticsearch* with Django, you first need to install Elasticsearch. Elasticsearch can be installed on many different operating systems and the latest version can be found on the official Elasticsearch website.
2. Install *elasticsearch-dsl* and *django-elasticsearch-dsl*: These two libraries provide the build classes and tools to interact with Elasticsearch in Django.

```bash
pip install elasticsearch-dsl
pip install django-elasticsearch-dsl

```

3. Set up connection to Elasticsearch: In *[settings.py](http://settings.py/)* of Django application, need to set up connection to Elasticsearch. For example:

```python
ELASTICSEARCH_DSL = {
    'default': {
        'hosts': 'localhost:9200'
    },
}
```

4. Define Elasticsearch models: Create Elasticsearch Model classes with properties to map to fields in Django models.

```python
from django_elasticsearch_dsl import Document
from django_elasticsearch_dsl.registries import registry
from .models import Book

@registry.register_document
class BookDocument(Document):
    class Index:
        # Name of the Elasticsearch index
        name = 'books'
        # See Elasticsearch Indices API reference for available settings
        settings = {'number_of_shards': 1, 'number_of_replicas': 0}

    class Django:
        model = Book # The model associated with this Document

        # The fields of the model you want to be indexed in Elasticsearch
        fields = [
            'title',
            'author',
            'description',
        ]

```

5. Create Views and Search: Create views and search queries to search and display results from Elasticsearch.

These are some basic steps to integrate Elasticsearch into Django web. This integration will help speed up the search and data analysis of your web application.
