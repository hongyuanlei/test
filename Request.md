# Request Flow
- Http11NioProtocol
```java
super(new NioEndpoint());
```
- NioEndpoint.run
```
processKey(sk, socketWrapper)
```
- NioEndpoint.processSocket
```java
executor.execute(sc);
```
- SocketProcessorBase.run
- NioEndpoint.SocketProcessor.doRun
```java
 getHandler().process(socketWrapper, event)
```
- (Http11NioProtocol) AbstractProtocol.process
```java
state = processor.process(wrapper, status);
```
- (Http11Processor) AbstractProcessorLight.process
```java
state = service(socketWrapper);
```
- Http11Processor.service
```java
 getAdapter().service(request, response);
```
- CoyoteAdapter.service
```java
 connector.getService().getContainer().getPipeline().getFirst().invoke(
                        request, response);
```
- StandardWrapperValve.invoke
```java
 servlet = wrapper.allocate();

 ApplicationFilterChain filterChain =
                ApplicationFilterFactory.createFilterChain(request, wrapper, servlet);


        filterChain.doFilter(request.getRequest(),
        response.getResponse());
```
- ApplicationFilterChain.doFilter
```java
 servlet.service(request, response);
```

- HttpServlet.service
```java
service(request, response);

```
