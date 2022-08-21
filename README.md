# Machine Readable Repository 

Convert PDF articles to a machine readable form, like XML or JSON.

## Pipeline

The pipelie to convert an article to text

1. Convert PDF to XML
1. Convert XML to JSON

We are using [GROBID](https://github.com/kermitt2/grobid) to convert the article to XML. and then, we convert to XML to [JSON](https://github.com/allenai/s2orc-doc2json)

## Metadata

The metadata for "packaging" the text collection

1. title
1. Authors
1. DOI
1. License
1. Abstract
1. Publish data
1. Journal
1. Arxiv indentifier

## GROBID

Running GROBID as container

```
docker pull lfoppiano/grobid:0.7.1
docker run -t --rm -name grobid_docker -p 8070:8070 lfoppiano/grobid:0.7.1
```

## S2ORC JSON

The S2ORC JSON talks with GROBID via port 8070, so if the container is running, the convertion to JSON will work

```
venv) a-garcm0b@library-elk:~/Work/s2orc-doc2json$ python doc2json/grobid2json/process_pdf.py -i ~/repo2text/in/592545-3873259.pdf \
> -t ~/repo2text/tmp/ -o ~/repo2text/out/
/home/a-garcm0b/repo2text/in/592545-3873259.pdf
runtime: 14.387 seconds
done.
(venv) a-garcm0b@library-elk:~/Work/s2orc-doc2json$
```


