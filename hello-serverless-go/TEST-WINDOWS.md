# TEST-WINDOWS

## test
```bash
FUNCTION_NAME='functions9522be'

hey -c 50 -n 2000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"

hey -c 100 -n 4000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"
```

## results - cold
```
hey -c 50 -n 2000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"

Summary:
  Total:        22.2970 secs
  Slowest:      15.8527 secs
  Fastest:      0.0374 secs
  Average:      0.4499 secs
  Requests/sec: 89.6981
  

Response time histogram:
  0.037 [1]     |
  1.619 [1987]  |■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■
  3.200 [0]     |
  4.782 [0]     |
  6.363 [0]     |
  7.945 [0]     |
  9.527 [0]     |
  11.108 [0]    |
  12.690 [0]    |
  14.271 [0]    |
  15.853 [8]    |


Latency distribution:
  10% in 0.0535 secs
  25% in 0.1266 secs
  50% in 0.2898 secs
  75% in 0.6131 secs
  90% in 0.8218 secs
  95% in 1.0359 secs
  99% in 1.2311 secs

Details (average, fastest, slowest):
  DNS+dialup:   0.0066 secs, 0.0374 secs, 15.8527 secs
  DNS-lookup:   0.0026 secs, 0.0000 secs, 0.1142 secs
  req write:    0.0001 secs, 0.0000 secs, 0.0061 secs
  resp wait:    0.4428 secs, 0.0371 secs, 15.6068 secs
  resp read:    0.0004 secs, 0.0000 secs, 0.0147 secs

Status code distribution:
  [200] 1996 responses

Error distribution:
  [4]   Get https://functions9522be.azurewebsites.net/api/HttpTrigger?name=Aaron: net/http: request canceled (Client.Timeout exceeded while awaiting headers)
```

## results - warm
```
hey -c 50 -n 2000 "https://${FUNCTION_NAME}.azurewebsites.net/api/HttpTrigger?name=Aaron"

Summary:
  Total:        5.0629 secs
  Slowest:      0.5877 secs
  Fastest:      0.0364 secs
  Average:      0.1049 secs
  Requests/sec: 395.0291
  
  Total data:   2210 bytes
  Size/request: 1 bytes

Response time histogram:
  0.036 [1]     |
  0.092 [1290]  |■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■
  0.147 [486]   |■■■■■■■■■■■■■■■
  0.202 [70]    |■■
  0.257 [39]    |■
  0.312 [45]    |■
  0.367 [27]    |■
  0.422 [11]    |
  0.477 [8]     |
  0.533 [13]    |
  0.588 [10]    |


Latency distribution:
  10% in 0.0591 secs
  25% in 0.0703 secs
  50% in 0.0827 secs
  75% in 0.1043 secs
  90% in 0.1596 secs
  95% in 0.2711 secs
  99% in 0.4961 secs

Details (average, fastest, slowest):
  DNS+dialup:   0.0045 secs, 0.0364 secs, 0.5877 secs
  DNS-lookup:   0.0002 secs, 0.0000 secs, 0.0069 secs
  req write:    0.0000 secs, 0.0000 secs, 0.0023 secs
  resp wait:    0.0993 secs, 0.0362 secs, 0.5875 secs
  resp read:    0.0002 secs, 0.0000 secs, 0.0091 secs

Status code distribution:
  [200] 2000 responses
```
