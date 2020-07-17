# Elasticsearch curator

```
docker run --name curator --entrypoint /usr/bin/curator_cli --rm bobrik/curator:5.8.1 --host=192.168.10.6 delete_indices --filter_list '[{"filtertype":"pattern","kind": "prefix","value": "c."},{"filtertype":"age","source":"name","direction":"older","timestring": "%Y.%m.%d","unit":"days","unit_count":5}]'
```
