Example: Apache Tomcat
======================

### Run

```console
$ docker-compose up
```

### Spring Boot

Spring Boot (>=2.2) does not expose MBeans by default. You need to set the following property to enable Tomcat MBeans.

```
server.tomcat.mbeanregistry.enabled=true
```

Also, as the domain part of the MBean name is changed to `Tomcat` in the embedded Tomcat (not `Catalina` as in standalone Tomcat),
you need to modify the exporter configuration as well.

### Response Example

```console
$ curl -s "localhost:9639/metrics?include_timestamp=false&include_help=false" | awk '/^Catalina/ || /^Users/'
Catalina_Connector_acceptCount{port="8080",} 100
Catalina_Connector_allowTrace{port="8080",} 0
Catalina_Connector_connectionLinger{port="8080",} -1
Catalina_Connector_connectionTimeout{port="8080",} 20000
Catalina_Connector_enableLookups{port="8080",} 0
Catalina_Connector_keepAliveTimeout{port="8080",} 20000
Catalina_Connector_localPort{port="8080",} 8080
Catalina_Connector_maxHeaderCount{port="8080",} 100
Catalina_Connector_maxKeepAliveRequests{port="8080",} 100
Catalina_Connector_maxParameterCount{port="8080",} 10000
Catalina_Connector_maxPostSize{port="8080",} 2097152
Catalina_Connector_maxSavePostSize{port="8080",} 4096
Catalina_Connector_maxSwallowSize{port="8080",} 2097152
Catalina_Connector_maxThreads{port="8080",} 200
Catalina_Connector_minSpareThreads{port="8080",} 10
Catalina_Connector_port{port="8080",} 8080
Catalina_Connector_portOffset{port="8080",} 0
Catalina_Connector_portWithOffset{port="8080",} 8080
Catalina_Connector_processorCache{port="8080",} 200
Catalina_Connector_proxyPort{port="8080",} 0
Catalina_Connector_redirectPort{port="8080",} 8443
Catalina_Connector_redirectPortWithOffset{port="8080",} 8443
Catalina_Connector_secure{port="8080",} 0
Catalina_Connector_tcpNoDelay{port="8080",} 1
Catalina_Connector_threadPriority{port="8080",} 5
Catalina_Connector_useBodyEncodingForURI{port="8080",} 0
Catalina_Connector_useIPVHosts{port="8080",} 0
Catalina_Connector_xpoweredBy{port="8080",} 0
Catalina_Deployer_copyXML{host="localhost",} 0
Catalina_Deployer_deployXML{host="localhost",} 1
Catalina_Deployer_unpackWARs{host="localhost",} 1
Catalina_Engine_backgroundProcessorDelay 10
Catalina_Engine_startChildren 1
Catalina_Engine_startStopThreads 1
Catalina_GlobalRequestProcessor_bytesReceived{name="http-nio-8080",} 0
Catalina_GlobalRequestProcessor_bytesSent{name="http-nio-8080",} 1364
Catalina_GlobalRequestProcessor_errorCount{name="http-nio-8080",} 2
Catalina_GlobalRequestProcessor_maxTime{name="http-nio-8080",} 18
Catalina_GlobalRequestProcessor_processingTime{name="http-nio-8080",} 19
Catalina_GlobalRequestProcessor_requestCount{name="http-nio-8080",} 2
Catalina_Host_autoDeploy{host="localhost",} 1
Catalina_Host_backgroundProcessorDelay{host="localhost",} -1
Catalina_Host_copyXML{host="localhost",} 0
Catalina_Host_createDirs{host="localhost",} 1
Catalina_Host_deployOnStartup{host="localhost",} 1
Catalina_Host_deployXML{host="localhost",} 1
Catalina_Host_startChildren{host="localhost",} 1
Catalina_Host_startStopThreads{host="localhost",} 1
Catalina_Host_undeployOldVersions{host="localhost",} 0
Catalina_Host_unpackWARs{host="localhost",} 1
Catalina_ProtocolHandler_acceptCount{port="8080",} 100
Catalina_ProtocolHandler_acceptorThreadCount{port="8080",} 1
Catalina_ProtocolHandler_acceptorThreadPriority{port="8080",} 5
Catalina_ProtocolHandler_allowHostHeaderMismatch{port="8080",} 0
Catalina_ProtocolHandler_aprRequired{port="8080",} 0
Catalina_ProtocolHandler_compressionMinSize{port="8080",} 2048
Catalina_ProtocolHandler_connectionCount{port="8080",} 1
Catalina_ProtocolHandler_connectionLinger{port="8080",} -1
Catalina_ProtocolHandler_connectionTimeout{port="8080",} 20000
Catalina_ProtocolHandler_connectionUploadTimeout{port="8080",} 300000
Catalina_ProtocolHandler_desiredBufferSize{port="8080",} -1
Catalina_ProtocolHandler_disableUploadTimeout{port="8080",} 1
Catalina_ProtocolHandler_keepAliveTimeout{port="8080",} 20000
Catalina_ProtocolHandler_localPort{port="8080",} 8080
Catalina_ProtocolHandler_maxConnections{port="8080",} 8192
Catalina_ProtocolHandler_maxExtensionSize{port="8080",} 8192
Catalina_ProtocolHandler_maxHeaderCount{port="8080",} 100
Catalina_ProtocolHandler_maxHttpHeaderSize{port="8080",} 8192
Catalina_ProtocolHandler_maxKeepAliveRequests{port="8080",} 100
Catalina_ProtocolHandler_maxSavePostSize{port="8080",} 4096
Catalina_ProtocolHandler_maxSwallowSize{port="8080",} 2097152
Catalina_ProtocolHandler_maxThreads{port="8080",} 200
Catalina_ProtocolHandler_maxTrailerSize{port="8080",} 8192
Catalina_ProtocolHandler_minSpareThreads{port="8080",} 10
Catalina_ProtocolHandler_nameIndex{port="8080",} 1
Catalina_ProtocolHandler_noCompressionStrongETag{port="8080",} 1
Catalina_ProtocolHandler_paused{port="8080",} 0
Catalina_ProtocolHandler_pollerThreadCount{port="8080",} 1
Catalina_ProtocolHandler_pollerThreadPriority{port="8080",} 5
Catalina_ProtocolHandler_port{port="8080",} 8080
Catalina_ProtocolHandler_portOffset{port="8080",} 0
Catalina_ProtocolHandler_portWithOffset{port="8080",} 8080
Catalina_ProtocolHandler_processorCache{port="8080",} 200
Catalina_ProtocolHandler_rejectIllegalHeader{port="8080",} 1
Catalina_ProtocolHandler_rejectIllegalHeaderName{port="8080",} 1
Catalina_ProtocolHandler_sSLDisableCompression{port="8080",} 1
Catalina_ProtocolHandler_sSLDisableSessionTickets{port="8080",} 0
Catalina_ProtocolHandler_sSLEnabled{port="8080",} 0
Catalina_ProtocolHandler_sSLHonorCipherOrder{port="8080",} 0
Catalina_ProtocolHandler_sSLVerifyDepth{port="8080",} 10
Catalina_ProtocolHandler_secure{port="8080",} 0
Catalina_ProtocolHandler_selectorTimeout{port="8080",} 1000
Catalina_ProtocolHandler_sendfileSupported{port="8080",} 1
Catalina_ProtocolHandler_serverRemoveAppProvidedValues{port="8080",} 0
Catalina_ProtocolHandler_sessionCacheSize{port="8080",} -1
Catalina_ProtocolHandler_sessionTimeout{port="8080",} 86400
Catalina_ProtocolHandler_sniParseLimit{port="8080",} 65536
Catalina_ProtocolHandler_tcpNoDelay{port="8080",} 1
Catalina_ProtocolHandler_threadPriority{port="8080",} 5
Catalina_ProtocolHandler_trustMaxCertLength{port="8080",} 10
Catalina_ProtocolHandler_useKeepAliveResponseHeader{port="8080",} 1
Catalina_ProtocolHandler_useSendfile{port="8080",} 1
Catalina_ProtocolHandler_useServerCipherSuitesOrder{port="8080",} 0
Catalina_Realm_cacheRemovalWarningTime{realmPath="/realm0",} 3600
Catalina_Realm_cacheSize{realmPath="/realm0",} 1000
Catalina_Realm_failureCount{realmPath="/realm0",} 5
Catalina_Realm_lockOutTime{realmPath="/realm0",} 300
Catalina_Realm_validate{realmPath="/realm0",} 1
Catalina_Realm_validate{realmPath="/realm0/realm0",} 1
Catalina_RequestProcessor_bytesReceived{worker="http-nio-8080",name="HttpRequest1",} 0
Catalina_RequestProcessor_bytesSent{worker="http-nio-8080",name="HttpRequest1",} 1364
Catalina_RequestProcessor_contentLength{worker="http-nio-8080",name="HttpRequest1",} -1
Catalina_RequestProcessor_errorCount{worker="http-nio-8080",name="HttpRequest1",} 2
Catalina_RequestProcessor_lastRequestProcessingTime{worker="http-nio-8080",name="HttpRequest1",} 1
Catalina_RequestProcessor_maxTime{worker="http-nio-8080",name="HttpRequest1",} 18
Catalina_RequestProcessor_processingTime{worker="http-nio-8080",name="HttpRequest1",} 19
Catalina_RequestProcessor_requestBytesReceived{worker="http-nio-8080",name="HttpRequest1",} 0
Catalina_RequestProcessor_requestBytesSent{worker="http-nio-8080",name="HttpRequest1",} 0
Catalina_RequestProcessor_requestCount{worker="http-nio-8080",name="HttpRequest1",} 2
Catalina_RequestProcessor_requestProcessingTime{worker="http-nio-8080",name="HttpRequest1",} 0
Catalina_RequestProcessor_serverPort{worker="http-nio-8080",name="HttpRequest1",} -1
Catalina_RequestProcessor_stage{worker="http-nio-8080",name="HttpRequest1",} 7
Catalina_SSLHostConfig_certificateVerificationDepth{ThreadPool="http-nio-8080",name="_default_",} 10
Catalina_SSLHostConfig_certificateVerificationDepthConfigured{ThreadPool="http-nio-8080",name="_default_",} 0
Catalina_SSLHostConfig_disableCompression{ThreadPool="http-nio-8080",name="_default_",} 1
Catalina_SSLHostConfig_disableSessionTickets{ThreadPool="http-nio-8080",name="_default_",} 0
Catalina_SSLHostConfig_honorCipherOrder{ThreadPool="http-nio-8080",name="_default_",} 0
Catalina_SSLHostConfig_insecureRenegotiation{ThreadPool="http-nio-8080",name="_default_",} 0
Catalina_SSLHostConfig_openSslConfContext{ThreadPool="http-nio-8080",name="_default_",} 0
Catalina_SSLHostConfig_openSslContext{ThreadPool="http-nio-8080",name="_default_",} 0
Catalina_SSLHostConfig_revocationEnabled{ThreadPool="http-nio-8080",name="_default_",} 0
Catalina_SSLHostConfig_sessionCacheSize{ThreadPool="http-nio-8080",name="_default_",} -1
Catalina_SSLHostConfig_sessionTimeout{ThreadPool="http-nio-8080",name="_default_",} 86400
Catalina_Server_port 8005
Catalina_Server_portOffset 0
Catalina_Server_portWithOffset 8005
Catalina_SocketProperties_appReadBufSize{name="http-nio-8080",} 8192
Catalina_SocketProperties_appWriteBufSize{name="http-nio-8080",} 8192
Catalina_SocketProperties_bufferPool{name="http-nio-8080",} 500
Catalina_SocketProperties_bufferPoolSize{name="http-nio-8080",} 104857600
Catalina_SocketProperties_directBuffer{name="http-nio-8080",} 0
Catalina_SocketProperties_directBufferPool{name="http-nio-8080",} 500
Catalina_SocketProperties_directSslBuffer{name="http-nio-8080",} 0
Catalina_SocketProperties_eventCache{name="http-nio-8080",} 500
Catalina_SocketProperties_processorCache{name="http-nio-8080",} 500
Catalina_SocketProperties_soLingerOn{name="http-nio-8080",} 0
Catalina_SocketProperties_soLingerTime{name="http-nio-8080",} -1
Catalina_SocketProperties_soTimeout{name="http-nio-8080",} 20000
Catalina_SocketProperties_tcpNoDelay{name="http-nio-8080",} 1
Catalina_SocketProperties_timeoutInterval{name="http-nio-8080",} 1000
Catalina_SocketProperties_unlockTimeout{name="http-nio-8080",} 250
Catalina_StringCache_accessCount 0
Catalina_StringCache_byteEnabled 1
Catalina_StringCache_cacheSize 200
Catalina_StringCache_charEnabled 0
Catalina_StringCache_hitCount 0
Catalina_StringCache_trainThreshold 20000
Catalina_ThreadPool_acceptCount{name="http-nio-8080",} 100
Catalina_ThreadPool_acceptorThreadCount{name="http-nio-8080",} 1
Catalina_ThreadPool_acceptorThreadPriority{name="http-nio-8080",} 5
Catalina_ThreadPool_alpnSupported{name="http-nio-8080",} 0
Catalina_ThreadPool_bindOnInit{name="http-nio-8080",} 1
Catalina_ThreadPool_connectionCount{name="http-nio-8080",} 1
Catalina_ThreadPool_connectionLinger{name="http-nio-8080",} -1
Catalina_ThreadPool_connectionTimeout{name="http-nio-8080",} 20000
Catalina_ThreadPool_currentThreadCount{name="http-nio-8080",} 10
Catalina_ThreadPool_currentThreadsBusy{name="http-nio-8080",} 0
Catalina_ThreadPool_daemon{name="http-nio-8080",} 1
Catalina_ThreadPool_deferAccept{name="http-nio-8080",} 0
Catalina_ThreadPool_executorTerminationTimeoutMillis{name="http-nio-8080",} 5000
Catalina_ThreadPool_keepAliveCount{name="http-nio-8080",} 0
Catalina_ThreadPool_keepAliveTimeout{name="http-nio-8080",} 20000
Catalina_ThreadPool_localPort{name="http-nio-8080",} 8080
Catalina_ThreadPool_maxConnections{name="http-nio-8080",} 8192
Catalina_ThreadPool_maxKeepAliveRequests{name="http-nio-8080",} 100
Catalina_ThreadPool_maxThreads{name="http-nio-8080",} 200
Catalina_ThreadPool_minSpareThreads{name="http-nio-8080",} 10
Catalina_ThreadPool_paused{name="http-nio-8080",} 0
Catalina_ThreadPool_pollerThreadCount{name="http-nio-8080",} 1
Catalina_ThreadPool_pollerThreadPriority{name="http-nio-8080",} 5
Catalina_ThreadPool_port{name="http-nio-8080",} 8080
Catalina_ThreadPool_portOffset{name="http-nio-8080",} 0
Catalina_ThreadPool_portWithOffset{name="http-nio-8080",} 8080
Catalina_ThreadPool_running{name="http-nio-8080",} 1
Catalina_ThreadPool_sSLEnabled{name="http-nio-8080",} 0
Catalina_ThreadPool_selectorTimeout{name="http-nio-8080",} 1000
Catalina_ThreadPool_sniParseLimit{name="http-nio-8080",} 65536
Catalina_ThreadPool_tcpNoDelay{name="http-nio-8080",} 1
Catalina_ThreadPool_threadPriority{name="http-nio-8080",} 5
Catalina_ThreadPool_useInheritedChannel{name="http-nio-8080",} 0
Catalina_ThreadPool_useSendfile{name="http-nio-8080",} 1
Catalina_UtilityExecutor_activeCount 0
Catalina_UtilityExecutor_completedTaskCount 197
Catalina_UtilityExecutor_continueExistingPeriodicTasksAfterShutdownPolicy 0
Catalina_UtilityExecutor_corePoolSize 2
Catalina_UtilityExecutor_executeExistingDelayedTasksAfterShutdownPolicy 0
Catalina_UtilityExecutor_largestPoolSize 2
Catalina_UtilityExecutor_maximumPoolSize 2147483647
Catalina_UtilityExecutor_poolSize 2
Catalina_UtilityExecutor_removeOnCancelPolicy 1
Catalina_UtilityExecutor_shutdown 0
Catalina_UtilityExecutor_taskCount 203
Catalina_UtilityExecutor_terminated 0
Catalina_UtilityExecutor_terminating 0
Catalina_Valve_asyncSupported{host="localhost",name="ErrorReportValve",} 1
Catalina_Valve_asyncSupported{name="StandardEngineValve",} 1
Catalina_Valve_asyncSupported{host="localhost",name="StandardHostValve",} 1
Catalina_Valve_asyncSupported{host="localhost",name="AccessLogValve",} 1
Catalina_Valve_buffered{host="localhost",name="AccessLogValve",} 1
Catalina_Valve_checkExists{host="localhost",name="AccessLogValve",} 0
Catalina_Valve_enabled{host="localhost",name="AccessLogValve",} 1
Catalina_Valve_renameOnRotate{host="localhost",name="AccessLogValve",} 0
Catalina_Valve_rotatable{host="localhost",name="AccessLogValve",} 1
Catalina_Valve_showReport{host="localhost",name="ErrorReportValve",} 1
Catalina_Valve_showServerInfo{host="localhost",name="ErrorReportValve",} 1
Users_UserDatabase_readonly{database="UserDatabase",} 1
Users_UserDatabase_writeable{database="UserDatabase",} 1
```
