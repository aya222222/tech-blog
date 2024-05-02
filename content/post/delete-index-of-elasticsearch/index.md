---
title: "How To Delete All Index of Elasticsearch"
description: How to Solve An Error "Wildcard expressions or all indices are not allowed"
date: 2024-05-01
math: 
comments: true
draft: false
tags: 
    - elasticsearch

categories:
    - debugging
    
---


<br><br>

I wanted to delete all index from elasticsearch.

So I did:
```
curl -XDELETE "http://localhost:9200/_all"
```

But got an error: 
```
{"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"Wildcard expressions or all indices are not allowed"}],
"type":"illegal_argument_exception","reason":"Wildcard expressions or all indices are not allowed"},"status":400}
```

So next, I did: 
```
curl -X PUT -u elastic:elastic "http://localhost:9200/_cluster/settings?pretty" -H "Content-Type: application/json" -d "{\"persistent\": {\"action.destructive_requires_name\": false}}"
```

Then it returns:
```
{

  "acknowledged" : true,

  "persistent" : {

    "action" : {

      "destructive_requires_name" : "false"

    }

  },

  "transient" : { }

}
```

Next, I did: 
```
curl -X DELETE "http://localhost:9200/_all"
```
again.

Then it returned: 
```
{"acknowledged":true} 
```

So now all index in elasticsearch was deleted.

