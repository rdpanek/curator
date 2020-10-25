# Elasticsearch curator

**Send data to elasticsearch**

Index
```
{{elastic.cluster}}:{{elastic.port}}/c.report-2020.07.02/c.report
```

Payload
```
{
  "uuid": "123456",
  "seleniumCluster": "192.168.10.6",
  "baseUrl": "http://clash-of-teststack.cz/",
  "capabilities": {
    "maxInstances": 1,
    "browserName": "chrome"
  },
  "event": "testStart",
  "sessionId": "b7d85ed01232328132ac5397c4ae536a",
  "sequence": 1,
  "env": "localhost",
  "spec": "./tests/tesla/smoke.js",
  "timestamp": "2020-07-02T12:51:48.063Z"
}
```


**Example: Remove 5 days old indices**
```
docker run --name curator --entrypoint /usr/bin/curator_cli --rm bobrik/curator:5.8.1 --host=192.168.10.6 delete_indices --filter_list '[{"filtertype":"pattern","kind": "prefix","value": "c."},{"filtertype":"age","source":"name","direction":"older","timestring": "%Y.%m.%d","unit":"days","unit_count":5}]'
```

**Example2: Remove 5 days old lindices from Elastic cloud**
```
docker run --name curator --entrypoint /usr/bin/curator_cli --rm bobrik/curator:5.8.1 --host=https://06d9ccc239fb44d291e4146233598b0b.us-central1.gcp.cloud.es.io --port=9243 --http_auth='elastic:s5wX1QtfCQJ19uHFQ2MOTyJ2' delete_indices --filter_list '[{"filtertype":"pattern","kind": "prefix","value": "c."},{"filtertype":"age","source":"name","direction":"older","timestring": "%Y.%m.%d","unit":"minutes","unit_count":5}]'
```
