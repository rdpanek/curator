# Elasticsearch curator

```
docker run --name curator --entrypoint /usr/bin/curator_cli --rm bobrik/curator:5.8.1 --host=192.168.10.6 delete_indices --filter_list '[{"filtertype":"pattern","kind": "prefix","value": "c."},{"filtertype":"age","source":"creation_date","direction":"older","unit":"minutes","unit_count":10}]'
```
