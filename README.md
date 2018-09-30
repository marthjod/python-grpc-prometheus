# python-grpc-prometheus


## ChangeLog


## Installation

Installation from PyPI:  
```
pip install python-grpc-prometheus
```

## Usage

Check the available interceptors in the source code. This example uses the PromServerInterceptor.
Usage example:
```
# Importing this whole package so that I can use prometheus_client.start_http_server()
# instead of just start_http_server(), which is not too descriptive. But it's your call.
import prometheus_client
from python_grpc_prometheus.prometheus_server_interceptor import PromServerInterceptor

<...>
    # Add the required interceptor(s) where you create your grpc server, e.g.
    prometheus_grpc_server_interceptor = PromServerInterceptor()
    server = grpc.server(ThreadPoolExecutor(max_workers=10), interceptors=(prometheus_grpc_server_interceptor,))
    # Start the http server where prometheus can fetch the data from. Use whatever listen port you prefer.
    prometheus_client.start_http_server(8000)
<...>
```

Now, when running your aplication, you can check http://localhost:8000 in a browser.
Note: the grpc_* metrics will just show commented out (with their descriptions) until your application actually receives gRPC calls.


## TODO

- add stream support
- add client metrics
- add test
- add example
