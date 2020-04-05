# TEST-LINUX

## test
```bash
FUNCTION_NAME='functions691d03'

hey -c 50 -n 2000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"

hey -c 100 -n 4000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"
```

## results - cold
```
hey -c 50 -n 2000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"

Summary:
  Total:        26.2661 secs
  Slowest:      4.9475 secs
  Fastest:      0.0462 secs
  Average:      0.6307 secs
  Requests/sec: 76.1438
  
  Total data:   26000 bytes
  Size/request: 13 bytes

Response time histogram:
  0.046 [1]     |
  0.536 [1515]  |■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■
  1.026 [18]    |
  1.517 [22]    |■
  2.007 [65]    |■■
  2.497 [335]   |■■■■■■■■■
  2.987 [39]    |■
  3.477 [0]     |
  3.967 [0]     |
  4.457 [2]     |
  4.948 [3]     |


Latency distribution:
  10% in 0.0910 secs
  25% in 0.1175 secs
  50% in 0.1537 secs
  75% in 0.3589 secs
  90% in 2.2558 secs
  95% in 2.3524 secs
  99% in 2.5399 secs

Details (average, fastest, slowest):
  DNS+dialup:   0.0055 secs, 0.0462 secs, 4.9475 secs
  DNS-lookup:   0.0014 secs, 0.0000 secs, 0.0578 secs
  req write:    0.0000 secs, 0.0000 secs, 0.0098 secs
  resp wait:    0.6244 secs, 0.0461 secs, 4.9474 secs
  resp read:    0.0001 secs, 0.0000 secs, 0.0015 secs

Status code distribution:
  [200] 2000 responses
```

## results - warm
```
hey -c 50 -n 2000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"

Summary:
  Total:        3.7540 secs
  Slowest:      0.4663 secs
  Fastest:      0.0438 secs
  Average:      0.0892 secs
  Requests/sec: 532.7659
  
  Total data:   26000 bytes
  Size/request: 13 bytes

Response time histogram:
  0.044 [1]     |
  0.086 [1154]  |■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■
  0.128 [737]   |■■■■■■■■■■■■■■■■■■■■■■■■■■
  0.171 [56]    |■■
  0.213 [3]     |
  0.255 [19]    |■
  0.297 [23]    |■
  0.340 [5]     |
  0.382 [0]     |
  0.424 [0]     |
  0.466 [2]     |


Latency distribution:
  10% in 0.0616 secs
  25% in 0.0703 secs
  50% in 0.0821 secs
  75% in 0.0981 secs
  90% in 0.1158 secs
  95% in 0.1305 secs
  99% in 0.2658 secs

Details (average, fastest, slowest):
  DNS+dialup:   0.0034 secs, 0.0438 secs, 0.4663 secs
  DNS-lookup:   0.0001 secs, 0.0000 secs, 0.0045 secs
  req write:    0.0000 secs, 0.0000 secs, 0.0011 secs
  resp wait:    0.0845 secs, 0.0435 secs, 0.2469 secs
  resp read:    0.0001 secs, 0.0000 secs, 0.0017 secs

Status code distribution:
  [200] 2000 responses
```
