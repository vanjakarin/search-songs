# Search songs in elasticsearch

This tutorial lets you index music data (artists and songs) into a local elasticsearch index using logstash. You can search the data using the Kibana dev tools console. 

## Preparations 

1. [Download and install](https://www.elastic.co/downloads) elasticsearch, kibana and logstash.
2. Download a text editor, like [Sublime Text](https://www.sublimetext.com/3) 
3. Clone this repository or download the files 

## Data Import 
1. Go to your elasticsearch installation and start elasticsearch 
   ```
   cd path-to-your-installation/elasticsearch-6.3.1
   bin/elasticsearch (or bin\elasticsearch.bat on Windows) 
    ``` 
2. Go to your Kibana installation and start kibana 
    ```
    cd path-to-your-installation/kibana-6.3.1-darwin-x86_64
    bin/kibana (or bin\kibana.bat on Windows)
    ```
3. Open the **riteband.conf** file and make sure you understand the contents. Update the file path your local path to the **music-xs.csv** file. 
4. Start Logstash using the config file. This will index the data into your local elasticsearch index. 
    ```
   cd path-to-your-installation/logstash-6.3.1
   bin/logstash -f riteband.conf 
    ```
    If it worked, the output in your terminal will be something like this: 
   ![terminal](https://github.com/vanjakarin/search-songs/blob/master/logstash-terminal.png)

## Explore the data 
1. Go to Kibana by pointing your browser to `http://localhost:5601`
2. Go to Dev Tools -> Console 
3. Start executing your queries :) 
     ```
    GET songs/_search
    {
        "query": {
           "match": {
             "title": "you can have it all"
          }
        }
    }
    ```
  


